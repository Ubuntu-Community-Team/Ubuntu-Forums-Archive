---
title: "Few terminal command related questions. Users, servers, and files."
date: 2009-10-26
forum: New to Ubuntu
---

### Post by RCantw3ll on 2009-10-26
Hell all,

I am in need of some help that I feel most could answer with relative ease. Here are my questions: (Note that I am in ubuntu 8.10)

How to enable a newly created user to use the sudo command through the terminal.

What command to run in terminal to find out what servers are running on my local system?

and what command will list all of the open files on my system? (some sort of specific -ls command maybe?)

I normally am able to find answers to my questions with a quick google search or with playing with the system, but that just has not been the case today. Thanks to everyone in advance.

Best,

RCantw3ll

---

### Post by oldos2er on 2009-10-26
man lsof typed into a terminal will give you a handle on open files.      Adding a user to the admin group will give them sudo privileges. System, Administration, Users & Groups.     You can use a program like sysv-rc-conf to show you services and daemons.

---

### Post by RCantw3ll on 2009-10-26
Thanks for the help man, got what I was lookin for.

Best,

RCantw3ll

---

