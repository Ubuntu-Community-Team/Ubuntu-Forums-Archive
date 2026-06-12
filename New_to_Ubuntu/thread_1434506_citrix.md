---
title: "citrix"
date: 2010-03-20
forum: New to Ubuntu
---

### Post by Trandre on 2010-03-20
Ihave earlier tried to use  citrix in Ubuntu without any luck, but now I found this post, so I give it a new try.

Wich one of these clients shall I download?

Trandre

```
Message Center
	
There are no existing applications available for reconnection.
	
If you wish to use the latest Citrix Presentation Server Client, you can install it. After installation, you must restart your browser.
Download the Citrix Presentation Server Client for Linux x86

Download the Citrix Presentation Server Client for Linux ARM

Other clients are available from the Citrix client download site


```

---

### Post by Trandre on 2010-03-20
ok, I think Arm is not an option due to,the glued in text.

but do I have an x86?

Trandre

```
ARM
ARM is a processor architecture used in a variety of applications, such as:

Handheld Computers (Nokia n9xx/n8xx/n7xx, Sharp Zaurus, etc.)
Network Devices (Thecus N series, Linksys NSLU2, etc.)
Project development boards (Gumstix, Beagleboard, etc.)
Subnotebooks (press releases indicate these will exist)
Ubuntu jaunty targets the ARM EABI, with an expectation of minimum compliance with the ARMv5t instruction set. Optimised libraries for ARMv6 and ARMv7 are expected to be available where there is significant performance gain.

Ubuntu karmic targets armv6.

Ubuntu lucid targets armv7 and higher only, See https://wiki.ubuntu.com/ARM/Thumb2.
```

---

### Post by patchwork on 2010-03-20
x86 is the standard 32 bit architecture (i.e. Penitum, Athlon XP, Celeron, Duron, etc.)

If you type in the terminal
```
uname -a
```
the last portion will tell you whether you are using 32 bit (x86 arch) or 64 bit (x86_64 arch) Ubuntu.

---

### Post by Trandre on 2010-03-20
Thank  you, patchwork


Trandre:p

---

### Post by Trandre on 2010-03-20
Hmmm I think I have an x86 and a 32bit. Can somebody tell me how I can read that from this?


Trandre

```
famfem@famfem-desktop:~$ uname -a
Linux famfem-desktop 2.6.31-20-generic #58-Ubuntu SMP Fri Mar 12 05:23:09 UTC 2010 i686 GNU/Linux

```

---

### Post by patchwork on 2010-03-20
You are correct, you are using 32 bit Ubuntu

> i686 

686 is a subset of x86.

If you were using 64 bit, it would read as i686_64 or similar

---

### Post by Trandre on 2010-03-20
Aha, Thanks. I am new to Ubuntu and apreciate your help. 

Trandre

---

