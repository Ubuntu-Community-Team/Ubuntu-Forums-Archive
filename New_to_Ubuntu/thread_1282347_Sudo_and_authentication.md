---
title: "Sudo and authentication"
date: 2009-10-04
forum: New to Ubuntu
---

### Post by donescamillo on 2009-10-04
This is a silly question for someone with my experience with Ubuntu (2 weeks), but here it goes:
I installed Ubuntu creating one user in the process. Now I log as this user. If I want to do something important I write sudo ...
The system asks me for a password and I enter the same password with which I logged in. Why is it asking me for a password, doesnt it know who is currently logged in? Or it asks just the same? Not that it is a bad thing...

regards,
donescamillo

---

### Post by jrothwell97 on 2009-10-04
> **donescamillo said:**
> This is a silly question for someone with my experience with Ubuntu (2 weeks), but here it goes:
I installed Ubuntu creating one user in the process. Now I log as this user. If I want to do something important I write sudo ...
The system asks me for a password and I enter the same password with which I logged in. Why is it asking me for a password, doesnt it know who is currently logged in? Or it asks just the same? Not that it is a bad thing...

regards,
donescamillo

Sudo is there to make sure you don't damage your system - or, more importantly, that any nasty software can't damage the system.

Linux (and all other UNIX-like OSes) use certain accounts for "normal" users, and one other account, usually called "root", as the system administrator. As the system sees it, root is god and that is final.

This is why only root can make major changes to the system. The sudo command allows you to "become" root for a short period of time, but *only* to run that command. The root account itself is locked on Ubuntu, because logging in as root (especially in a graphical environment) is *incredibly* dangerous.

In short, it's to provide another level of protection to help ensure that you and only you can run administrative commands on the system.

---

### Post by dumblebee100 on 2009-10-04
> **donescamillo said:**
> This is a silly question for someone with my experience with Ubuntu (2 weeks), but here it goes:
I installed Ubuntu creating one user in the process. Now I log as this user. If I want to do something important I write sudo ...
The system asks me for a password and I enter the same password with which I logged in. Why is it asking me for a password, doesnt it know who is currently logged in? Or it asks just the same? Not that it is a bad thing...

regards,
donescamillo

security buddy

one is not encouraged to use root account the whole time ..because if anything bad you do then it damages ur full ubuntu ..

and comming to entering ur password 

ubuntu asks your password in order to give u a temporary access to root but for that it needs to know that the user is legitimate ones so it asks for ur password ..and It expires in about 10-15 mins I think so

---

