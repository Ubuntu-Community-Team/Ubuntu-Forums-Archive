---
title: "Ubuntu 14.04 not recognizing wireless card"
date: 2014-10-31
forum: Networking &amp; Wireless
---

### Post by YardDart63 on 2014-10-31
Hello all. I am totally new to Ubuntu. I installed Ubuntu 14.04 alongside Windows 7 on a HP Pavilion DV6000 laptop. When I click on the networking icon, it shows my wired connection but doesn't show anything about wireless. The lspci command in Terminal shows I have a Broadcom BCM4311 802/11b/g WLAN (rev 02) wireless card. I started following lswest's guidelines in a similar post from 2008 ([http://ubuntuforums.org/showthread.php?t=780212&p=4871609#post4871609](http://ubuntuforums.org/showthread.php?t=780212&p=4871609#post4871609)). I was making good progress until I entered the (sudo modprobe -r ssb) command, and I was met with (modprobe: FATAL: Module ssb is in use). Can someone help me out with this? Any help appreciated.

---

### Post by grahammechanical on 2014-10-31
That thread dates from 2008. And that is a long time. The suggestions there may not apply. There is something simple that you can try. Go to System Settings>Software and Updates>Additional Drivers tab and see if Additional Drivers can find a driver for that card. You can also try this command

```
rfkill list
```

This is what I see on my machine

>  0: phy0: Wireless LAN    
Soft blocked: no
Hard blocked: no


Soft blocked would mean that there is not a driver installed or WiFi is disabled. Hard Block means that the WiFi adapter is switched off. Perhaps it is disabled in the machine's BIOS. Is there another OS on that machine? Has wireless been disabled in that OS? Do you need to activate the Wifi adapter by pressing a Fn key?

There are ways and means but some information is needed.

Regards.

---

### Post by westie457 on 2014-10-31
Hi, YardDart63 if you try grahammechanical's suggestion and your wifi does not work give this a try. ignore all errors and warnings,just keep going through the commands.```
sudo apt-get purge bcmwl-kernel-source
sudo apt-get install b43-fwcutter firmware-b43-installer
sudo modprobe -rfv b43
sudo modprobe b43
```

Let us know how it goes.

---

### Post by Bucky Ball on 2014-10-31
*Thread moved to **Networking & Wireless**.*

Welcome. I had a DV6000. The drivers for that card are in Additional Drivers. You need to get online with a cable and update, then check Additional Drivers. Please provide the output of this command:

```
sudo lshw -C network
```

That will tell us what driver, if any, is already installed.

PS: As suggested, the link you provide is old and out of date (in fact, completely redundant ... I didn't even do that on 8.04 when I was using a DV6000). That card should be working out of the box by now. Surprised it's not.

---

### Post by YardDart63 on 2014-11-01
Problem solved. I reinstalled Ubuntu and downloaded all available updates. Wireless works flawlessly now. Thanks to everyone for your suggestions, I apologize for taking your time unnecessarily. I feel kinda dumb now. :oops:

---

### Post by Bucky Ball on 2014-11-01
All good. You just got here.

You DID mark the thread as solved to help others, though, so gold star, big tick, thumbs up, kudos for that. ;)

---

