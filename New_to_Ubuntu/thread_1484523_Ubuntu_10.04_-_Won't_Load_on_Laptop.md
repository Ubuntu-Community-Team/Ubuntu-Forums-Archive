---
title: "Ubuntu 10.04 - Won't Load on Laptop"
date: 2010-05-15
forum: New to Ubuntu
---

### Post by Atavaka on 2010-05-15
Hi. I've used several flavors of Ubuntu in the past but never had the opportunity to make it a primary operating system at home due to using EVDO for my internet. Have gotten around that now and have a laptop I'm wanting to use it on. I downloaded 10.04 32-bit edition and the netbook edition and can't get either of them to load.

The furthest I can get is to the splash screen with the 5 dots blinking, it loads for a bit (can hear the disc spinning up in the drive) and then it kicks to a black screen, the disc stops spinning and it hangs. I've let it sit for an hour and nothing ever happened. Happens on both discs, too. I managed to load and install OpenSuSE just fine but I really prefer Ubuntu to that (have a small harddrive, too, that is sharing space with a Windows partition and SuSE has a pretty big footprint.)

I honestly don't know where to start as far as getting Ubuntu to load. I can provide any information that might be relevant to getting it up and running. It's a Dell Inspiron 710m and I can provide any other specs that may be needed.

Thanks!

---

### Post by readycarpenter on 2010-05-15
ubuntu install disk has heavily compressed files, which makes it easier to get burn errors, it is really important to burn the iso using a very slow burn speed, this could be your problem, but also because of the heavily compressed files, it is a lot of work on your cd/dvd drive, your disk drive could also be failing.

try to re-burn the iso using the slowest speed available, or if your pc has boot from usb option, you can create a boot-able usb ubuntu install

cheers

---

### Post by Atavaka on 2010-05-15
I don't believe the media is an issue here. The drive has seemed to be fine and the disc will load in my desktop just fine. I'll give the USB route a go and see how that works out.

---

### Post by Animal0307 on 2010-05-15
I have a similar problem. I believe mine is being caused by dvd drive itself not being set up right. I created a Usb boot stick with no problems but when I booted from it I had to wait for like 30-45 minutes( far from the 30-45 seconds I was expecting). And I am trying to test a couple of spare drives because I'm not keen on installing a dual boot yet as I am still learning. But the only problem I'm having is its really slow. Could just be my machine. Hope everything works out. Good Luck.

---

### Post by Atavaka on 2010-05-16
Okay, so, I've messed with half a dozen other things and found a way to get 10.04 on my laptop. What I ended up doing is loading 8.04 LTS and network upgrading and got everything fully installed. 

Unfortunately, it still hangs, but I have more information, now.

Near as I can tell, X is where the problem lies. As soon as the x starts it hangs. I tried booting in to the recovery mode and ran X from there and boom- as soon as X starts the system hangs. 

Does anyone have any advice on how I might work around this to get to the GUI? Or is there anything I can do to keep it from hanging? I can supply any information that might be relevant.

---

### Post by lkraemer on 2010-05-16
You could have downloaded and tried the Alternate Install CD.

lk

---

### Post by keepingitcivil on 2010-05-17
I'm getting this same problem on my Dell Latitude D505.  I was able to install ubuntu using the alternate iso, but it did the same thing upon the first load (hung after the progress bar.)

---

### Post by Atavaka on 2010-05-17
I never managed to get it working. Went back to the 9 LTS and it works just fine. I guess I'll just wait until they get the bugs worked out before I give it another shot.

---

### Post by efrens on 2010-06-17
I'm confirming that the same error happens with this Dell Inspiron 710m I have with me. Exactly as described on the first post. But only with Lucid Lynx. Older versions work just fine.

---

### Post by efrens on 2010-06-17
Got the reason why so.
[http://ubuntuforums.org/showthread.php?t=1476730](http://ubuntuforums.org/showthread.php?t=1476730)

This user's fujitsu laptop has the same graphics controller Intel 82852.

---

### Post by ukripper on 2010-06-17
> **Atavaka said:**
> Hi. I've used several flavors of Ubuntu in the past but never had the opportunity to make it a primary operating system at home due to using EVDO for my internet. Have gotten around that now and have a laptop I'm wanting to use it on. I downloaded 10.04 32-bit edition and the netbook edition and can't get either of them to load.

The furthest I can get is to the splash screen with the 5 dots blinking, it loads for a bit (can hear the disc spinning up in the drive) and then it kicks to a black screen, the disc stops spinning and it hangs. I've let it sit for an hour and nothing ever happened. Happens on both discs, too. I managed to load and install OpenSuSE just fine but I really prefer Ubuntu to that (have a small harddrive, too, that is sharing space with a Windows partition and SuSE has a pretty big footprint.)

I honestly don't know where to start as far as getting Ubuntu to load. I can provide any information that might be relevant to getting it up and running. It's a Dell Inspiron 710m and I can provide any other specs that may be needed.

Thanks!

See post #34 on here - [http://www.uluga.ubuntuforums.org/showthread.php?t=1463294&page=4](http://www.uluga.ubuntuforums.org/showthread.php?t=1463294&page=4) your solution is there.

---

### Post by h218design on 2010-06-17
> **Atavaka said:**
> Hi. I've used several flavors of Ubuntu in the past but never had the opportunity to make it a primary operating system at home due to using EVDO for my internet. Have gotten around that now and have a laptop I'm wanting to use it on. I downloaded 10.04 32-bit edition and the netbook edition and can't get either of them to load.

The furthest I can get is to the splash screen with the 5 dots blinking, it loads for a bit (can hear the disc spinning up in the drive) and then it kicks to a black screen, the disc stops spinning and it hangs. I've let it sit for an hour and nothing ever happened. Happens on both discs, too. I managed to load and install OpenSuSE just fine but I really prefer Ubuntu to that (have a small harddrive, too, that is sharing space with a Windows partition and SuSE has a pretty big footprint.)

I honestly don't know where to start as far as getting Ubuntu to load. I can provide any information that might be relevant to getting it up and running. It's a Dell Inspiron 710m and I can provide any other specs that may be needed.

Thanks!

Ok, don't know if this works for all, but if you don't want to tweak, this worked for me.  

Had same problem with my Dell Vostro 1500 (Blank screen). 

What I did: Before booting up the CD, connected an external monitor.  Powered up, and shifted over to the monitor (FN+F8 for me).  I was able to do the entire install with the external monitor, then installed the nvida driver, rebooted and the laptop screen worked fine.

Hope it helps!

---

### Post by efrens on 2010-08-04
[https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes)

workaround A worked for me.

---

