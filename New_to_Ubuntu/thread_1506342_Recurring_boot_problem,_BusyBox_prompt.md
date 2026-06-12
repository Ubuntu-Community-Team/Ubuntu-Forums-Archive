---
title: "Recurring boot problem, BusyBox prompt"
date: 2010-06-10
forum: New to Ubuntu
---

### Post by zlapidus on 2010-06-10
Dear Ubuntu Community,

Thanks for taking the time to read this message. I've had this same issue happen several times with my wubi install, and I'm trying to figure out why this occurs. Every time I've deleted and reinstalled, but this happens after about 4 or 5 boots into ubuntu, so something must be wrong. I just downloaded it, so it's using the latest, 64-bit version of ubuntu.

When selecting Ubuntu, Linux 2.6.32-21-generic, the cursor blinks for about 15-20 seconds, and then gives me the message:

Gave up waiting for root device. Common problems:
- Boot args (cat /proc/cmdline)
    - Check rootdelay= (did the system wait long enough?)
    - Check root= (did the system wait for the right device?)
 - Missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/sdb1 does not exist. Dropping to a shell!

and then I have the BusyBox shell, with the (initramfs) prompt. Waiting for a few minutes and typing exit does nothing.

The strangest thing to me is that prior to this, every time I'd been able to boot and login to ubuntu about 4 or 5 times. Here's where it gets really weird:

If i boot into Ubuntu, Linux 2.6.32-21-generic recovery mode, and select "Resume normal boot" from the recovery menu, I can login to Ubuntu with my username and type "startx," and I can get into ubuntu's graphical environment.

According to grub, I can't see a difference between the startup commands for either option, so I'm not sure why this is happening. The three times this happened before, it directly followed installing system updates that popped up. This most recent time, I decided to not install the system updates to avoid the problem, but instead installed some software (gftp, some editors, etc) and the problem happened again. I'm not saying that these problems necessarily correlate, but it seems like something's being changed.

I'm enjoying my experience with ubuntu, despite this headache, and understand it's probably due to the fact that i'm using wubi. Hopefully somebody can help shed some light on this situation? Thanks in advance.

---

### Post by kevin.bogle on 2010-06-10
> **zlapidus said:**
> Dear Ubuntu Community,

Thanks for taking the time to read this message. I've had this same issue happen several times with my wubi install, and I'm trying to figure out why this occurs. Every time I've deleted and reinstalled, but this happens after about 4 or 5 boots into ubuntu, so something must be wrong. I just downloaded it, so it's using the latest, 64-bit version of ubuntu.

When selecting Ubuntu, Linux 2.6.32-21-generic, the cursor blinks for about 15-20 seconds, and then gives me the message:

Gave up waiting for root device. Common problems:
- Boot args (cat /proc/cmdline)
    - Check rootdelay= (did the system wait long enough?)
    - Check root= (did the system wait for the right device?)
 - Missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/sdb1 does not exist. Dropping to a shell!

and then I have the BusyBox shell, with the (initramfs) prompt. Waiting for a few minutes and typing exit does nothing.

The strangest thing to me is that prior to this, every time I'd been able to boot and login to ubuntu about 4 or 5 times. Here's where it gets really weird:

If i boot into Ubuntu, Linux 2.6.32-21-generic recovery mode, and select "Resume normal boot" from the recovery menu, I can login to Ubuntu with my username and type "startx," and I can get into ubuntu's graphical environment.

According to grub, I can't see a difference between the startup commands for either option, so I'm not sure why this is happening. The three times this happened before, it directly followed installing system updates that popped up. This most recent time, I decided to not install the system updates to avoid the problem, but instead installed some software (gftp, some editors, etc) and the problem happened again. I'm not saying that these problems necessarily correlate, but it seems like something's being changed.

I'm enjoying my experience with ubuntu, despite this headache, and understand it's probably due to the fact that i'm using wubi. Hopefully somebody can help shed some light on this situation? Thanks in advance.
Having the same problem, running 32 instead of 64.  Please advise.

---

### Post by vivek_yadav on 2010-12-13
having the same problem running 64

---

