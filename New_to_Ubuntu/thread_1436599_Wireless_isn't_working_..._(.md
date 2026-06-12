---
title: "Wireless isn't working ... :("
date: 2010-03-22
forum: New to Ubuntu
---

### Post by txsweetheart09 on 2010-03-22
I'm running Windows Vista on HP Pavilion dv6000

My Broadcom wireless card is 

```
BCMWL6.SYS

Version 4.102.15.61

Broadcom 802.11b/g WLAN 
```I found this tutorial but I don't know if it will work with this version of ubuntu.

[https://wiki.ubuntu.com/HP_Pavillion_dv6000_%28dv6604nr%29]("https://wiki.ubuntu.com/HP_Pavillion_dv6000_%28dv6604nr%29.")

 I used wubi as the installer on my Windows system.

My computer is a 32 bit system with AMD Turion 64X2 and Nvidia graphics card.

My wireless driver is [sp37746.exe,  (1/1, 17.67M)]("http://h10025.www1.hp.com/ewfrf/wc/softwareDownloadIndex?softwareitem=ob-57604-1&lc=en&dlc=en&cc=us&lang=en&os=2093&product=1842155")

If you need to move this, please do. I just posted in the beginners section since I'm a newbie at this..


It won't show any wireless connections whatsoever.

I uninstalled wubi to see if I can figure out a solution before I reinstall it onto my system.


Thanks for any help you may provide.

---

### Post by txsweetheart09 on 2010-03-22
I just installed a new HD so I was using wubi so I don't have to do anything permanent just yet.

---

### Post by overdrank on 2010-03-22
Hi and welcome, please be patient and do not create multiple threads on the same issue. Threads merged. :)

---

### Post by sandyd on 2010-03-22
I believe that you have a 4321AG card
[[click here]]("apt:/bcmwl-kernel-source,bcmwl-modaliases") to install drivers.

---

### Post by readycarpenter on 2010-03-22
> **txsweetheart09 said:**
> I'm running Windows Vista on HP Pavilion dv6000

My Broadcom wireless card is 

```
BCMWL6.SYS

Version 4.102.15.61

Broadcom 802.11b/g WLAN 
```I found this tutorial but I don't know if  it will work with this version of ubuntu.

[https://wiki.ubuntu.com/HP_Pavillion_dv6000_%28dv6604nr%29]("https://wiki.ubuntu.com/HP_Pavillion_dv6000_%28dv6604nr%29.")

 I used wubi as the installer on my Windows system.

My computer is a 32 bit system with AMD Turion 64X2 and Nvidia graphics  card.

My wireless driver is [sp37746.exe,  (1/1, 17.67M)]("http://h10025.www1.hp.com/ewfrf/wc/softwareDownloadIndex?softwareitem=ob-57604-1&lc=en&dlc=en&cc=us&lang=en&os=2093&product=1842155")


It won't show any wireless connections whatsoever.

I uninstalled wubi to see if I can figure out a solution before I  reinstall it onto my system.


Thanks for any help you may provide.

**I also posted this in the beginner's section since I'm a newbie at this. Please inform me if I have to move that thread or delete it. Thank you**

I'm pretty sure wubi might be the problem, I've not had good luck with it, 

just boot the ubuntu cd, shrink your windows partition, then install ubuntu to "largest unused space", 
if your wireless card is usb make sure it is inserted during the installation. 

then most wireless dont work out of box, so you need to be connected to a wired network, update your newly installed ubuntu, 

then restart and run >system>admin>hardware drivers to see if there are any wireless drivers, 

this has worked for me for at least 20 ubuntu boxes/laptops

cheers hope this helps, I love UBUNTU!

---

### Post by txsweetheart09 on 2010-03-22
I don't want to create a double boot system right now so I used wubi. I just got a new HD since my last one  got damaged by falling so I don't want to do anything permanent right now. 

Sorry about double posting.

My wireless card is internal as far as I know. I had to send it to HP to get repaired in the summer of 07.

---

### Post by txsweetheart09 on 2010-03-23
> **carlee said:**
> I believe that you have a 4321AG card
[[click here]]("apt:/bcmwl-kernel-source,bcmwl-modaliases") to install drivers.


It won't let me download it. Do I have to download it through Linux ?

---

### Post by waynefoutz on 2010-03-23
> **txsweetheart09 said:**
> It won't let me download it. Do I have to download it through Linux ?

yeah you have to download that through linux.

You can download the deb file here:
[http://packages.ubuntu.com/karmic/i386/bcmwl-kernel-source/download](http://packages.ubuntu.com/karmic/i386/bcmwl-kernel-source/download)

---

### Post by undecim on 2010-03-23
> **readycarpenter said:**
> I'm pretty sure wubi might be the problem, I've not had good luck with it

That's not the kind of problem Wubi would cause. Wubi causes boot problems. Once you boot your Wubi-installed Ubuntu system, its just like any other Ubuntu install, but just running from a loopback device (i.e. it stores its files inside another file on the Windows install).

---

### Post by mujahied on 2010-03-23
just install from the cd dude and yre problem should be solved 
i have been running ubuntu for a while now on my laptop and working wireless i also have an hp laptop

---

### Post by txsweetheart09 on 2010-03-23
I updated the system and installed broadcom STA driver and I see my wifi connection but can't connect now, is there another  wifi manager available?

---

### Post by txsweetheart09 on 2010-03-24
Did I do something wrong ?

---

### Post by djackn on 2010-03-24
> **txsweetheart09 said:**
> I updated the system and installed broadcom STA driver and I see my wifi connection but can't connect now, is there another wifi manager available?
 
[FONT=Georgia][SIZE=1][FONT=Georgia][SIZE=1][LEFT]Have you been using Synaptic Package Manager to do your installs?[/LEFT]
[/SIZE][/FONT][/SIZE][/FONT]

---

### Post by txsweetheart09 on 2010-03-24
No. I did it under hardware manager. It gave me the drives that ubuntu had tested to see if they would work. It had my broadcom drive in there. I can see my connection and all and set up a new connection but when it connects, it is just left at activating during my wireless setup. My wired connection works fine.

---

### Post by txsweetheart09 on 2010-03-24
> **djackn said:**
> [FONT=Georgia][SIZE=1][FONT=Georgia][SIZE=1][LEFT]Have you been using Synaptic Package Manager to do your installs?[/LEFT]
[/SIZE][/FONT][/SIZE][/FONT]


How do I download the synaptic package manager? I didn't see it under my system. (I'm on Windows right now so I can't really tell...). Do I install it from the website itself?

---

### Post by bkratz on 2010-03-24
> **txsweetheart09 said:**
> How do I download the synaptic package manager? I didn't see it under my system. (I'm on Windows right now so I can't really tell...). Do I install it from the website itself?




Go to system>>administration>>Synaptic Package Manager is there already

---

### Post by bkratz on 2010-03-24
> **txsweetheart09 said:**
> I updated the system and installed broadcom STA driver and I see my wifi connection but can't connect now, is there another  wifi manager available?



I assume you left clicked on the nework icon to see your network, did you set it up by right clicking on it and selecting things like encryption?

---

### Post by txsweetheart09 on 2010-03-24
> **bkratz said:**
> I assume you left clicked on the nework icon to see your network, did you set it up by right clicking on it and selecting things like encryption?


Yes. It just stays at activating & doesn't connect at all.

---

