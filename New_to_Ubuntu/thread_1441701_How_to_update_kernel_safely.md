---
title: "How to update kernel safely?"
date: 2010-03-29
forum: New to Ubuntu
---

### Post by karthick87 on 2010-03-29
This is my kernel version,i would like to update my kernel..How to update it safely..?

```
karthick@Learners-desktop:~$ uname -a
Linux Learners-desktop **2.6.28-11-generic** #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009 i686 GNU/Linux
```

---

### Post by KIAaze on 2010-03-29
From source or from the repositories?
The latest version in the repositories seems to be 2.6.31-20-generic.

Normally, Ubuntu should offer it to you as an upgrade.
If not simply open Synaptic, refresh the package list and install "linux-image".

Or more quickly:
```

sudo apt-get update
sudo apt-get install linux-image

```

This will not remove any older kernels. It will just upgrade to the latest generic Linux kernel image.

If you have problems with the new kernel, you can still boot into older kernels through the grub menu.

---

### Post by watgate on 2010-03-29
Just use the update manager!:KS

---

### Post by bkratz on 2010-03-29
> **getyourkarthick said:**
> This is my kernel version,i would like to update my kernel..How to update it safely..?

```
karthick@Learners-desktop:~$ uname -a
Linux Learners-desktop **2.6.28-11-generic** #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009 i686 GNU/Linux
```



Well I did it this way

[http://unixmen.com/linux-tutorials/780-upgrade-your-kernel-the-safe-way-in-ubuntu-linuxmint](http://unixmen.com/linux-tutorials/780-upgrade-your-kernel-the-safe-way-in-ubuntu-linuxmint)

there are warnings given, but it worked for me, upgrading to one of the 10.04 kernels, due to wireless issues.

---

### Post by karthick87 on 2010-04-01
Which version of kernel is safe?

---

### Post by NightwishFan on 2010-04-01
If you are using a supported version of Ubuntu (8.04, then 9.04 and up) then any of them are safe and supported. Run the update manager (system -> administration -> update manager) and you will have the latest security and bug fix updates. It will also let you upgrade to a new version of Ubuntu if you want.

Using a up to the minute kernel (2.6.33 or 2.6.34rc I believe) is not really needed unless you know you need something fresh in the newer kernel. Ubuntu will incorporate the newest kernel every 6 month cycle. So in 10.04 we have the 2.6.32 kernel. I am willing to bet 10.10 will be using 2.6.34. Just keep the one you have

---

