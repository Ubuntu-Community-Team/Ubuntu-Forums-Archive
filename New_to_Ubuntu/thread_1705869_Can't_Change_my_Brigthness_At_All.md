---
title: "Can't Change my Brigthness At All"
date: 2011-03-12
forum: New to Ubuntu
---

### Post by juancee on 2011-03-12
I kinda have to post this quick, due to the problem. Please tell me if I'm missing some vital information.

Ever since I installed Ubuntu a few days ago, I have not been able to turn down the brightness. I use the Fn + Brightness down key (on a laptop), and I'm notified that the brightness does go down, but it physically does not. I hold the buttons to make sure that they do something, but Ubuntu says it's completely down even though it's not.

I've searched the forum a while and tried the xbacklight and xgamma thing in the Terminal, but xgamma just changes the colors to darker versions of themselves and xbacklight makes no changes. I really would like this changed, because the battery dies down quickly and it hurts me eyes.

Also, this only happens on Ubuntu. On W7 (I have a dual-boot going on here), I can change it fine.

Here's some info, if it's needed. Like I said, my battery power is dying and it might not be relevant:
What I get in Terminal when I do lspci: [http://pastebin.com/M4RFt9CK](http://pastebin.com/M4RFt9CK)

Gateway NV55C
Intel Pentium Processor PC6100

Again, please tell me if I'm missing something. Thanks.

---

### Post by fabricator4 on 2011-03-13
> **juancee said:**
> I kinda have to post this quick, due to the problem. Please tell me if I'm missing some vital information.

Ever since I installed Ubuntu a few days ago, I have not been able to turn down the brightness. I use the Fn + Brightness down key (on a laptop), and I'm notified that the brightness does go down, but it physically does not. I hold the buttons to make sure that they do something, but Ubuntu says it's completely down even though it's not.


Edit /etc/default/grub and make sure that you have:

```

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash osi_acpi=Linux backlight=vendor"

```

Then make sure you've got any third part drivers loaded.  First check that you've got proprietory drivers enabled in software sources:

```

->System
   ->Administration
       ->Software Sources

```

Then

```

->System
   ->Administration
       ->Hardware Drivers

```


Chris

---

### Post by juancee on 2011-03-13
How do I edit /etc/default/grub? Sorry, I'm a total newb. >.<

And I don't have Software Sources under Administration. The closest thing is Additional Drivers, and I get "No proprietary drivers are in use on the this system." with a blank box.

---

### Post by fabricator4 on 2011-03-13
> **juancee said:**
> How do I edit /etc/default/grub? Sorry, I'm a total newb. >.<

And I don't have Software Sources under Administration. The closest thing is Additional Drivers, and I get "No proprietary drivers are in use on the this system." with a blank box.

try:

```

sudo nano /etc/default/grub

```

Chris

---

### Post by juancee on 2011-03-13
I did that, and then the file opens in Terminal. I change it, but I don't know how to save it. So I copied the file to the desktop from the location I found in the folder and changed the one on the desktop. I tried replacing it, but can't because I don't have the permission to do so. :\

---

### Post by fabricator4 on 2011-03-13
> **juancee said:**
> I did that, and then the file opens in Terminal. I change it, but I don't know how to save it. So I copied the file to the desktop from the location I found in the folder and changed the one on the desktop. I tried replacing it, but can't because I don't have the permission to do so. :\

<ctrl>O should have let you write the file out, and <ctrl>X to exit.

Meanwhile if you have the file on your desktop, just use sudo in front of your cp command to copy the file with assumed root user privileges.  sudo = SUperuser DO.

Chris

---

### Post by juancee on 2011-03-14
Thank you again.

So I changed the grub file to match your input, rebooted, but still cannot change the backlight. Also, when you mentioned the drivers earlier in the posts, I took this: [http://i51.tinypic.com/5x53fa.png](http://i51.tinypic.com/5x53fa.png)
Is this normal?

---

### Post by fabricator4 on 2011-03-14
> **juancee said:**
> ]
Is this normal?

Yes, that's fine, it just means that the system already all the drivers it needs in the Kernel (but not for the backlight, obviously.)

It really should be working.  Is this with 10.04 LTS release, or have you installed 10.10?

Chris

---

### Post by juancee on 2011-03-14
```

Distributor ID:    Ubuntu
Description:    Ubuntu 10.10
Release:    10.10
Codename:    maverick

```

I've tried searching Google & the Forums various times and tried some things but they haven't done any good.

---

### Post by Quadunit404 on 2011-03-14
Judging by the Ambiance window controls, I'd say Maverick.

---

### Post by fabricator4 on 2011-03-14
> **juancee said:**
> ```

Distributor ID:    Ubuntu
Description:    Ubuntu 10.10
Release:    10.10
Codename:    maverick

```

I've tried searching Google & the Forums various times and tried some things but they haven't done any good.

Would it be possible to try the 10.04 LTS release?  10.10 does seem to be having more than the odd problem here and there.  LTS stands for Long Term Support, it gets updates and support for three years from release.

Chris

---

### Post by juancee on 2011-03-15
I'd prefer not to, since I don't have something to backup my files with right now. Also, if 10.4LTS has the same problem, then I might not benefit much from it. :\

---

