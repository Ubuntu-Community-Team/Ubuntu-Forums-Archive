---
title: "software update issues"
date: 2009-01-23
forum: New to Ubuntu
---

### Post by rovering on 2009-01-23
Hi, new to Ubuntu.
Trying to install what is now 58 updates.
I keep getting an error message which says I need to manually run 'dpkg--configure-a'in a terminal window. 
I located the terminal window. Applications-Accessories- Terminal. I entered the command but it comes back with bad command. 
Help please! I dont know what to do to fix this issue so I can install updates.

---

### Post by hyper_ch on 2009-01-23
what is the exacte error message you get when you run this command that it tells you?

---

### Post by rovering on 2009-01-23
exact error message is as follows:
E:dkpg was interrupted. You must manually run pkg--configure-a' to correct the problem. E:_cache->open()failed. Please report.

---

### Post by rovering on 2009-01-23
error message from terminal window says: bash:dpkg--configure-a: command not found

---

### Post by sahabcse on 2009-01-23
hi

dpkg-reconfigure command available in ubuntu it is used to 
dpkg-reconfigure - reconfigure an already installed package

For package upgrade and update. 

Run #sudo apt-get upgrade
    #sudo apt-get update

For more info [http://sahabm.blogspot.com/2009/01/package-management-debian-and-ubuntu.html](http://sahabm.blogspot.com/2009/01/package-management-debian-and-ubuntu.html)

---

### Post by Paqman on 2009-01-23
The correct command is:
```
sudo dpkg --configure -a
```

Copy and paste that into the terminal to avoid syntax errors.

---

