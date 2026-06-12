---
title: "[SOLVED] This has forced me to go back to Vista"
date: 2008-07-19
forum: Networking &amp; Wireless
---

### Post by hobs on 2008-07-19
I've been struggling to get wireless to work on Hardy for a few weeks now.  I have tried b43-fwcutter, ndiswrapper and absolutely nothing worked.  I actually gave up and went back to Vista so I could have functional wireless. 

But, I do dislike Vista and much prefer ubuntu/kubuntu so last night I put in the Kubuntu Hardy CD and because wireless worked on the live CD, I partitioned and installed.  Sadly, now wireless does not work and I'm forced to run Vista.  

In the live CD all I had to do was enable wireless from the hardware manager where it installed b43-fwcutter for me.  In the installed version I am not able to check the enable box.  All I tried was installing b43-fwcutter manually, but this did not work.

Help me free myself from Vista.

---

### Post by cybrsaylr on 2008-07-19
Just go through this forum. I had the same problem till yesterday when I finally got my wireless working on my laptop. Now I'm totally MS & MAC free.

---

### Post by hyper_ch on 2008-07-19
probably the least nerve-breaking thing would be to get a wifi card that works out of the box even now.... but it's kind of hard to believe, that the wifi worked in the live cd... can you test that again?

---

### Post by hobs on 2008-07-19
I am running wireless quite smoothly from the live CD.  I have a wired connection available so I can go to my Kubuntu install and work from there if anyone has some nice suggestions.

---

### Post by hyper_ch on 2008-07-19
strange that it works from the live cd...

---

### Post by Ayuthia on 2008-07-19
> **hobs said:**
> I am running wireless quite smoothly from the live CD.  I have a wired connection available so I can go to my Kubuntu install and work from there if anyone has some nice suggestions.Can you open up the Konsole and post the results of the following:
```
ls /lib/firmware
ls /lib/firmware/b43
lshw -C network
```
The first command is checking to see if the b43 firmware has been installed.  The second will help us see what wireless card you are using and see if is able to use the firmware or if it is having problems.

---

### Post by hobs on 2008-07-19
ls /lib/firmware:

```
2.6.24-16-generic     bcm43xx_initval05.fw  bcm43xx_microcode11.fw
2.6.24-19-generic     bcm43xx_initval06.fw  bcm43xx_microcode2.fw
bcm43xx_initval01.fw  bcm43xx_initval07.fw  bcm43xx_microcode4.fw
bcm43xx_initval02.fw  bcm43xx_initval08.fw  bcm43xx_microcode5.fw
bcm43xx_initval03.fw  bcm43xx_initval09.fw  bcm43xx_pcm4.fw
bcm43xx_initval04.fw  bcm43xx_initval10.fw  bcm43xx_pcm5.fw
```

ls /lib/firmware/b43:

```
ls: cannot access /lib/firmware/b43: No such file or directory

```
lshw -C network:

```
WARNING: you should run this program as super-user.
  *-network
       description: Network controller
       product: BCM4312 802.11a/b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0 module=ssb
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 02
       serial: 00:1c:23:84:0d:c9
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=b44 driverversion=2.0 ip=192.168.0.100 latency=64 module=ssb multicast=yes
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:1c:26:1a:15:e5
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g
```

---

### Post by Ayuthia on 2008-07-19
> **hobs said:**
> ls /lib/firmware:

```
2.6.24-16-generic     bcm43xx_initval05.fw  bcm43xx_microcode11.fw
2.6.24-19-generic     bcm43xx_initval06.fw  bcm43xx_microcode2.fw
bcm43xx_initval01.fw  bcm43xx_initval07.fw  bcm43xx_microcode4.fw
bcm43xx_initval02.fw  bcm43xx_initval08.fw  bcm43xx_microcode5.fw
bcm43xx_initval03.fw  bcm43xx_initval09.fw  bcm43xx_pcm4.fw
bcm43xx_initval04.fw  bcm43xx_initval10.fw  bcm43xx_pcm5.fw
```

ls /lib/firmware/b43:

```
ls: cannot access /lib/firmware/b43: No such file or directory

```

This looks like you have installed bcm43xx-fwcutter instead of b43-fwcutter.  The bcm43xx is the depreciated driver.  The b43 firmware is generally created in the b43 folder and the firmware does not start with bcm43xx.  You can try to install the b43-fwcutter again (from the Konsole):
```
sudo apt-get install b43-fwcutter
```Of course this is should only be done if you can connect to the internet by a wired connection.  You can also install this by going into Adept and selecting b43-fwcutter.

---

### Post by hobs on 2008-07-19
> **Ayuthia said:**
> This looks like you have installed bcm43xx-fwcutter instead of b43-fwcutter.  The bcm43xx is the depreciated driver.  The b43 firmware is generally created in the b43 folder and the firmware does not start with bcm43xx.  You can try to install the b43-fwcutter again (from the Konsole):
```
sudo apt-get install b43-fwcutter
```Of course this is should only be done if you can connect to the internet by a wired connection.  You can also install this by going into Adept and selecting b43-fwcutter.

sudo apt-get install b43-fwcutter:
```
Reading package lists... Done
Building dependency tree
Reading state information... Done
b43-fwcutter is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

---

### Post by Ayuthia on 2008-07-19
> **hobs said:**
> sudo apt-get install b43-fwcutter:
```
Reading package lists... Done
Building dependency tree
Reading state information... Done
b43-fwcutter is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

Interesting.  Well, you can try this link:
[http://ubuntuforums.org/showthread.php?t=779754](http://ubuntuforums.org/showthread.php?t=779754)
Try and do the Downloading Firmware section.  That should get the firmware installed for you.

---

### Post by mg620 on 2008-07-19
Hobs is not alone...I have the same wacky issue...wireless works flawlessly off Kubuntu live CD (with absolutely no coaxing from me), but not when Kubuntu is installed.  I only tried Kubuntu because I can't get my wireless card to work in Ubuntu (which I've used off and on for a few years).  The upside is Kubuntu is really shiny and slick...glad I tried it...will stick with it if I can get wireless to work.

I will now stay out of the way and try these recommendations myself...just wanted to lend some moral support.

---

### Post by hobs on 2008-07-20
> **Ayuthia said:**
> Interesting.  Well, you can try this link:
[http://ubuntuforums.org/showthread.php?t=779754](http://ubuntuforums.org/showthread.php?t=779754)
Try and do the Downloading Firmware section.  That should get the firmware installed for you.

Thank you so much! This seemed to do the trick.  Think, after nights of frustration it took less than 5 minutes to fix this! mg620, I hope it works for you as well.

---

