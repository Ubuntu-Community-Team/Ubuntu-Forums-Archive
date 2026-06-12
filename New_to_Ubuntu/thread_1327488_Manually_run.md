---
title: "Manually run?"
date: 2009-11-15
forum: New to Ubuntu
---

### Post by mary.ydm on 2009-11-15
I am trying to update my software using update manager however I get the message:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.


When I try to run dpkg --configure -a in terminal I get the following message dpkg: requested operation requires superuser privilege

I have no idea what this means as I am the only registered user on this computer - Help???

---

### Post by howefield on 2009-11-15
> **mary.ydm said:**
> When I try to run dpkg --configure -a in terminal I get the following message dpkg: requested operation requires superuser privilege

Precede the command with sudo.

Then type your password when prompted and press enter.

---

### Post by sisco311 on 2009-11-15
Open a terminal 
(Applications -> Accessories -> Terminal)

copy and paste this command in the terminal window:
```
sudo dpkg --configure -a
```
press Enter, type your password and press enter again.

NOTE: There is no visual feedback when you enter your password.

---

### Post by ectomorph on 2009-11-15
A good little article on sudo..

[http://aplawrence.com/Basics/sudo.html]("http://aplawrence.com/Basics/sudo.html")

:D

---

