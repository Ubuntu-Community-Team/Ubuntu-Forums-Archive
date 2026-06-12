---
title: "cant log in cos keyboard and mose stop working"
date: 2009-06-16
forum: New to Ubuntu
---

### Post by aiden707 on 2009-06-16
just installed  ubuntu on a acer aspire 5310 laptop installed on seperate partion and have vista on other partion. after grub loader when on ubuntu side keyboard and mouse wont work so i cant log in!. If i chose recovery mode keyboard works  ( not if try normal boot , at login same problem) in shell keyboard works only i dont know command to start login and the desktop.
any help welcome
thanks
aiden

---

### Post by brewbie on 2009-06-16
not super awesome at this stuff yet, but try 

Sudo /etc/init.d/gdm Stop
Sudo /etc/init.d/gmd Start

See if that helps out at all.

If not have you tried a different mouse and keyboard?
:confused:

---

### Post by aiden707 on 2009-06-16
tried those comands but no luck, still cant log in or move mouse at login , but can use key board in recovery mode. have tried diffferent keyboard but same problem
any other ideas?

---

### Post by aiden707 on 2009-06-18
just reinstalled ubuntu using different copy of ubuntu now works fine

---

### Post by vaikz on 2009-06-18
Will you please state what version of ubuntu you installed?

---

