---
title: "UMASK doubt??"
date: 2009-11-05
forum: New to Ubuntu
---

### Post by abhiram7 on 2009-11-05
hello ppl

while trying out a simple program that uses umask function, i set the umask value to 0 (umask(0)) and create a file foo which only read write permissions for user,other and group, on executing the program and ls -l foo i find even the execute permission is also enabled for everyone (User, group, others). though the file is created only with read and write permission.
I dont understand the reason behind it.
can somebody explain it.

thanks

---

### Post by ajgreeny on 2009-11-05
I think files are either executable or not-executable, but I don't think you can make tham executable only by some users.  The only way to allow for that, I think, is if the execution action requires root privileges, when only those in the admin group will be able to run it with password.

I coild be wrong, of course, so wait for others to answer as well.

---

