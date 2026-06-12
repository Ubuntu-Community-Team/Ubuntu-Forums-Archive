---
title: "Linux wifi usb adapter drivers?"
date: 2016-10-02
forum: Networking &amp; Wireless
---

### Post by richard12345 on 2016-10-02
Ok, so I'm new to linux and I'm so confused about this driver thing in linux. Can someone just fill me in on how do installing drivers in linux work? I obviously know how to install them in windows 7 using a disk and everything or getting the driver in via internet. But what about linux? I'm dual booting ubuntu by the way. what do i need to do to install my wifi driver? How does installing drivers really work in linux? I would like a universal answer if possible. PLEASE do not make fun of me because I'm a noob. I know how drivers work in this and that, but in linux, it's just so gosh dang frustrating like HECK. SOMEONE HELP! Thanks:)

---

### Post by Bucky Ball on 2016-10-03
*Thread moved to **Networking and Wireless**.* 

Welcome. First thing: deep breath and slow down. You may not even need to install drivers. Linux is not like Win and many drivers are already present in the kernel. No need to drag them in from all over and insert 25 digit authentication keys. A few questions.

You have Ubuntu installed?
If so, which release?
Is this an internal wifi card or a USB wifi dongle?

If USB, plug it in and run these two commands:

```
sudo lsusb
sudo lshw -C network
```

If it is internal, just run the second command. Post the output back here between code tags (see the link in my signature at bottom of this post for how). 

This may sound silly, but how do you know it is not working? If USB, have you plugged it in and checked? Have you plugged it in and done an update? Have you done an update since you installed? If not, do so then plug the device in if USB or check the network icon for networks if internal.

PS: There is rarely a universal answer here and certainly not to this. Some cards will work right of the bat and others no. Not about Ubuntu, it's about the companies that make the cards. If you stick around you'll find that you will buy things that you know work in Linux rather than the first thing off the shelf that looks good. Makes life a LOT easier. :)

---

### Post by richard12345 on 2016-10-03
Sorry for the long response, thanks btw I really appreciate it. Yeah I already knew about the proprietary drivers but my question is, how do I install the proprietary drivers on ubuntu?  What's the difference of installing wireless cards and usb and routers? My version of ubuntu is 16.0.4.1 desktop and I am dual booting.

---

### Post by jeremy31 on 2016-10-03
Do you have internet access with Ubuntu?

I don't think there are any proprietary drivers for USB wifi devices in Ubuntu.  Do you currently have a USB wireless adapter or are you looking for recommendations? 

If you do have a USB wifi, please provide the results from terminal (CTRL + t) then enter ```
lsusb
```

---

### Post by chili555 on 2016-10-03
>  How does installing drivers really work in linux? I would like a universal answer if possible. PLEASE do not make fun of me because I'm a noob. I know how drivers work in this and that, but in linux, it's just so gosh dang frustrating like HECK. SOMEONE HELP! No one here is going to make fun of you because you are a noob unless they want to get banned. Jeremy and I feel quite strongly about that. As well, he is one of the nicest, most polite gurus we see here. You are in great hands.

A great many wireless drivers are built in to the Linux kernel already. All that is necessary is to insert the device and connect. A very few devices, either very new or very old, don't yet have default drivers and we must install them after the fact. 

If your device isn't working, we need to figure out what driver to install, develop a process and tell you how to do it. Jeremy will explain the steps as he goes along.

The first step is to identify the device. Please insert it and then open a terminal Ctrl+Alt+t and run:```
lsusb
```You will get an output something like, but not exactly like this:> Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 058f:6366 Alcor Micro Corp. Multi Flash Reader
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID [COLOR="#FF0000"]0846:9020 NetGear, Inc. WNA3100(v1) Wireless-N 300 [Broadcom BCM43231][/COLOR]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 003: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 004 Device 002: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop LaserOnce we see the exact details, Jeremy can proceed.

---

### Post by richard12345 on 2016-10-03
Good news and bad news, bad news is that i can't connect to the internet on my ubuntu at all. The good news is that I do indeed have a netgear WNA3100. This is exactly it:

[COLOR=#000000]*Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub*[/COLOR]
[COLOR=#000000]*Bus 002 Device 002: ID 058f:6366 Alcor Micro Corp. Multi Flash Reader*[/COLOR]
[COLOR=#000000]*Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub*[/COLOR]
[COLOR=#000000]*Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub*[/COLOR]
[COLOR=#000000]*Bus 001 Device 002: ID *[/COLOR][COLOR=#FF0000]*0846:9020 NetGear, Inc. WNA3100(v1) Wireless-N 300 [Broadcom BCM43231]*[/COLOR]
[COLOR=#000000]*Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub*[/COLOR]
[COLOR=#000000]*Bus 004 Device 003: ID 046d:c52b Logitech, Inc. Unifying Receiver*[/COLOR]
[COLOR=#000000][I]Bus 004 Device 002: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser


[/I][/COLOR]

---

### Post by jeremy31 on 2016-10-03
I would not say that having a WNA3100 is good news as I had one and it was trouble even when I did get it working.  I would suggest getting a TP-Link  TL-WN722N 150 Mbps USB wifi device as they work very well in Ubuntu and don't require ndiswrapper and WinXP drivers, see [http://ubuntuforums.org/showthread.php?t=2264020&highlight=WNA3100](http://ubuntuforums.org/showthread.php?t=2264020&highlight=WNA3100)

I am sorry that I don't have better news

---

### Post by richard12345 on 2016-10-03
I appreciate you helping and no need to be sorry. I just have a few other questions:

1.) What if I have a live linux cd running? If I have a proper Wifi usb, will it automatically connect to the internet?
2.) Is there way to get ndiswrapper or winxp driver from a computer with wifi and then extract it to the ubuntu os?
3.) What kind of problems did you experience with the WNA3100 Wireless Adapter after installing the driver?
4.) Can you do penetration testing with this adapter?

---

### Post by wildmanne39 on 2016-10-03
> Cracking: Requests for help about any form of password or encryption "cracking" are not supported. Even though there are packages such as aircrack in the repositories, discussions about cracking or software related to cracking often lead to discussions about illegal activities. Such threads will be closedThread closed! your best option is to try the kali forum or aircrack forum.
[https://ubuntuforums.org/misc.php?do=showrules](https://ubuntuforums.org/misc.php?do=showrules)
Thanks

---

