---
title: "Problem with Ralink RT2870 driver on Ubuntu 15.10"
date: 2015-10-23
forum: Networking &amp; Wireless
---

### Post by aurora4 on 2015-10-23
Hey,

I have a Ralink RT2870 dongle (mt7601) that I would like to use with Ubuntu MATE 15.10 for better internet performance.
I used this driver from this post [http://askubuntu.com/questions/457061/ralink-148f7601-wifi-adapter-installation](http://askubuntu.com/questions/457061/ralink-148f7601-wifi-adapter-installation)
It used to work with Ubuntu MATE 15.04 but it doesn't with 15.10 >.<
It starts when you first install it but when you try to connect to a wifi point, it doesn't work and after trying again my system froze.
After force rebooting the system, Ubuntu threw a kernel panic and I couldn't get in... Can anyone please help me with finding an alternate driver? ^^
The documentation claims that the driver is in Linux Kernel 4.2 but it wasn't automatically detected so is there a way to enable that?

Thanks,
Aurora

---

### Post by huy4 on 2015-10-27
I have met the same problem. Ubuntu MATE 15.10 auto-recognised the driver mt7601 on the first use and after I updated some updates in the update manager, it haven't recognised the driver anymore. First, I installed Ubuntu 15.10 and met the same error. I tried to install the driver manually but it came to a crash so I installed Ubuntu MATE and hoped that it would work, but it was not. So I think this is a kernel update problem which led to the unrecognised driver. I hope Canonical will fix this error soon.

---

### Post by slickymaster on 2015-10-27
*Moved to the ***Networking & Wireless*** sub-forum*

---

### Post by chili555 on 2015-10-27
The driver mt7601u exists in Ubuntu 15.10. Does it load automatically?```
lsmod | grep 7601
```Are there any clues in the log?```
dmesg | grep 7601
```What is your exact device?```
lsusb
```

----------------------------------

Firmware: ```
sudo wget https://github.com/porjo/mt7601/raw/master/src/mcu/bin/MT7601.bin -O /lib/firmware/mt7601u.bin
```

---

### Post by huy4 on 2015-10-28
Below is my os's information. Please check it out. 

```
huynguyenibe@huynguyenibe:~$ lsmod | grep 7601
mt7601u                86016  0
mac80211              659456  1 mt7601u
cfg80211              483328  2 mac80211,mt7601u
```

```
huynguyenibe@huynguyenibe:~$ dmesg | grep 7601
[    1.723705] usb 1-3: New USB device found, idVendor=148f, idProduct=7601
[   10.094799] mt7601u 1-3:1.0: ASIC revision: 76010001 MAC revision: 76010500
[   10.397856] mt7601u 1-3:1.0: Direct firmware load for mt7601u.bin failed with error -2
[   10.398592] mt7601u: probe of 1-3:1.0 failed with error -2
[   10.398664] usbcore: registered new interface driver mt7601u
```

```
huynguyenibe@huynguyenibe:~$ lsusb
Bus 001 Device 003: ID 148f:7601 Ralink Technology, Corp. MT7601U Wireless Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 1bcf:0007 Sunplus Innovation Technology Inc. Optical Mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 04d9:1702 Holtek Semiconductor, Inc. Keyboard LKS02
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

---

### Post by chili555 on 2015-10-28
> mt7601u 1-3:1.0: Direct firmware load for mt7601u.bin failed with error -2The firmware is not present, as we suspected.

With a temporary working internet connection by ethernet, tethered or whatever means possible, please do:```
sudo wget https://github.com/porjo/mt7601/raw/master/src/mcu/bin/MT7601.bin -O /lib/firmware/mt7601u.bin
sudo modprobe -r mt7601u  &&  sudo modprobe mt7601u
```Your wireless should be working, however, it might take a reboot.

---

### Post by huy4 on 2015-10-28
Wow, this is great. It works again. Thanks for your help.

---

### Post by slickymaster on 2015-10-28
Please don't forget to [mark the thread as solved]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads"), now that chili555 solution fixed your problem. It lets other people searching the forums know that this thread provides a working solution for the problem.

---

### Post by Dhairav_Mehta on 2015-11-25
heyy,thanks a lot ..worked for me too,what seemed to be the problem and how did you fix it?..i'll be glad to learn the error that occrred
'

---

### Post by chili555 on 2015-11-25
It was only that the required firmware isn't installed by default and needs, at least for now, to be installed later.

The real learning point is that, when something isn't working as expected, check the log:```
dmesg
```Try to fix whatever is reported and you will almost always succeed. As you can see above, dmesg told us everything:> mt7601u 1-3:1.0: Direct firmware load for mt7601u.bin failed with error -2

---

