---
title: "issue with d-link wua2340"
date: 2007-09-20
forum: Networking &amp; Wireless
---

### Post by gspat on 2007-09-20
Hi!!

This is my first post, but I've lurked here trying to learn as much as I can without asking too many stupid questions...

I have  ad-link wua2340 wireless usb dongle that I'm trying to get running, but not having too much luck with...

I've installed the latest ndiswrapper 1.48 (it seems there is no native driver) and followed the steps to get this dongle working... but no go...

using ndiswrapper -l I get the following...

```
neta5agu : driver installed
        device (07D1:3A08) present
```

and doing a lsusb gives me the following:

```
Bus 001 Device 002: ID 07d1:3a08 D-Link System 
Bus 001 Device 001: ID 0000:0000  
```

so it seems to me that the system sees the dongle and the appropriate driver is installed for it, but it does not light up and start flashing.

I went to the d-link site and downloaded the latest drivers (ver 101) 

Should I be getting a response back after the commands sudo depmod -a or sudo modprobe ndiswrapper? It just returns me to the command prompt.

the system I'm trying to use is as follows:

P3 800 Mhz
256 ram
ubuntu feisty (all updates to present) 7.04

any ideas? If I haven't included enough information, please just ask!!

---

### Post by Jeremy Jackins on 2007-09-28
I had the same thing, mine didn't work until I added ndiswrapper to /etc/modules and rebooted.

---

### Post by gspat on 2007-09-28
hmm...

multiple reboots later, the machine will not boot if I have the dongle connected and it will lock up if I connect it after start up...

it is in /etc/modules...

this whole lockup thing has always happened, but not booting with it connected has only started since I tried setting up the wireless connection when it "almost" started to work...

---

