---
title: "Trying to use Aztech WL562USB in Ubuntu 10.04 LTS"
date: 2013-09-22
forum: Networking &amp; Wireless
---

### Post by fs3 on 2013-09-22
I am trying to get Aztech wl562usb wifi adapter to work under Ubuntu Lucid. Anyone having luck with it please help.
Thanks.

---

### Post by varunendra on 2013-09-23
Hi fs3, and Welcome to the forums ! :)

If you are not already aware, Ubuntu 10.04 desktop version has reached its EOL (End Of Life), means it is no more supported. There will be no security or software updates.

As such, the first thing I would suggest is to upgrade to 12.04 LTS. With newer kernel and drivers, your adapter might work without any efforts. If not, troubleshooting it would be easier on a newer, supported platform.

If you think it makes sense, I'd recommend to download the 12.04.3 ISO via torrent from here (64 bits if your system supports that) : [http://www.ubuntu.com/download/alternative-downloads](http://www.ubuntu.com/download/alternative-downloads)

Once downloaded, create a live USB or burn a CD and try it in live mode (Test without installing option) to make sure everything works. If satisfied, do an upgrade or better, do a fresh install if that isn't a problem for you.

I might be able to tell you in advance whether the adapter will work automatically or not if I knew its device ID. To let me see it, please post the output of -
```
lsusb
``` ....while the adapter is plugged in.

---

### Post by fs3 on 2013-09-23
Hi Varun,

The output s as such:

Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 148f:2573 Ralink Technology, Corp. RT2501USB Wireless Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

### Post by fs3 on 2013-09-23
Hi varun,
 
  Disregard the above, let me come back to you in a while. Thanks.

---

### Post by fs3 on 2013-09-23
Hi Varun,

The output is as such:
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 005: ID 148f:3070 Ralink Technology, Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

### Post by varunendra on 2013-09-23
> **fs3 said:**
> Bus 001 Device 002: ID 148f:2573 Ralink Technology, Corp. RT2501USB Wireless Adapter

> **fs3 said:**
> Bus 001 Device 005: ID 148f:3070 Ralink Technology, Corp.

Both your adapters are natively supported in 12.04. It is guaranteed that both of these will be recognized as soon as plugged in, although I can't predict about the performance.

I suggest you do upgrade to 12.04.3. Download via torrent and do a fresh install if possible.

---

### Post by fs3 on 2013-09-23
Hi Varun,   I am downloading the 12.04LTS, will do an upgrade soon. Thanks & have a nice day ahead.

---

### Post by varunendra on 2013-09-23
Good luck! And let me know if the native driver gives you any troubles, I'll be ready with my guns loaded :P

---

### Post by fs3 on 2013-09-24
Hi Varun,

  I had tested 12.04.03, both adapters are natively supported. Thanks.
Btw, I am looking at TP-Link Wifi adapters as backup, any good recommendation from you. Thanks. a bunch.

---

### Post by Bucky Ball on 2013-09-24
Good news. Please mark thread as solved from thread tools at the top right. ;)

---

### Post by varunendra on 2013-09-24
> **fs3 said:**
> Hi Varun,

  I had tested 12.04.03, both adapters are natively supported. Thanks.
Glad to hear that. :)

As for the recommendation on TP-Link adapters, I don't remember any in particular. As troubleshooters, obviously we come across only those ones that have some issues to be solved - minor or major. I'll have to do the same thing as you would do otherwise - search the forums with keywords "TP-Link" or "TP-Link wireless", and pick the threads that were easily solved with the latest kernel versions (3.8.0-19 or later).

An official list of "Supported devices" can be found here : [https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)
Direct link to supported TP-Link models : [https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsTP-Link#USB](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsTP-Link#USB)

Although I won't trust the above too much. Things keep changing and stuff breaks. By personal experience, I think anything supported by the native rt2800usb is easy to fix, if required. But then again, there may be others that don't need any fixing at all. :)

---

### Post by fs3 on 2013-09-24
Thanks again & had gt the thread marked solved.

---

