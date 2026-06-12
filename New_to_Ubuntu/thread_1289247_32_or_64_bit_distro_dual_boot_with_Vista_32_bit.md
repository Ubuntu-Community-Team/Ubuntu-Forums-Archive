---
title: "32 or 64 bit distro dual boot with Vista 32 bit"
date: 2009-10-12
forum: New to Ubuntu
---

### Post by Antiopa on 2009-10-12
Hello everyone,
 
I am trying to choose the Ubuntu distro and version to install as a dual boot with Vista 32 bit. Right now I have a disc for 32 bit 8.10 but I have been considering making a copy of 64 bit 9.04 and using it instead.  I have checked and my system is 64 bit capable.
 
My main question is this: can I install a 64 bit distro when the other part of the dual boot (Vista) is only 32 bit. Will this damage my hardware or create any problems?
 
Secondary question: are there any major advantages of using 8.10 instead of going to 9.04?
 
Thank you!

---

### Post by MelDJ on 2009-10-12
for 1st question: i dont think so. because the two OSes aren't influenced by each other. if your computer uses a 64-bit processor, use the 64-bit ubuntu.
2. 9.04 is more up to date than 8.10. latest features are in it etc. or just wait another 17 days for karmic :)

---

### Post by bwallum on 2009-10-12
I have just configured a machine running 32 bit XP and 64bit Ubuntu karmic on an AMD 64bit platform. All runs well. I used seperate hard drives for each os largely because I always expect trouble from M$, vista in particular, and so have Ubuntu on a drive with its own master boot record (grub). That way, when antivirus software tries to lock/screws the mbr and vista goes belly up, I can repair the system by booting up on the Ubuntu drive by changing booting priority in the cmos.

Karmic is running particularly fast so I would opt for Ubuntu 9.10 when it comes out on the 29th of this month.

---

### Post by Antiopa on 2009-10-12
Thanks!  :)

I ended up sticking with an install of 8.10 32 bit for now (which is working quite well so far) and I plan to change over once Karmic is out of beta.

---

