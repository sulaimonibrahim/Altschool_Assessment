"""Representing an individual financial expense"""
```
import uuid
from datetime import datetime, timezone

class Expense:
    def __init__(self, title, amount):
        self.id = str(uuid.uuid4())
        self.title = title
        self.amount = amount
        self.created_at = datetime.now(timezone.utc)
        self.updated_at = self.created_at

    def update(self, title=None, amount=None):
        if title is not None:
            self.title = title
        if amount is not None:
            self.amount = amount
        self.updated_at = datetime.now(timezone.utc)

    def to_dict(self):
        return {
            'id': self.id,
            'title': self.title,
            'amount': self.amount,
            'created_at': self.created_at.isoformat(),
            'updated_at': self.updated_at.isoformat()
        }
```
"""This Represents a collection of financial expense"""
```
class ExpenseDatabase:
    def __init__(self):
        self.expenses = []

    def add_expense(self, expense):
        self.expenses.append(expense)

    def remove_expense(self, expense_id):
        self.expenses = [e for e in self.expenses if e.id != expense_id]

    def get_expense_by_id(self, expense_id):
        for expense in self.expenses:
            if expense.id == expense_id:
                return expense
        return None

    def get_expenses_by_title(self, title):
        return [expense for expense in self.expenses if expense.title == title]

    def to_dict(self):
        return [expense.to_dict() for expense in self.expenses]

# Example usage:
expense_db = ExpenseDatabase()

expense1 = Expense(title="Groceries", amount=70.0)
expense2 = Expense(title="Utilities", amount=210.0)

expense_db.add_expense(expense1)
expense_db.add_expense(expense2)

print("Initial Expenses:")
print(expense_db.to_dict())

# Update an expense
expense_db.get_expense_by_id(expense1.id).update(title="New Groceries", amount=80.0)

print("\nExpenses after update:")
print(expense_db.to_dict())

# Remove an expense
expense_db.remove_expense(expense2.id)

print("\nExpenses after removal:")
print(expense_db.to_dict())
```

# Expense Tracker

This project implements two classes in Python, Expense and ExpenseDatabase, to model and manage financial expenses. The Expense class represents individual expenses, while the ExpenseDatabase class manages a collection of Expense objects.

## Expense Class

### Attributes:

1. 'id': A unique identifier generated as a UUID string.
2. 'title': A string representing the title of the expense.
3. 'amount': A float representing the amount of the expense.
4. 'created_at': A timestamp indicating when the expense was created (UTC).
5. 'updated_at': A timestamp indicating the last time the expense was updated (UTC).

### Methods:

1. '__init__': Initializes the attributes.
2. 'update': Allows updating the title and/or amount, updating the updated_at timestamp.
3. 'to_dict': Returns a dictionary representation of the expense.

## Expense Database Class

### Attributes:

1. 'expenses': A list storing Expense instances.

### Methods:

1. '__init__': Initializes the list.
2. 'add_expense': Adds an expense.
3. 'remove_expense': Removes an expense.
4. 'get_expense_by_id': Retrieves an expense by ID.
5. 'get_expenses_by_title': Retrieves expenses by title (returning a list).
6. 'to_dict': Returns a list of dictionaries representing expenses.

## GitHub Repository

[Expense Tracker](https://github.com/sulaimonibrahim/Altschool_Assessment)

## How to Clone
To clone the repopsitory use the link below:

git clone https://github.com/sulaimonibrahim/Altschool_Assessment.git
cd Altschool_Assessment

## How to run my code
I wrote this code on vscode. So here is how i run it:

'python3 Altschool_Assessment'
