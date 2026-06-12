---
title: "ENABLE SMP in 8.10!"
date: 2008-12-07
forum: New to Ubuntu
---

### Post by mr_rg on 2008-12-07
Many computers today have more than one core. If ubuntu want to stay on top of things SMP need to be a part of the kernel. What the heck were they thinking ??? Completely mind boggling.

---

### Post by 67GTA on 2008-12-07
It should support SMP. Post the output of ```
cat /proc/cpuinfo
``` from a terminal.

---

### Post by iponeverything on 2008-12-07
root@mac-laptop:~# cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=8.10
DISTRIB_CODENAME=intrepid
DISTRIB_DESCRIPTION="Ubuntu 8.10"

root@mac-laptop:~# uname -a
Linux mac-laptop 2.6.27-9-generic #1 [COLOR="Red"]SMP[/COLOR] Thu Nov 20 21:57:00 UTC 2008 i686 GNU/Linux

---

### Post by kerry_s on 2008-12-07
> **mr_rg said:**
> Many computers today have more than one core. If ubuntu want to stay on top of things SMP need to be a part of the kernel. What the heck were they thinking ??? Completely mind boggling.

almost every linux distro uses a smp kernel.

i use debian lenny:
uname -a:
Linux Vaio 2.6.26-1-686 #1 **SMP** Wed Nov 26 19:14:11 UTC 2008 i686 GNU/Linux

---

### Post by katon on 2008-12-27
i have quad core intel proc, and it seems sometimes uses only one of them....i can see it in process manager.
i use ubuntu 8.10   
do i need to compile software i use to run under quad core multithread ? or is it automatic?

---

### Post by 3rdalbum on 2008-12-27
> **katon said:**
> i have quad core intel proc, and it seems sometimes uses only one of them....i can see it in process manager.
i use ubuntu 8.10   
do i need to compile software i use to run under quad core multithread ? or is it automatic?

Any software that can use multiple threads will use multiple threads. Multi-threaded programming is more difficult than you think. Some tasks cannot be separated into multiple threads, or doing this would not give a speed benefit.

It's like hiring four trucks to carry a fridge to your house. You can't split a fridge up into four parts, and if you did, it wouldn't get to your house quicker. However, if you need to carry 20 fridges, you can load them onto four trucks and deliver 20 fridges in the same time that it would take one truck to deliver 5 fridges.

This is why Intel's new Core i7 processors have "turbo mode" - if you are running a single-threaded program, it slows down the less-occupied cores and uses the power saving to run the fully-loaded core faster.

However: You do get a slight speed improvement on your quad-core even if a process is only using one thread. All the other services on Linux will occupy your other three cores and allow the intensive thread to monopolize the first core. As the first core doesn't have to worry about running your printing system, displaying your desktop and decoding Youtube videos, your intensive task will run faster than on a single-core processor.

---

### Post by katon on 2008-12-27
thank you, just i have been noticed that opening some web pages with FLASH it uses a lot of one core.
Also using Mplayer opening HD movies...
but it could be about my 9600gt nvidia ...maybe not the newest driver..

---

### Post by sdennie on 2008-12-27
Ubuntu kernels have support for up to 8 cores/threads.  I think 3rdalbum has probably described the situation you are seeing.

Edit: Actually, it appears that for Intrepid, the core/thread limit has been changed 64.

---

### Post by mr_rg on 2008-12-31
Hi

I was confused by this in the 8.10 release notes:

UbuntuStudio real-time kernel support
The real-time kernel variant included in Ubuntu 8.10 does not include SMP support. Users of UbuntuStudio 8.04 who need real-time kernel support for dual-core, dual-processor, or more complex SMP configurations are advised not to upgrade to UbuntuStudio 8.10 at this time. 

But now I realised the realtime kernel is not the ordinary kernel.

---

