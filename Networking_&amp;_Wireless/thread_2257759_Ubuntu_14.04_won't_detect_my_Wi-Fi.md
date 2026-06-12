---
title: "Ubuntu 14.04 won't detect my Wi-Fi"
date: 2014-12-22
forum: Networking &amp; Wireless
---

### Post by keltonkostis on 2014-12-22
I just installed Ubuntu on a secondary computer from a Live USB (created using Rufus). It won't detect my Wi-Fi and picking "edit connections" just gives me an option to add a connecting which makes me put in a whole bunch of information I don't even know. My wi-fi worked fine on Windows 7, what's going on?

---

### Post by TheFu on 2014-12-22
What is the output from 
**rfkill list**

BTW, there is a wifi troubleshooting script that would be helpful if the answer isn't obvious from the rfkill output.

---

### Post by keltonkostis on 2014-12-22
The output is:
0: ideapad wlan: Wireless LAN
Soft blocked: no
Hard blocked: no

---

### Post by Pilot6 on 2014-12-22
Pls give output of

lspci -knn | grep Net -A2

---

### Post by keltonkostis on 2014-12-22
Oh god, so much output:
04:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b /g LP-PHY
[14e4:4315] (rev 01)
Subsystem:Broadcom Corporation Device [14e4:04b5]
Kernel driver in use: b43-pci-bridge
07:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express [14e4:1713] (rev 02)
Subsystem: Lenovo IdeaPad S10e [17aa:3a23]
Kernel driver in use: tg3
That's it. Also, I'm not using an ethernet cable.

---

### Post by Pilot6 on 2014-12-22
You may want to install wl driver. Here is the manual.

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

---

### Post by keltonkostis on 2014-12-22
Sorry for the late reply, but which one is/how do I install the wl driver? I did a [COLOR=#333333][FONT=UbuntuMono]lspci -vvnn | grep -A 9 Network and it said Kernel driver in use: b43-pci-bridge[/FONT][/COLOR]

[COLOR=#333333][FONT=Ubuntu][/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu][/FONT][/COLOR]

---

### Post by Pilot6 on 2014-12-22
I gave a link to the manual.

---

### Post by keltonkostis on 2014-12-22
I know, but I couldn't see what driver download it was. Since the other computer is offline (I have no other way of connecting to the internet) it would have to be moved over through a USB drive (all I have access to right now) and I have no idea what to do.

---

### Post by Pilot6 on 2014-12-22
Yoy have now b43. There is a manual without interrnet access too.
You need bcmwl-kernel-source

---

### Post by keltonkostis on 2014-12-22
I downloaded it and copied it to my Ubuntu computer through a USB drive, now what?

---

### Post by Pilot6 on 2014-12-22
Now put it into your home folder and type in terminal

sudo dpkg -i bcmwl

then press <Tab> and the rest of file name will appear.
Then press <Enter>

---

### Post by keltonkostis on 2014-12-22
I downloaded it, now what?

Wait, nvm. I saw your other post....

---

### Post by keltonkostis on 2014-12-22
OK, I tried that but it can't find the archive. Does it need the compressed .tar.gz?

Edit: Even the compressed form doesn't work. I downloaded [bcmwl_6.30.223.248+bdcom.orig.tar.gz]("https://launchpad.net/ubuntu/+archive/primary/+files/bcmwl_6.30.223.248%2Bbdcom.orig.tar.gz") from [https://launchpad.net/ubuntu/+source/bcmwl/6.30.223.248+bdcom-0ubuntu1](https://launchpad.net/ubuntu/+source/bcmwl/6.30.223.248+bdcom-0ubuntu1), is that correct?

---

### Post by Pilot6 on 2014-12-22
You need to download a deb package, not tar.gz.

---

### Post by Pilot6 on 2014-12-22
[http://launchpadlibrarian.net/181487980/bcmwl-kernel-source_6.30.223.248%2Bbdcom-0ubuntu1_amd64.deb](http://launchpadlibrarian.net/181487980/bcmwl-kernel-source_6.30.223.248%2Bbdcom-0ubuntu1_amd64.deb)

---

### Post by keltonkostis on 2014-12-22
You linked the amd64 package. It's a 32-bit computer. (and ubuntu install)

---

### Post by Pilot6 on 2014-12-22
OK. Then

[https://launchpad.net/ubuntu/+source/bcmwl/6.30.223.248+bdcom-0ubuntu1/+build/6238743/+files/bcmwl-kernel-source_6.30.223.248%2Bbdcom-0ubuntu1_i386.deb](https://launchpad.net/ubuntu/+source/bcmwl/6.30.223.248+bdcom-0ubuntu1/+build/6238743/+files/bcmwl-kernel-source_6.30.223.248%2Bbdcom-0ubuntu1_i386.deb)

You may need also dkms package too, if it is not installed yet.

---

### Post by keltonkostis on 2014-12-22
It said dependency problems, leaving unconfigured. Can you link to the "dkms" thing and tell me the command to install it?

---

### Post by Pilot6 on 2014-12-22
Did it ask only for dkms or anything else?

Dkms is here

[http://mirrors.kernel.org/ubuntu/pool/main/d/dkms/dkms_2.2.0.3-1.1ubuntu5.14.04_all.deb](http://mirrors.kernel.org/ubuntu/pool/main/d/dkms/dkms_2.2.0.3-1.1ubuntu5.14.04_all.deb)

---

### Post by keltonkostis on 2014-12-22
Thank you, it works now, issue resolved.

---

### Post by m-veron622 on 2014-12-23
Hello, I am new with Ubuntu 14.04 and also had it installed via thumbdrive, but not with Rufus(?). I am experiencing the same problem, except when I type the command **rfkill list**, this is what I receive:

0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no

Any advice on further action??

---

### Post by Pilot6 on 2014-12-23
You better create a new thread. Yhe issue in this thread is solved. You have something else.

And give there

lspci -knn | grep Net -A2

---

