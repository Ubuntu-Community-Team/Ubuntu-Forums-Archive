---
title: "Attansic ATL1 Problem"
date: 2007-07-11
forum: Networking &amp; Wireless
---

### Post by justin.fyfe1 on 2007-07-11
Hello, 

I am having a very odd problem with my Attansic L1 ethernet driver. I don't think it is specific to the driver, perhaps just a configuration issue that I can't figure out.

Here is the interesting bit. After installing, I rebooted, and ran ifconfig however only the lo interface appears. I did a quick check of the kernel messages which contained:
ACPI: PCI interrupt for device 0000:04:00.0 disabled
atl1: module license 'ATTANSIC' taints kernel.
Attansic(R) L1 Ethernet Network Driver - version 2.0.6
Copyright(c) 2005-2006 Attansic Corporation
ACPI: PCI Interrupt 0000:04:00.0[A] -> GSI 36 (level, low) -> IRQ 36
PCI: Setting latency timer of device 0000:04:00.0 to 64

Very odd... The driver appeared, however there was no eth0 device. So, I added this to /etc/modprobe.d/aliases

alias eth0 atl1

Still no results. 

I am stuck for answers. Any help would be greatly appreciated.
-Justin

---

### Post by aleb on 2007-11-13
Hi, It seems you were using the vendor version of the driver. There is a newer version which works (better it seems). 

The [http://www.hogchain.net/attansic/attansic.html](http://www.hogchain.net/attansic/attansic.html) page provides some more info but it does not currently contain the latest version of the driver. For the latest you have to download the latest (stable?) kernel (2.6.23.1) from kernel.org, and copy the driver from there.

If you use 4G or more RAM and are using the default driver that comes with ubuntu gutsy, you have to specify a mem=3900m kernel boot parameter, otherwise the system will freeze when the network is under heavy load (sooner or later). Another solution is use a newer (for example 2.6.23.1) kernel or recompile your current kernel with the newest drivers (copied from a newer kernel).

So if you just installed a 64 bit system so that you can use all the 4G RAM, only to find that the network chipset of the motherboard (for example Asus P5K) has problems with the higher memory addresses and now you have to limit the usable memory yourself to make it work without crashes, read on.. :)

[SIZE="3"]Some more details for whoever is interested (read: has more than 4G RAM and a 64 bit operating system):[/SIZE]

apt-get the sources of the 2.6.22-14 ubuntu kernel running on your system, copy the /drivers/net/atl1 folder from the newer 2.6.23.1 kernel version to yours. The idea is to build the atl1 driver by rebuilding the 2.6.22-14 kernel sources. (I found no way to recompile just a specific driver, maybe it is possible though)
Read about [recompiling the kernel]("https://help.ubuntu.com/community/Kernel/Compile") (sudo make oldconfig; sudo make modules) and after the thing compiles, copy the new atl1.ko file to /lib/modules/2.6.22-14-generic/kernel/drivers/net/atl1 (you can make a backup copy just in case :) ):

Have a look at the man page of modprobe. Remove the old driver from the kernel:

$ sudo modprobe -r atl1
$ sudo modprobe -r atl1
$ sudo modprobe -r atl1
$ sudo modprobe -r atl1

..4 times, to make it a bit misterious.
Now check your network connection, it should be dead.

$ ping -c 4 google.com

I'm not sure running depmod is really necessary, but I think it will not hurt (the system):

$ sudo depmod -a

Install the new driver:

$ sudo modprobe -v atl1

Finally, restart your network connection:

$ sudo /etc/init.d/networking restart

In theory, you don't even have to reboot. Amazing.

To test the thing, you can scp (a few times) a 13G file from your LAN (Gbit, right?) to the altered system. Note: this test works better if you copy the file to the harddisk, not to /dev/null, so that the used memory will slowly increase and then at some point, in case of the current gutsy driver, the system will crash. :)

Good luck, I hope this works for you too!

---

### Post by SpaceBas on 2008-02-03
Hey Folks,
I've been trying to get this Attansic L1 working with a fresh install of 7.10 Server (32-bit).
The driver seems to be loaded, and the system actually almost recognizes the thing, but it will not acquire and address (or respond to a static address should I set one)

