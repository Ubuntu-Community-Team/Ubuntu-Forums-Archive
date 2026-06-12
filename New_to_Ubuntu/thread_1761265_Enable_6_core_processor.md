---
title: "Enable 6 core processor"
date: 2011-05-17
forum: New to Ubuntu
---

### Post by steigerjb on 2011-05-17
Is there anything I need to do to enable all 6 cores of my hexacore processor?

I hear for multicore booting I need to do the following:

```
sudo gedit /etc/init.d/rv
```

Change 

> CONCURRENCY=none

 to 

> CONCURRENCY=shell

Is that all?

---

### Post by jtarin on 2011-05-17
[Found this.]("http://computingtech.blogspot.com/2008/08/enabling-multiple-cpus-smp-in-ubuntu.html").....forgot about the SMP kernel.

[In addition someone else's experience.]("http://ubuntuforums.org/showthread.php?t=1706348")

From a Bulletin Board:```
> Does anyone know if a /proc or /sys tweak can be used to enable/disable
> a CPU or CPU core in a running Linux system?

echo 0 >> /sys/devices/system/cpu/cpu1/online

I didn't know that until I just Googled for it. It's a nice trick :)
```

---

### Post by steigerjb on 2011-05-18
> **jtarin said:**
> [Found this.]("http://computingtech.blogspot.com/2008/08/enabling-multiple-cpus-smp-in-ubuntu.html").....forgot about the SMP kernel.

[In addition someone else's experience.]("http://ubuntuforums.org/showthread.php?t=1706348")

From a Bulletin Board:```
> Does anyone know if a /proc or /sys tweak can be used to enable/disable
> a CPU or CPU core in a running Linux system?

echo 0 >> /sys/devices/system/cpu/cpu1/online

I didn't know that until I just Googled for it. It's a nice trick :)
```

I have the BURG boot loader with Natty Narwhal.

---

### Post by jtarin on 2011-05-18
It's only a front for Grub2.....google Ubuntu docs on editing.

And I have the EasyBCD Boot loader with Windows 7 and chainloading Ubuntu Maverick Meerkat......so....NYAH!!

---

### Post by steigerjb on 2011-05-18
> **jtarin said:**
> It's only a front for Grub2.....google Ubuntu docs on editing.

And I have the EasyBCD Boot loader with Windows 7 and chainloading Ubuntu Maverick Meerkat......so....NYAH!!

Its a what?

---

### Post by bwang on 2011-05-18
AFAIK Ubuntu will work happily with 6 cores out of the box; I have it running on my quad-core fine, and I've had Debian on a 10-CPU machine with no problems.

---

### Post by steigerjb on 2011-05-18
> **bwang said:**
> AFAIK Ubuntu will work happily with 6 cores out of the box; I have it running on my quad-core fine, and I've Debian on a 10-CPU machine with no problems.

Thanks

---

### Post by steigerjb on 2011-05-18
Do you guys know a way to get KDEnlive to take advantage of the 6 cores?

---

