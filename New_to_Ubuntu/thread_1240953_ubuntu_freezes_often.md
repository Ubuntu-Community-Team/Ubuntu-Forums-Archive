---
title: "ubuntu freezes often"
date: 2009-08-15
forum: New to Ubuntu
---

### Post by gkraju on 2009-08-15
hi i am having ubuntu 9.04 (GNOME)
ubuntu freezes often in my system it freezes mostly when i am using opera or firefox
i had to restart since everything hangs
what should i do?


System configuration
1 GB Ram
Intel core 2 Duo 1.8Ghz

---

### Post by gkraju on 2009-08-15
> **gkraju said:**
> hi i am having ubuntu 9.04 (GNOME)
ubuntu freezes often in my system it freezes mostly when i am using opera or firefox
i had to restart since everything hangs
what should i do?


System configuration
1 GB Ram
Intel core 2 Duo 1.8Ghz

i checked the swap space using top 
it shows swap 0k total 0k
is that a problem?

---

### Post by enli on 2009-08-15
What is your other hardware?

There is a issue with Intel drivers causing random system freezes. It might be the root of the problem with your case.

---

### Post by dlmarti on 2009-08-15
Both Opera and Firefox use alot of ram, this could be a ram issue.

Please run the memtest program on the install disk, or at least install memtest86 (and run it) on your system.

memtest86 is run from the grub menu if you install it.

---

### Post by gkraju on 2009-08-15
> **enli said:**
> What is your other hardware?

There is a issue with Intel drivers causing random system freezes. It might be the root of the problem with your case.

Mother Board:Intel D946GZ
Processor: Intel Core 2 Duo 1.8 GHZ

---

### Post by roger_1960 on 2009-08-15
Hi

Suggest you back up everything externally if you have not already. 

 I had very similar problems - random "lock ups", needing a hard reset, for about a week, especially when using memory intensive programs......and then the hard drive finally failed completely!  I thought it was a ram problem before the disk failed, but turned out to be locking up when trying to read from a hard drive that wouldn't play.

Try running a live disk in ram only and if this is OK (ie no locking up) it may well be a hard drive issue.

---

### Post by colau on 2009-08-15
> **gkraju said:**
> hi i am having ubuntu 9.04 (GNOME)
ubuntu freezes often in my system it freezes mostly when i am using opera or firefox
i had to restart since everything hangs
what should i do?


System configuration
1 GB Ram
Intel core 2 Duo 1.8Ghz
Run firefox, and run top command.
See the %CPU usage by firefox and report.

---

### Post by colau on 2009-08-15
> **gkraju said:**
> hi i am having ubuntu 9.04 (GNOME)
ubuntu freezes often in my system it freezes mostly when i am using opera or firefox
i had to restart since everything hangs
what should i do?


System configuration
1 GB Ram
Intel core 2 Duo 1.8Ghz
Can you post:
```

dpkg -l | grep mozilla-plugin-gnash
dpkg -l | grep swfdec-mozilla 

```

---

### Post by enli on 2009-08-15
I had similar problem on Ubuntu 9.04. System would hang randomly when Firefox is run and less frequently when it is not.

This problem was related to Intel video driver and not the firefox. I don't know current status of Intel video driver but mine issue was solved by reverting back to 2.4 driver as guided at [https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4](https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4)

If you don't play any high graphics 3D games then this is the easiest fix, if our problems are the same.

---

