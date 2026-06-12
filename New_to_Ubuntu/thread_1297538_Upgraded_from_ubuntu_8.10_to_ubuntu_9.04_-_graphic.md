---
title: "Upgraded from ubuntu 8.10 to ubuntu 9.04 - graphic problems"
date: 2009-10-21
forum: New to Ubuntu
---

### Post by Bigbob22 on 2009-10-21
I have an ATI mobility radeon x1400 graphics card in my inspiron e1505. Today I upgraded from 8.10 to 9.04 and encountered serious graphical problems. I was able to get it to where a black screen shows after the boot. If i then click ctrl alt f1 to get to the console it says xserver failed to start. How do I fix this problem? Please help, I have been trying to fix this constantly for the past 3 hours.

---

### Post by Mark Phelps on 2009-10-21
Did you have ATI restricted drivers installed in 8.10?

If so, you should have removed them BEFORE the upgrade to 9.04 as your card is no longer supported for ATI drivers with 9.04 and newer.

Read the link below about removing proprietary drivers and installing the open source drivers:

[https://help.ubuntu.com/community/RadeonDriver]("https://help.ubuntu.com/community/RadeonDriver")

---

### Post by Bigbob22 on 2009-10-21
I tried to remove xorg-driver-fglrx but this comes up 
```
dpkg: parse error, in file '/var/lib/dpkg/available' near line 8642 package 'libgnutls26':
value for 'status' field not allowed in this context
E: Sub-process /user/bin/dpkg returned an error code (2)
```

---

### Post by Bigbob22 on 2009-10-22
please help

---

### Post by Bigbob22 on 2009-10-22
I fixed the parse error and I am going to try to do what the link said to do.

---

### Post by Bigbob22 on 2009-10-22
Now this is showing up when i try to reinstall libgl1-mesa-glx
```
dpkg: unrecoverable fatal error, aborting:
too-long line or missing newline in '/var/lib/dpkg/diversions'
E: Sub-process /usr/bin/dpkg returned an error code (2)

```

---