I have tried to compile the driver on the disk supplied from asus but it fails every time (probably due to higher version of the kernel). Hogchain's FTP server appears to be down, so I cannot grab the standalone ATl1 module from them. I did try the current version on sourceforge which also fails to compile. 

It seems like others have gotten this NIC to work, so I'm hoping there may be some insight that will help me. 

I've pasted the results of my troubleshooting below.
 


dmesg | grep atl1

```
[62791.857188] atl1 0000:01:00.0: eth1 link is up 1000 Mbps full duplex
```


dmesg | grep eth1
```
[62357.145755] atl1 0000:01:00.0: eth1 link is up 100 Mbps full duplex
[62357.146969] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[62367.856179] eth1: no IPv6 routers present
[62406.767520] atl1 0000:01:00.0: eth1 link is down
[62791.857188] atl1 0000:01:00.0: eth1 link is up 1000 Mbps full duplex
```

mii-diag eth1
```
Basic registers of MII PHY #0:  1000 796d 004d d015 0de1 cde1 000d 2801.
 The autonegotiated capability is 01e0.
The autonegotiated media type is 100baseTx-FD.
 Basic mode control register 0x1000: Auto-negotiation enabled.
 You have link beat, and everything is working OK.
 Your link partner advertised cde1: Flow-control 100baseTx-FD 100baseTx 10baseT-FD 10baseT, w/ 802.3X flow control.
   End of basic transceiver information.
```

ifconfig
```
eth1      Link encap:Ethernet  HWaddr 00:1E:8C:91:8A:27  
          inet6 addr: fe80::21e:8cff:fe91:8a27/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:10902 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20 errors:0 dropped:0 overruns:0 carrier:3
          collisions:0 txqueuelen:1000 
          RX bytes:843606 (823.8 KB)  TX bytes:1308 (1.2 KB)
```

---

### Post by aleb on 2008-02-05
> **SpaceBas said:**
> I have tried to compile the driver on the disk supplied from asus but it fails every time (probably due to higher version of the kernel). Hogchain's FTP server appears to be down, so I cannot grab the standalone ATl1 module from them. I did try the current version on sourceforge which also fails to compile. 

Try downloading the latest linux kernel, it should have a newer driver in /drivers/net/atl1
I was just prompted for a kernel upgrade, you may want to try this upgrade before, maybe it fixes the problem.

---

### Post by niceguyeddie on 2008-03-01
Hey aleb,

I attempting to do what you stated here... to compile the atl1 module from the latest linux-source.  I went into that directory and ran "make" but it's saying no target.  Do you know how to compile just this module from the kernel source code?

To give you the history of my problem, I made the mistake of compiling the driver from ASUS's website.  I think it wiped the existing (working) module from my system (64 bit 7.1 Ubuntu) and I'm just trying to revert back.  LMK....

Thank you!
nge

---

### Post by aleb on 2008-03-02
> **niceguyeddie said:**
> Hey aleb,

I attempting to do what you stated here... to compile the atl1 module from the latest linux-source.  I went into that directory and ran "make" but it's saying no target.  Do you know how to compile just this module from the kernel source code?

To give you the history of my problem, I made the mistake of compiling the driver from ASUS's website.  I think it wiped the existing (working) module from my system (64 bit 7.1 Ubuntu) and I'm just trying to revert back.  LMK....

Thank you!
nge

I used this:
make modules --jobs=2

Did you run "make oldconfig" before running make?

One problem with some very recent version of the driver (from the 2.6.24 kernel) is that it's not 100% compatible with the current 2.6.22-14.52 version used by Gutsy 64. But the atl1 changes between 2.6.23 and 2.6.24 are minor, meaning you can revert them easily (if you want to have the latest and cleanest version of the code). I think it would be simpler to use the atl1 version from the 2.6.23 kernel..

I don't remember trying the driver from ASUS, I am not aware of its existence. Remember to make copies of the files before overwriting them... :)

hth!

EDIT: I attached the version I am using (after "fixing" the 2.6.24 driver)

---

