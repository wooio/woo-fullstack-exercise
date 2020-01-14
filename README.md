## General:
Sections marked as nice to have (NTH), are not expected in this scope, and can be omitted or replaced with stubs.

## Tech notes:
* Create a responsive single page application using AngularJS.
* Preferably use TypeScript over JavaScript.
* Use Java 8 (or higher) for your Backend.
* Use Spring IoC container and beans
* Use Hibernate as your persistence layer and ORM.
* Use mySQL as you database.

## Spec:

### Data Model
Candidate has a name  
Candidate has multiple tech skills *(from technologies list - can be currently a limited hardcoded list of strings)*  
Candidate has multiple expectations:  
* Tech stack *(from technologies list)*
* Salary *(minimum required)*
* **NTH** - Location - *(from a cities list - can be currently a limited hardcoded list of strings)*
* More in the future...

Employer has a name  
Employer has multiple Positions  
Position has a title and:  
* Tech stack - Serves both as required skills and as tech stack to fulfill candidate expectation.
* Salary *(maximum possible)*
* **NTH** - Location (from cities list)

Process is between a Candidate and Position  
Process has the following available statuses:
* New
* Accepted 
* Rejected

### User Interface (See screenshots in the repository):
* Candidate can choose to view a list of all his Processes.
* **NTH** - Candidate can choose to view only the “New” Processes.
* Candidate can accept or reject a new Process.

For each process the following details will be shown:
* Position title
* Employer name
* Process status
* Position tech stack
* Candidate expectations marked as either fulfilled or unfulfilled
* For new processes Accept/Reject button
* **NTH** - Time when process started

**NOTE:** Exact font, color or spacing is not critical. But layout, positioning and alignment is.

### Matching:
* **A candidate should only have x (currently 1) processes in status “New” at any given moment.**
* A scheduled task running once an hour will search for matches and create new processes accordingly.
* In addition, when a candidate accepts a “New” process, the system should search for a new match to create.

Match Score - A Candidate and position with a score higher than 75 is considered a match.
* Skills score - percentage of the position tech stack a candidate possesses as skills * 25 *(max 25 pts)*
* Tech stack score - percentage of fulfilled tech stack expectations * 25 *(max 25 pts)*
* **NTH** - Salary score -  *((Position salary / Candidate expected salary) * 25)  (max 25 pts)*
* **NTH** - Location score - same city = 25 pts. same country = 10 pts.  *(max = 25 pts)*

Expectation fulfillment *(when is an expectation considered fulfilled)*
* Technologies - More than half of required technologies exist in the position.
* **NTH** - Salary - Position salary >= Candidate expected salary
* **NTH** - Location - same city.

### Bonus:
Add examples for tests (server and client side).
