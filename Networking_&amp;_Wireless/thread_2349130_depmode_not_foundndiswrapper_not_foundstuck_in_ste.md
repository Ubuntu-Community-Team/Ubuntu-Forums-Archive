---
title: "depmode not found/ndiswrapper not found/stuck in step 3.7 of ndiswrapper wifi docs"
date: 2017-01-11
forum: Networking &amp; Wireless
---

### Post by edgarej on 2017-01-11
I'm trying to install the drivers for my netgear wna3100 wireless usb. Here are the step I have taken:

1. Downloaded and installed ndiswrapper common 1.5.7 package and ndiswrapper utils 1.9 amd64 from ubuntu packages. I would have loved to installed the latest ndiswrapper instead, but I don't know tars and balls and I figured getting the packages from ubuntu repositories is safer.

2. After installing, I typed ndiswrapper in the CLI and it spitted out the help message, so I figured ndiswrapper is at least installed.

3. Grabbed the the wna3100 inf files from my windows installation, brought it over to ubuntu and installed the inf files with ndiswrapper.

4. Typed ndiswrapper -l and it said I'm clear to go, driver and device is present (it said however that my mind is not present, but I think we could fly with that).

5. Typed in sudo depmode -a and sudo modprobe ndiswrapper and it spitted out errors beyond belief ("sudo: depmode: command not found" error and "modprobe: FATAL: Module ndiswrapper not found in directory /lib/modules/4.4.0-31-generic" error). After digging around in the forums, I found Jimmy Hoffa's body, the last chalice, and the holy lance (in your face Indiana Jones!). I also found out I needed some other packages, so I went and installed dkms 2.2 as well as ndiswrapper-dkms.

6. I typed in sudo depmode and ubuntu said it still hates me, but on the other hand it gave me the silent treatment when I typed in sudo modprobe ndiswrapper.

7. I rebooted ubuntu to slap it's face and see if it complies with the wireless thing. Nope, still no juice.

I'm currently stuck with still no wireless and absolutely no clue as to how to proceed. Any help would be greatly appreciated. I could give you Jimmy Hoffa's body as a token of gratitude. Thanks folks.

---

### Post by jeremy31 on 2017-01-11
Buy a TP-Link WN722N 150 Mbps and forget about the Netgear and ndiswrapper, your forehead and wall will thank you.  I have been down that road.  Even when it did work it the internet would stall, so I mailed it to chili555 and here is his [report](http://ubuntuforums.org/showthread.php?t=2264020&highlight=WNA3100)

You did have a typo in one command
```
sudo depmod -a
```
But ndiswrapper should run that when you load the windows files

---

