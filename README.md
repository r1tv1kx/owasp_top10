# OWASP Top 10 Vulnerabilities

The OWASP Top 10 is a list of the most dangerous security problems in web applications. This guide explains these risks in simple terms and how to prevent them.

---

## 1. Broken Access Control
**What is it?**
Users get access to things they shouldn’t, like admin panels or other people's data.

**Example Attack:**
A normal user types:
```plaintext
https://example.com/admin
```
and gets admin access because the system doesn’t check their permissions.

**How to Fix It:**
- Set proper user roles and permissions.
- Always check permissions before giving access.
- Follow the rule of least privilege—users should only see what they need.

---

## 2. Cryptographic Failures
**What is it?**
Sensitive data (passwords, credit card details) isn’t protected properly, making it easy to steal.

**Example Attack:**
A hacker finds that passwords are stored as plain text and logs in as any user.

**How to Fix It:**
- Encrypt important data using strong encryption methods (AES-256, TLS 1.3).
- Hash passwords with bcrypt, Argon2, or PBKDF2.
- Avoid weak encryption like MD5 and SHA-1.

---

## 3. Injection (SQLi, XSS, etc.)
**What is it?**
Hackers insert harmful code into an application through input fields.

**Example Attack (SQL Injection):**
A hacker enters:
```sql
' OR 1=1 --
```
This tricks the system into always allowing access.

Another SQL Injection example:
```sql
SELECT * FROM users WHERE username = 'admin' AND password = '' OR '1'='1';
```
This lets an attacker log in without a real password.

**How to Fix It:**
- Use prepared statements in database queries.
- Always validate and clean user input.
- Use security tools like Web Application Firewalls (WAFs).

---

## 4. Insecure Design
**What is it?**
Security isn’t considered when designing the application.

**Example Attack:**
A banking app allows password resets without verifying user identity.

**How to Fix It:**
- Plan security from the start of development.
- Identify risks early using threat modeling.
- Test for security flaws regularly.

---

## 5. Security Misconfiguration
**What is it?**
Using weak settings, exposing important data, or leaving default configurations.

**Example Attack:**
- A site still uses default login details (`admin/admin`).
- Error messages reveal sensitive system info.

**How to Fix It:**
- Change default credentials immediately.
- Hide error messages from users.
- Regularly check and update security settings.

---

## 6. Vulnerable & Outdated Components
**What is it?**
Using old, unsafe software or libraries.

**Example Attack:**
A hacker exploits a bug in an old version of Apache Struts to take control of a server.

**How to Fix It:**
- Always update software and dependencies.
- Use security tools like OWASP Dependency-Check.
- Monitor known vulnerabilities in your tech stack.

---

## 7. Identification & Authentication Failures
**What is it?**
Weak login systems make it easy for hackers to break in.

**Example Attack:**
A hacker tries common passwords (`123456`, `password1`) and gets in.

**How to Fix It:**
- Require strong passwords (at least 12 characters, mix of letters, numbers, symbols).
- Enable Multi-Factor Authentication (MFA).
- Block repeated login attempts.

---

## 8. Software & Data Integrity Failures
**What is it?**
Using untrusted software updates or insecure delivery methods.

**Example Attack:**
A hacker modifies a software update, spreading malware to all users.

**How to Fix It:**
- Use code signing to check if updates are legit.
- Secure your software development pipeline.
- Verify the integrity of all downloaded files.

---

## 9. Security Logging & Monitoring Failures
**What is it?**
Without proper logging and alerts, attacks go unnoticed.

**Example Attack:**
Hackers try thousands of passwords, but no one notices because failed logins aren’t recorded.

**How to Fix It:**
- Log important security events like failed logins.
- Use monitoring tools (SIEM) to detect attacks.
- Set up real-time alerts for suspicious activity.

---

## 10. Server-Side Request Forgery (SSRF)
**What is it?**
Hackers trick a server into making unauthorized requests.

**Example Attack:**
A hacker enters:
```plaintext
http://localhost:8080/admin
```
If the server processes the request, private data can be exposed.

**How to Fix It:**
- Block requests to internal IPs (like `127.0.0.1`).
- Allow requests only to trusted websites.
- Always check and sanitize user input.

---
