---
title: "How can I make my user act as a root"
date: 2008-12-22
forum: New to Ubuntu
---

### Post by my_everything78 on 2008-12-22
Hello everyone 
in Ubuntu my user  is sizar , the problem is when im in sizar user it always ask me for permission when im trying to do something , so I log as root to continue my task .
The question how can I make my user act as a root ?

Thank you

---

### Post by SlidingHorn on 2008-12-22
use "sudo" in front of a command to use root priviledges

[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---

### Post by igknighted on 2008-12-22
You shouldn't run as a user with root privileges, as it is a security risk.  Your user is configured to be able to temporarily assume admin rights with sudo.  This is completely fundamental to why linux is more secure than windows, and as far as I know it is a violation of forum policy to discuss how to do it on these boards.

***NOTE: THE FOLLOWING IS NOT A GOOD SECURITY PRACTICE.  I RECOMMEND THAT YOU DO NOT DO THIS!

If you don't want to enter your password a lot, you can bypass the password requirement.  Run the command "sudo visudo", then change the last line to "%admin ALL=NOPASSWD: ALL".  You would still need to type sudo to use admin commands, but it wont ask for your password.

---

### Post by my_everything78 on 2008-12-22
thank you slidinghorn for your help .
I understand now why i cant login as root.
:)

---

### Post by my_everything78 on 2008-12-22
thank you sir .
I do understand now , and i think it is better to have password everytime you want to run sudo , it is more secure .

Thank you alot for your help

---

