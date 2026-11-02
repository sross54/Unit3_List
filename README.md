"""
==================================================
Unit 3 DISCUSSION: List Operations (Insert, Delete, Search)
==================================================

INSTRUCTIONS:
This assignment focuses on understanding how lists behave when elements
are inserted, removed, and searched. You will analyze how Python lists
shift elements in memory and how different operations impact performance.
"""


def insert_at(lst, index, value):
    """
    TODO (Student):
    Insert a value into the list at the specified index.

    Requirements:
    - Use a list operation to insert the value.
    - Add comments explaining what happens to existing elements
      after an insertion occurs.
    - Use comments to explain how insertion performance may vary depending on
      where the insertion occurs.
    """
    # Insert the value at the specified index.
    # Any existing elements at this position, and after it
    # are shifted one position to the right.
    lst.insert(index, value)

    # Insertion at the beginning or middle typically requires
    # more shifting of elements, making it less efficient than
    # insertion at the end of the list.
    return lst


def delete_at(lst, index):
    """
    TODO (Student):
    Remove and return the value at the specified index.

    Requirements:
    - Validate that the index exists.
    - Return the removed value.
    - Return None if the index is invalid.
    - Add comments explaining why index validation and safe deletion are important.
    """
    # Validate the index before attempting deletion.
    # This prevents IndexError exceptions and allows the
    # program to handle invalid input safely.
    if index < 0 or index >= len(lst):
        return None

    # Remove and return the value at the specified index.
    # Elements after the deleted item shift left to fill the gap.
    return lst.pop(index)


def search_value(lst, value):
    """
    TODO (Student):
    Search for a value within the list.

    Requirements:
    - Return the index if the value is found.
    - Return -1 if the value is not found.
    - Add comments explaining why this is a linear search and why it scans sequentially.
    """
    # This is a linear search because each element is checked
    # one at a time from left to right until the value is found
    # or the end of the list is reached.
    for i in range(len(lst)):
        if lst[i] == value:
            return i

    return -1


def main():
    print("=== UNIT 3: LIST OPERATIONS ===")

    # ===============================
    # TODO (Student): INSERTION TESTS
    # ===============================
    #
    # Requirements:
    # 1. Create a list containing several values.
    # 2. Display the original list.
    # 3. Test insertion at:
    #    - the beginning
    #    - the middle
    #    - the end
    # 4. Display the list after each insertion.
    # 5. Use comments to explain each step in the implementation.

    print("\n=== INSERTION TESTS ===")
    numbers = [10, 20, 30, 40]
    print("Original List:", numbers)

    # Insert at the beginning
    insert_at(numbers, 0, 5)
    print("After inserting 5 at beginning:", numbers)

    # Insert in the middle
    insert_at(numbers, 3, 25)
    print("After inserting 25 in middle:", numbers)

    # Insert at the end
    insert_at(numbers, len(numbers), 50)
    print("After inserting 50 at end:", numbers)

    # ===============================
    # TODO (Student): DELETION TESTS
    # ===============================
    #
    # Requirements:
    # 1. Delete an item from:
    #    - the beginning
    #    - the middle
    #    - the end
    # 2. Display the removed value.
    # 3. Display the updated list after each deletion.
    # 4. Use comments to clearly explain what is happening in the output.

    print("\n=== DELETION TESTS ===")
    removed = delete_at(numbers, 0)
    print("Removed from beginning:", removed)
    print("Updated List:", numbers)

    middle_index = len(numbers) // 2
    removed = delete_at(numbers, middle_index)
    print("Removed from middle:", removed)
    print("Updated List:", numbers)

    removed = delete_at(numbers, len(numbers) - 1)
    print("Removed from end:", removed)
    print("Updated List:", numbers)

    # ===============================
    # TODO (Student): SEARCH TESTS
    # ===============================
    #
    # Requirements:
    # 1. Search for a value that exists.
    # 2. Search for a value that does not exist.
    # 3. Display the search results with clear explanations.
    # 4. Use comments to explain each step.

    print("\n=== SEARCH TESTS ===")
    found_index = search_value(numbers, 20)
    print("Value 20 found at index:", found_index)

    missing_index = search_value(numbers, 999)
    print("Value 999 found at index:", missing_index)

    # ===============================
    # TODO (Student): EDGE CASES
    # ===============================
    #
    # Demonstrate at least two edge cases.
    #
    # Example ideas:
    # - Delete using an invalid index
    # - Search for a missing value
    # - Insert into an empty list
    # - Delete from an empty list
    # - Use comments to explain each edge case.

    print("\n=== EDGE CASES ===")
    # Edge Case 1: Invalid deletion index
    result = delete_at(numbers, 100)
    print("Delete at invalid index:", result)

    # Edge Case 2: Insert into an empty list
    empty_list = []
    insert_at(empty_list, 0, 99)
    print("Insert into empty list:", empty_list)

    # Edge Case 3: Delete from an empty list
    result = delete_at([], 0)
    print("Delete from empty list:", result)

    # Edge Case 4: Search for missing value
    result = search_value(empty_list, 500)
    print("Search for missing value:", result)



if __name__ == "__main__":
    main()
