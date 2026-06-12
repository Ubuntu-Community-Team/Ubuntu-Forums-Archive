---
title: "Open Office problem?"
date: 2010-03-18
forum: New to Ubuntu
---

### Post by nene7 on 2010-03-18
hi, 
 I am triyng to install open office 3.2 in a mini 10v that have ubuntu 8.04. I remove openoffice 2.4 with command:
> sudo apt-get remove openoffice*.* and the i tried to install download the ooo file from official page in the desktop and then 
> 

sudo dpkg -i ~/Desktop/OOO320_m12_native_packed-1_en-US.9483/DEBS/*.deb

then 
> 

sudo dpkg -i ~/Desktop/OOO320_m12_native_packed-1_en-US.9483/DEBS/desktop-integration/openoffice.org3.2-debian-menus_3.2-9472_all.deb

and it suppost to be installed. what am i doin wrong?

---

### Post by linuxman94 on 2010-03-18
Have a look at this thread.

[http://ubuntuforums.org/showthread.php?t=1428441&highlight=open+office]("http://ubuntuforums.org/showthread.php?t=1428441&highlight=open+office")

---

### Post by nene7 on 2010-03-18
ok, i need to reinstall ooo 2.4 because it appear that ooo 3.2 dont install in ubuntu.  thanks i stay with the illution to install ooo 3.2 in my machine.

---

### Post by mechro on 2010-03-18
The command for debian installation quoted here...

[http://wiki.services.openoffice.org/w/images/7/7e/Installation_Guide_OOo3.pdf](http://wiki.services.openoffice.org/w/images/7/7e/Installation_Guide_OOo3.pdf)

is...

```
dpkg -i --force-overwrite openoffice.org*.deb \
 desktop-integration/openoffice.org-debian-menus*.deb
```

---

### Post by Hagar Delest on 2010-03-20
> **nene7 said:**
> it suppost to be installed. what am i doin wrong?
You don't tell us what's wrong! Have you seen the installation taking places in the terminal? Do you get the entries in the menus? Can you launch OOo?

Basically, I would say that your commands are correct (no need to use any additional parameter to the command line BTW). Check that one perhaps: [[Ubuntu] Installing OOo on Debian and Co.](http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=68)

---

