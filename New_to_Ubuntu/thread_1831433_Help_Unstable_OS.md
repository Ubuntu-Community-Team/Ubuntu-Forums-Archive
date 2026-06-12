---
title: "Help Unstable OS"
date: 2011-08-23
forum: New to Ubuntu
---

### Post by sketchme on 2011-08-23
I am having a serous problem with OS freezing every little bit. I have ubuntu 10.04. I originally had windows and then added ubuntu and eventually tried to get rid of windows. but it is still in the directory when I start up... I wonder if this could be part of the problem. I need some suggestions because how unstable this is its ridiculous. Tell me any other info that you guy need to help me.

---

### Post by Grenage on 2011-08-23
Hi there.

First off, did you have any stability issues when running windows?  While the residual windows boot option or files may exist, they shouldn't be causing any Linux problems.

I believe there is a memtest option in the grub boot menu; would you mind running that?  A few hours of testing will give you a good indication, especially if you're having frequent problems.

---

### Post by sketchme on 2011-08-23
> **Grenage said:**
> Hi there.

First off, did you have any stability issues when running windows?  While the residual windows boot option or files may exist, they shouldn't be causing any Linux problems.

I believe there is a memtest option in the grub boot menu; would you mind running that?  A few hours of testing will give you a good indication, especially if you're having frequent problems.

 Yes I had problems with windows too. It just kept on crashing on me repeatedly. I have been using memtest. its been half a day and still not done. Hopefully soon

---

### Post by M1ttenz11 on 2011-08-23
Yes memtest can take quite the time.
I have never had a problem like this, and I have been using 10.04 for some months now.
Im not very good with this sort of stuff, but... If you didnt run disk defrag and disc clean up etc, this might cause a problem, as disk defrag will help keep your hard drive 'in order?'
My friends always warn me to run those sort of stuff when im mucking about with partions and stuff.
but like I say, im no expert in this department, I hope you can get your problem sorted, if not, I hope you dont have any important information on the computer as it only takes about 20-30mins to re-install Ubuntu.

Good luck.

---

### Post by Grenage on 2011-08-24
> **sketchme said:**
> Yes I had problems with windows too. It just kept on crashing on me repeatedly. I have been using memtest. its been half a day and still not done. Hopefully soon

I'm not sure if the default memtest runs indefinitely, or whether it's just a through test.  The error count should be displayed on the fly, so you'll at least get some idea of what it's finding.

When there are seemingly random freezes (especially across operating systems), I usually start with memory, then take a look at the hard drive.

---

### Post by sketchme on 2011-08-24
> **Grenage said:**
> I'm not sure if the default memtest runs indefinitely, or whether it's just a through test.  The error count should be displayed on the fly, so you'll at least get some idea of what it's finding.

When there are seemingly random freezes (especially across operating systems), I usually start with memory, then take a look at the hard drive.


I finished mem test andit showed nothing still trying to figure out how to check my hard drive on linux. I think I need to back up my computer NOW.

---

### Post by SavageWolf on 2011-08-24
In Ubuntu run `sudo touch /forcefsck` and reboot.

---

### Post by jtarin on 2011-08-24
Are you by any chance running Ubuntu inside Windows (WUBI)?

---

### Post by sketchme on 2011-08-25
> **jtarin said:**
> Are you by any chance running Ubuntu inside Windows (WUBI)?

Well I did in the begining and then ubuntu messed up, and then downloaded it by itself next to windows with the WUBI sill in windows... probily a dumb idea

---

### Post by sketchme on 2011-09-02
I checked my hard drive and that works ok it says... I dont know what else to look at... Im tierd of this instability

---

### Post by mbuell on 2011-09-02
WUBI? Let us be clear - are you still running Ubuntu while Windows is running?

At this point, I would hope that you have a dual boot, and you are not trying to run a virtual machine, and you are not running a liveCD from inside Windows. 

To begin - basic hardware troubleshooting says to simplify everything, get it to run, then add stuff. If you have 2 OSes running, that isn't simple. 

In my experience, memtest usually lets me know pretty quickly (<20 minutes) if I may have a problem with the memory. Letting it run longer may be necessary, I won't rule it out. fsck to check the hard disk for bad spots, or Windows chkdisk for the windows partition. fsck should work for all. 

Checking the RAM and the hdd are quick and ez answers - frequently the problem is there and they help. Reinstalling the OS is another "quick and ez" answer - just less quick, and less easy. 

Technically, though, I think you may want to fall back to hardware trouble-shooting 101: remove everything that is not essential and boot. Disconnect everything except RAM, hdd, video, keyboard, mouse. Hardware issues can pop up from video cards - so you want to start the process with a very basic vid card. If it works, power down, add one thing, reboot. When it stops working, you have isolated the problem.  If you have a fancy $$$ vid card, add that back as one of the "later" steps. 

If you went back to the simplest setup, and you still have unstable systems - then it may be time to upgrade your hardware.

---

### Post by bcbc on 2011-09-02
> **sketchme said:**
> I checked my hard drive and that works ok it says... I dont know what else to look at... Im tierd of this instability

Please list your full specs: brand, model, graphics card, wireless card etc.

---

### Post by Miljet on 2011-09-02
A weak or failing power supply will cause many seemingly random problems. I added a second hard drive to my wife's computer and immediately started having freeze-ups, flash crashes, random reboots, etc. As soon as I removed the second drive, the problems quit. Replaced the power supply and now can run the second, and even third hard drive.

---

### Post by sketchme on 2011-09-05
I will start trouble shooting now today... I will have my specs up tell the end of the day..

---

