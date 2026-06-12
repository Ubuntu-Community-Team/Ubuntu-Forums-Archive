---
title: "wlan0 not showing up"
date: 2008-05-26
forum: Networking &amp; Wireless
---

### Post by ayq on 2008-05-26
I have a USB wireless adapter that came with a CD with drivers on it. The drivers are for Windows XP.

Upon googling, I learn about ndiswrapper and how to get the drivers up and running on my Linux box.

So, I use ndiswrapper and follow a couple of guides.

ndiswrapper -i thedriver.inf
ndiswrapper -l
(blah blah, everything's working ok. the driver is installed and the hardware is detected)
ndiswrapper -m
modprobe ndiswrapper

no errors are returned on any of these. everything seems to be going fine until:
iwconfig

it returns eth0 and a local loopback and says to me that they aren't wireless. Upon rebooting and a couple of changes here and there in some config files, the problem still persists. Am I forgetting something? Did I mess something up without knowing about it? Every single guide that I read basically goes from "modprobe ndiswrapper" and then straight into setting up wlan0 for WEP/WPA access OR the guide just ends without getting into encryption. Not a single one that I've found has any troubleshooting on "what happens if wlan0 doesn't even show up?"

So, that's why I thought I'd ask here.

Thanks in advance.

---

### Post by danpos on 2008-05-26
@ayq

It seems that the wlan0 device isn't getting up at start up, but is it being probed? What does happen when you type

```
ifconfig -a
```

at terminal?

If something like 'wlan0' or similar is showed up so you just need to get the device up with

```
sudo ifconfig wlan0 up
```

and so set it up using network-manager applet or whatever. Anyway, is not your adapter supported natively by Linux? What's the output from the following command (at terminal):

```
lsusb
```

Danpos.

---

### Post by ayq on 2008-05-26
> **danpos said:**
> @ayq

It seems that the wlan0 device isn't getting up at start up, but is it being probed? What does happen when you type

```
ifconfig -a
```

at terminal?

If something like 'wlan0' or similar is showed up so you just need to get the device up with

```
sudo ifconfig wlan0 up
```

and so set it up using network-manager applet or whatever. Anyway, is not your adapter supported natively by Linux? What's the output from the following command (at terminal):

```
lsusb
```

Danpos.

ifconfig -a shows eth0 and lo

lsusb shows a bunch of entries, most of which are all 0s except for my wireless adapter:
Bus 1 Device 2: 1915:2233
Bus 001 Device 002: 1915:2233

so I take it it's not recognized?

---

### Post by cdtech on 2008-05-26
iwconfig....

---

### Post by ayq on 2008-05-26
> **cdtech said:**
> iwconfig....

[quote=ayq]no errors are returned on any of these. everything seems to be going fine until:
iwconfig

it returns eth0 and a local loopback and says to me that they aren't wireless.[/quote]

:guitar:

---

### Post by cdtech on 2008-05-26
Check the contents of the /etc/iftab file and make sure that no other device has the wlan0 driver name reserved for it:

user@ubuntu:~$ cat /etc/iftab

---

### Post by ayq on 2008-05-26
> **cdtech said:**
> Check the contents of the /etc/iftab file and make sure that no other device has the wlan0 driver name reserved for it:

user@ubuntu:~$ cat /etc/iftab

No such file.

I didn't mention that I'm not running Ubuntu (if it's Ubuntu specific). I'm actually running back|track 3.

---

### Post by cdtech on 2008-05-26
Sorry, as of 7.10 use this file. Change the entries of the appropriate macs

/etc/udev/rules.d/70-persistent-net.rules

---

### Post by cdtech on 2008-05-26
> **ayq said:**
> No such file.

I didn't mention that I'm not running Ubuntu (if it's Ubuntu specific). I'm actually running back|track 3.

I see. I had to comment out a device that was persistent to my device in order for it to work. Sorry about the non help, maybe this will give you something more to look for.

---

### Post by wernotalone on 2008-05-26
I'm having the same problem I think. 

Iwconfig:
lo        no wireless extensions.

eth0      no wireless extensions.

lsub:
Bus 006 Device 002: ID 04f2:b008 Chicony Electronics Co., Ltd 



I've tried a bunch of guides, and I get to the same point as the poster, where wlan0 should be showing up but isn't.

---

