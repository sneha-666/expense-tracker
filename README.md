# expense-tracker
Here is a simple implementation of the Expense Tracker project in Python:


Expense Tracker

class ExpenseTracker:
    def __init__(self):
        self.expenses = {}

    def add_expense(self, category, amount, description):
        if category not in self.expenses:
            self.expenses[category] = []
        self.expenses[category].append({"amount": amount, "description": description})

    def view_expenses(self, category=None):
        if category:
            if category in self.expenses:
                print(f"Expenses for {category}:")
                for expense in self.expenses[category]:
                    print(f"Amount: {expense['amount']}, Description: {expense['description']}")
            else:
                print("Category not found.")
        else:
            print("All Expenses:")
            for category, expenses in self.expenses.items():
                print(f"{category}:")
                for expense in expenses:
                    print(f"Amount: {expense['amount']}, Description: {expense['description']}")

    def monthly_summary(self):
        total_expenses = 0
        for category, expenses in self.expenses.items():
            category_total = sum(expense["amount"] for expense in expenses)
            total_expenses += category_total
            print(f"{category}: ${category_total:.2f}")
        print(f"Total Expenses: ${total_expenses:.2f}")

    def category_wise_expenditure(self):
        for category, expenses in self.expenses.items():
            category_total = sum(expense["amount"] for expense in expenses)
            print(f"{category}: ${category_total:.2f}")

def main():
    tracker = ExpenseTracker()

    while True:
        print("1. Add Expense")
        print("2. View Expenses")
        print("3. Monthly Summary")
        print("4. Category-wise Expenditure")
        print("5. Quit")

        choice = input("Enter your choice: ")

        if choice == "1":
            category = input("Enter category: ")
            amount = float(input("Enter amount: "))
            description = input("Enter description: ")
            tracker.add_expense(category, amount, description)
        elif choice == "2":
            category = input("Enter category (or leave blank for all): ")
            if category:
                tracker.view_expenses(category)
            else:
                tracker.view_expenses()
        elif choice == "3":
            tracker.monthly_summary()
        elif choice == "4":
            tracker.category_wise_expenditure()
        elif choice == "5":
            break
        else:
            print("Invalid choice. Please try again.")

if __name__ == "__main__":
    main()
