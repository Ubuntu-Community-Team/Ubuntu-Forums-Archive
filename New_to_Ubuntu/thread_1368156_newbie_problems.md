---
title: "newbie problems"
date: 2009-12-30
forum: New to Ubuntu
---

### Post by bobmccleskey on 2009-12-30
I have recently installed Ubuntu 9.10 as a stand alone OS on an HP a6528p (which is a 2.20 Ghz dual processor with 3.0 gb or RAM).  When trying to start from the hard drive I am getting error messages as follows:

Mount of filesystem failed
a maintenance shell will now be started
Control-D will terminate the shell and retry
Root@bosb-desktop: ~#     [ok]

and the system hangs up.  Sometimes I get *starting init crypto disks... after the root@bosb-desktop: ~# line

However, I am able to start the system by booting from the CD.

Any suggestions for solving the problem?

---

### Post by Merk42 on 2009-12-30
Maybe a corrupted install?
Did you chose the option "Check Disk for Errors" before you installed?

---

### Post by arubislander on 2009-12-30
Hi.. 

> **Merk42 said:**
> Maybe a corrupted install?
Did you chose the option "Check Disk for Errors" before you installed?
+1

And after doing that and the Disk has no errors, have you tried installing again? I've had this in the past... Maybe try selecting different settings this time around. For instance if you selected the option to encrypt your home directory, or to add an encrypted directory to your home directory, omit doing so this time around. I've never gotten this option to work.

---

### Post by bobmccleskey on 2009-12-30
> **arubislander said:**
> Hi.. 


+1

And after doing that and the Disk has no errors, have you tried installing again? I've had this in the past... Maybe try selecting different settings this time around. For instance if you selected the option to encrypt your home directory, or to add an encrypted directory to your home directory, omit doing so this time around. I've never gotten this option to work.

I vaguely recall doing a check disk during the install.  Did not encrypt anything.  

This is the first time I have attemped to install a Linux based OS.  The computer came with Windows Vista which I attempted to replace with XP Pro, unsuccessfully, I will add.  Thought I would give Ubuntu a try.  I downloaded both the 32 and 64 bit versions but only installed the 32 bit.  How would I determine which Intel processor I have (32 ot 64 bit) using Ubuntu?

I will try re-installing.

---

### Post by thatguruguy on 2009-12-30
You CAN run the 64-bit version with your setup.  The fact that the upgrade to Win XP Pro suggests you *may* have a disk issue. Good luck.

---

### Post by Merk42 on 2009-12-30
> **bobmccleskey said:**
> I vaguely recall doing a check disk during the install.  Did not encrypt anything.  

This is the first time I have attemped to install a Linux based OS.  The computer came with Windows Vista which I attempted to replace with XP Pro, unsuccessfully, I will add.  Thought I would give Ubuntu a try.  I downloaded both the 32 and 64 bit versions but only installed the 32 bit.  How would I determine which Intel processor I have (32 ot 64 bit) using Ubuntu?

I will try re-installing.

Well  you say you have an an [HP a6528p](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01474421&tmp_track_link=ot_faqs/top_issues/en_us/c01474421/loc:3&lc=en&dlc=en&cc=us&product=3751188&lang=en) that has a [Intel® Pentium® Processor E2200](http://ark.intel.com/Product.aspx?id=33925) which says it's 64bit.

As far as checking the disc for errors the installation was checking your disks (hard drive) not the CD.  So I would recommend doing that.  It's one of the options when you first boot, when you have the option of installing or trying.

---

### Post by danastasio on 2009-12-30
to check which architecture you are currently running, run 
```
uname -a
```

I'm going with everyone else and saying that it is a corrupted install.

But at the system maintenence shell, you can try running
```
fsck
```

and seeing what that gets you.

---

