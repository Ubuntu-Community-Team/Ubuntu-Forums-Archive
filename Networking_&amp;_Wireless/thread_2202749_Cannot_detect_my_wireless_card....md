---
title: "Cannot detect my wireless card..."
date: 2014-01-30
forum: Networking &amp; Wireless
---

### Post by Kaiser2k on 2014-01-30
Hello, I'm using Windows 7 and running BackTrack 5 R3 with VMWare. Today I bought a usb adapter model TL-WN8200ND and I was trying all day to find the chipset of the device but in vain... Every time I run BackTrack the usb device turns off with the result cannot detect it
I tried
```
root@bt:~# airmon-ng

Interface    Chipset    Driver
```
```
root@bt:~# airmon-ng start wlan0

Found 3 processes that could cause trouble.
If airodump-ng, aireplay-ng or airtun-ng stops working after
a short period of time, you may want to kill (some of) them!

PID     Name
886     dhclient3
1455    dhclient
1488    dhclient

Interface    Chipset    Driver

```
```
root@bt:~# wicd
```
```
root@bt:~# iwconfig
lo       no wireless extensions

eth0     no wireless extensions
```
```
root@bt:~# lsusb
Bus 002 Device 004: ID 0e0f:0008 VWare, Inc.
Bus 002 Device 003: ID 0e0f:0002 VWare, Inc. Virtual USB Hub
Bus 002 Device 002: ID 0e0f:0003 VWare, Inc. Virtual Mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 2357:0100
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```
```
root@bt:~# usb_modeswitch -v 2357 -p 0100


Looking for default devices ...
 Found devices in default mode or class (1)
Accessing device 002 on bus 001 ...
Using endpoints 0x02 (out) and 0x81 (in)
Not a storage device, skipping SCSI inquiry


USB description data (for identification)
-------------------------
Manufacturer: realtek
     Product: 802.11n WLAN Adapter
  Serial No.: 00e04c000001
-------------------------
Warning: no switching method given.
-> Run lsusb to note any changes. Bye.

```
Also, tried this but wicd and wicd-daemon are ok
```
root@bt:~# apt-get install synaptic
```
Tried networking, wicd stop and start. I don't remember what else...
On Wicd Network Manager says "No wireless networks found." but at the bottom says "Connected to wired network (IP: ...) and I can connect to the internet.
On the options my adapter is selected and right now I'm running BT and it is disabled. I think that I need compatible drivers..... What can I do????? Please help :cry::cry:

---

### Post by tfrue on 2014-01-31
I don't know so much about VMware, but I know in Oracle Vitrual Box you couldn't do wireless and the reason you are getting internet is because you are doing a virtual bridged connection between your virtual machine and your host machines NIC. That's also why you cannot have wireless. I've never been able to set up wireless and I've read either in the Oracle VM info pages about no wireless, or somewhere but I would say that your best bet would be to dual boot or live boot when you want to do pen test and network audits.

---

### Post by Kaiser2k on 2014-01-31
> **tfrue said:**
> I don't know so much about VMware, but I know in Oracle Vitrual Box you couldn't do wireless and the reason you are getting internet is because you are doing a virtual bridged connection between your virtual machine and your host machines NIC. That's also why you cannot have wireless. I've never been able to set up wireless and I've read either in the Oracle VM info pages about no wireless, or somewhere but I would say that your best bet would be to dual boot or live boot when you want to do pen test and network audits.
I have both VMware and Virtual Box. Basically, I want my "airmon-ng" to detect my interface. So if I try live boot could solve my problem? Why every time I run VMware or Virtual box disables my device?

---

### Post by tfrue on 2014-01-31
Go to this site and read the fourth post, it may help you. But I've never set up wireless in virtual box but you may be able to. Live booting will utilize your actual hardware rather than being virtualized on the hardware. You should have better performance since you can dedicate all of your CPU, RAM, HDD and anything to running that live boot rather than shared RAM, CPU and other hardware while in the VM.

Chris

EDIT:

Forgot to add the link to the site, here it is

[https://forums.virtualbox.org/viewtopic.php?f=8&t=19305](https://forums.virtualbox.org/viewtopic.php?f=8&t=19305)

---

### Post by Kaiser2k on 2014-01-31
> **tfrue said:**
> Go to this site and read the fourth post, it may help you. But I've never set up wireless in virtual box but you may be able to. Live booting will utilize your actual hardware rather than being virtualized on the hardware. You should have better performance since you can dedicate all of your CPU, RAM, HDD and anything to running that live boot rather than shared RAM, CPU and other hardware while in the VM.

Chris

EDIT:

Forgot to add the link to the site, here it is

[https://forums.virtualbox.org/viewtopic.php?f=8&t=19305](https://forums.virtualbox.org/viewtopic.php?f=8&t=19305)
Unfortunately, that didn't help. Already did that lots of times. I want my adapter to find all wifi routers around but when I run Virtual box, stops working, it turns off like it's unplugged. Virtual box disables the adapter and if I disconnect it from Virtual box it works fine. I'm disappointed :( :( :cry:

---

### Post by oldos2er on 2014-01-31
We don't support Backtrack here, I suggest you use the [Backtrack forums]("http://www.backtrack-linux.org/forums/forum.php") instead.

Closed.

---

