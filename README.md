# student-result-management-system
A Python-based Student Result Management System to calculate marks, percentage, grades, and display student results.
print("=" * 40)
print("      WELCOME TO STUDENT CALCULATOR")
print("=" * 40)

name = ""
roll_number = 0
marks = []
percentage = 0

while True:

    print("\n----------- MENU -----------")
    print("1. Personal Details")
    print("2. Enter Marks")
    print("3. Calculate Percentage")
    print("4. Check Grade")
    print("5. Check Pass/Fail")
    print("6. Exit")
    print("----------------------------")

    try:
        choice = int(input("Enter your choice: "))

        # Personal Details
        if choice == 1:

            name = input("Enter Student Name: ")
            roll_number = int(input("Enter Roll Number: "))

            print("\n--- Student Details ---")
            print("Student Name :", name)
            print("Roll Number  :", roll_number)

        # Marks
        elif choice == 2:

            print("\nEnter marks out of 100:")

            subjects = ["English", "Hindi", "Chemistry", "Physics", "Maths"]
            marks = []

            for subject in subjects:
                mark = int(input(f"Enter {subject} Marks: "))

                if 0 <= mark <= 100:
                    marks.append(mark)
                else:
                    print("Marks must be between 0 and 100.")
                    marks = []
                    break

            if marks:
                print("\nMarks:", marks)
                print("Total Marks:", sum(marks), "/ 500")

        # Percentage
        elif choice == 3:

            if len(marks) == 5:
                total = sum(marks)
                percentage = total / 5

                print(f"\nStudent Percentage: {percentage:.2f}%")
            else:
                print("Please enter marks first!")

        # Grade
        elif choice == 4:

            if len(marks) == 5:
                percentage = sum(marks) / 5

                if percentage >= 80:
                    grade = "A"
                elif percentage >= 60:
                    grade = "B"
                elif percentage >= 40:
                    grade = "C"
                else:
                    grade = "F"

                print("Student Grade:", grade)

            else:
                print("Please enter marks first!")

        # Pass / Fail
        elif choice == 5:

            if len(marks) == 5:

                if all(mark >= 33 for mark in marks):
                    print("\nResult: PASS")
                    print("Education is the key to success.")

                else:
                    print("\nResult: FAIL")
                    print("A single piece of paper cannot decide your future.")

            else:
                print("Please enter marks first!")

        # Exit
        elif choice == 6:

            print("\nThank you for using Student Calculator!")
            print("Better luck and keep learning. 😊")
            break

        else:
            print("Invalid choice! Please select 1 to 6.")

    except ValueError:
        print("Please enter a valid number.")
