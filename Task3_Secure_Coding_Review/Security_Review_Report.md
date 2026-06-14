# Security Review Report

## Project Information

**Project Name:** Python Login System

**Programming Language:** Python

**Objective:** Review the source code, identify security vulnerabilities, assess risks, and recommend security improvements.

---

## Vulnerability Findings

### 1. Hardcoded Credentials

The username and password are directly stored in the source code.

**Example:**

```python
if username == "admin" and password == "admin123":
```

**Risk Level:** High

**Impact:**
Anyone with access to the source code can view the credentials and gain unauthorized access.

**Recommendation:**
Store credentials securely in a database and use password hashing instead of hardcoding them in the application.

### 2. Weak Password

The application uses a weak and easily guessable password.

**Example:**

```python
password == "admin123"
```
**Risk Level:** Medium

**Impact:**
Attackers can guess common passwords using dictionary attacks or brute-force attacks.

**Recommendation:**
Use strong passwords that contain uppercase letters, lowercase letters, numbers, and special characters. Passwords should be at least 8–12 characters long.
### 3. No Login Attempt Limit

The application allows unlimited login attempts without any restriction.

**Risk Level:** Medium

**Impact:**
Attackers can repeatedly try different passwords until they find the correct one, leading to brute-force attacks.

**Recommendation:**
Implement a login attempt limit (e.g., maximum 3 attempts) and temporarily lock the account after repeated failures.


### 4. Plain Text Password Handling

The password is stored and compared in plain text instead of using secure hashing techniques.

**Example:**

```python
password = input("Enter Password: ")

if username == "admin" and password == "admin123":
```

**Risk Level:** High

**Impact:**
If the source code or storage system is compromised, attackers can directly view and steal user passwords.

**Recommendation:**
Use password hashing algorithms such as bcrypt or SHA-256 and never store passwords in plain text.
---
## Recommendations

1. Remove hardcoded usernames and passwords from the source code.

2. Store passwords securely using hashing algorithms such as bcrypt.

3. Enforce strong password policies requiring:

   * Uppercase letters
   * Lowercase letters
   * Numbers
   * Special characters

4. Implement a login attempt limit to prevent brute-force attacks.

5. Store credentials securely in a database instead of directly in the application code.

6. Conduct regular security reviews and code audits.


---

## Conclusion

The security review identified several vulnerabilities in the Python Login System, including hardcoded credentials, weak password usage, lack of login attempt restrictions, and plain text password handling.

These vulnerabilities could allow attackers to gain unauthorized access through password guessing, brute-force attacks, or source code exposure.

By implementing secure coding practices such as password hashing, strong password policies, login attempt limits, and secure credential storage, the overall security of the application can be significantly improved.

