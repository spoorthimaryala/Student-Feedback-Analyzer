Student Feedback Analyzer

A command-line Python application that lets students submit anonymous ratings and comments for their faculty, and lets faculty view their own feedback with an average rating and charts.

Developed as a Course End Project for A9513 – Python Programming Laboratory, Department of Computer Science and Engineering, Vardhaman College of Engineering, Hyderabad (Academic Year 2026-27).

Table of Contents
Features
Tech Stack
How It Works
Project Structure
Getting Started
Usage
Default Credentials
Data Files
Sample Output
Limitations and Security Notes
Future Enhancements
Authors
Acknowledgements
Features
Separate logins for students and faculty
Auto-generated data on first run: 600 student accounts and 72 faculty accounts
Section-wise feedback: each student rates every faculty member assigned to their department and section
Input validation: ratings must be between 1 and 5, and comments cannot be empty
Anonymous feedback: student IDs are never stored with feedback records
Faculty dashboard: view all comments, total responses, and average rating
Visualization: Matplotlib bar charts for rating distribution and average rating
No database needed: all data is stored in plain CSV files
Tech Stack
Component	Technology
Language	Python 3.x
Data storage	CSV files (csv module)
Visualization	Matplotlib
Interface	Command line (terminal)

Python concepts used: lists, dictionaries, loops, conditionals, functions, file handling, exception handling.

How It Works
On startup, the program creates students.csv, teachers.csv and feedback.csv if they do not already exist.
A student logs in, and the app looks up the faculty for that student's department and section. The student gives a rating (1-5) and a comment for each faculty member.
Each response is appended to feedback.csv with the department, section, faculty name, rating, comment and timestamp.
A faculty member logs in and sees only the feedback recorded against their own name, along with the average rating and charts.
Structure of the Data
Departments: CSE, CSM, ECE
Sections: A, B, C, D (per department)
Students: 200 per department, 50 per section (600 total)
Faculty: 6 per section (72 total)
Project Structure
student-feedback-analyzer/
├── main.py             # Application source code
├── students.csv        # Auto-generated on first run
├── teachers.csv        # Auto-generated on first run
├── feedback.csv        # Auto-generated on first run
├── requirements.txt    # Python dependencies
└── README.md

Rename the uploaded pythontemp script to main.py (or any .py name) before committing it.

Getting Started
Prerequisites
Python 3.8 or higher
pip
Installation
bash
# 1. Clone the repository
git clone https://github.com/<your-username>/student-feedback-analyzer.git
cd student-feedback-analyzer

# 2. (Optional) create a virtual environment
python -m venv venv
source venv/bin/activate        # On Windows: venv\Scripts\activate

# 3. Install dependencies
pip install -r requirements.txt

requirements.txt only needs one line:

matplotlib
Run
bash
python main.py
Usage
================================
   STUDENT FEEDBACK SYSTEM
================================
1. Student Login
2. Teacher Login
3. Exit

As a student

Choose 1. Student Login and enter your ID and password.
Choose 1. Submit Feedback.
For each faculty member, enter a rating from 1 to 5 and a short comment.

As a faculty member

Choose 2. Teacher Login and enter your ID and password.
Choose 1. View My Feedback.
Read the comments and see the average rating. Two charts open in separate windows (close the first to see the second).
Default Credentials

Accounts are generated automatically using a fixed pattern.

Role	ID format	Password format	Example
Student	<DEPT><1001-1200>	<ID>@123	CSE1001 / CSE1001@123
Faculty	<dept><section><01-06> lowercase	<ID>@123	csea01 / csea01@123

Student sections are assigned by number: 1-50 → A, 51-100 → B, 101-150 → C, 151-200 → D.

Data Files

feedback.csv

Column	Description
Department	Student's department
Section	Student's section
Faculty	Faculty member being rated
Rating	Integer from 1 to 5
Comment	Free-text feedback
Date	Timestamp (YYYY-MM-DD HH:MM)
Sample Output
Feedback for Dr. Kumar
Department: CSE
Section: A
----------------------------------------
Rating: 5 /5
Comment: Explains concepts very clearly.
Date: 2026-10-09 10:30
----------------------------------------
Total feedback: 1
Average rating: 5.0 /5

(You can add screenshots of the menus and charts here, for example in a screenshots/ folder.)

Limitations and Security Notes

This is an academic prototype, so please keep these points in mind before using it for anything real:

Passwords are stored in plain text in the CSV files. A real system should store salted hashes (for example with bcrypt).
Default passwords are predictable and follow a public pattern.
Students can submit multiple times. There is no check to stop a student from rating the same faculty again.
Faculty and student data are hard-coded in the script and not editable from the app.
Comments are not analyzed automatically. Sentiment classification is not implemented yet.
CSV files do not handle many users writing at the same time.
Future Enhancements
Hashed passwords and a one-submission-per-student rule
Graphical user interface (Tkinter or a web front end)
Database storage (SQLite / MySQL)
Automatic sentiment analysis of comments (positive / neutral / negative)
Admin panel to manage students, faculty and sections
Exporting reports as PDF or Excel
Online feedback collection
Authors
K. Revanth
M. Spoorthi

Course Facilitator: Ms. P.S. Madhavi, Assistant Professor, Department of Computer Science and Engineering

Vardhaman College of Engineering, Hyderabad

Acknowledgements
Python Documentation
Matplotlib
Allen B. Downey, Think Python: How to Think Like a Computer Scientist, O'Reilly Media
UNESCO, Education 2030: Sustainable Development Goal 4 – Quality Education
