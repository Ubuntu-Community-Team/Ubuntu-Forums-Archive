---
title: "How to connect Netgear USB Dongle to Ubuntu"
date: 2015-06-09
forum: Networking &amp; Wireless
---

### Post by Ashish_Saxena on 2015-06-09
Hi All,

I have purchased a Netgear AC327U USB Dongle and I am running on Ubuntu 14.04.01. But my neither my Dongle is being detected nor I am able to connect to network (dongle network). Under Network Manager-->Edit connections I created new mobile broadband connection and gave properties but still not able to connect.

Please help.

Regards
Ashish Saxena

---

### Post by Bucky Ball on 2015-06-09
Welcome. Nothing much is going to happen unless you have a driver installed. Many USB dongles will work 'out of the box' with the drivers already available in the Linux kernel and best to stick with those devices. Others need a little persuading and a very few (generally released on the market ten minutes ago!) don't work at all ... yet.

Is this a very new device, as in, released not long ago?

Anyways, with the dongle in, open a terminal and copy/paste these two commands, one after the other and hitting enter after each:

```
sudo lshw -C network
```

Copy/paste the output back here between code tags (see last link in my signature). That should get the ball rolling. :)

PS: When the dongle is working, you will be notified that there are wireless networks available. You choose yours, are asked for the security key, input it and Network Manager is taken care of 'automagically'. It creates its own entry (and won't use yours) which you can then tweak however you like (for instance set a static IP address instead of DHCP, or 'automatic'). 

If it were me, I'd get rid of the entry you have created in NM. May just confuse the issue.

---

### Post by Ashish_Saxena on 2015-06-16
Hi,

Here is the output of the cmd:

```

 *-network               
       description: Wireless interface
       product: Centrino Wireless-N 1030 [Rainbow Peak]
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: wlan0
       version: 34
       serial: ac:72:89:20:ce:4d
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=3.16.0-38-generic firmware=18.168.6.1 ip=192.168.6.161 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:49 memory:d1600000-d1601fff
  *-network
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 06
       serial: 14:fe:b5:bb:3a:7e
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl_nic/rtl8168e-2.fw ip=192.168.6.84 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:45 ioport:3000(size=256) memory:d0404000-d0404fff memory:d0400000-d0403fff


```

---

### Post by chili555 on 2015-06-16
Why did you get a USB wireless when you have a working internal device? Is it not working as expected?> description: Wireless interface
       product: Centrino Wireless-N 1030 [Rainbow Peak]
       vendor: Intel Corporation
       logical name: wlan0
       configuration: broadcast=yes driver=iwlwifi driverversion=3.16.0-38-generic firmware=18.168.6.1 [COLOR="#FF0000"]ip=192.168.6.161[/COLOR] latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:49 memory:d1600000-d1601fff]

---

### Post by Ashish_Saxena on 2015-06-18
Hi,

I ordered this Netgear for using it as Dongle or data card, I am having a telecom operator SIM in it and trying to connect to 3G.

Regards
Ashish Saxena

---

### Post by chili555 on 2015-06-18
Let's see if we can get more information about your 3G dongle. With the device inserted, please run and post:```
lsusb
```Thanks.

---

### Post by Ashish_Saxena on 2015-06-22
Hi,

PFB the output of lsusb:

```

Bus 002 Device 005: ID 2077:a003  
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 003: ID 04ca:0061 Lite-On Technology Corp. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 005: ID 1bcf:2b81 Sunplus Innovation Technology Inc. 
Bus 001 Device 004: ID 138a:0011 Validity Sensors, Inc. VFS5011 Fingerprint Reader
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

---

### Post by chili555 on 2015-06-22
> 2077:a003 I assume that is your device as a Google search describes a usb_modeswitch device Netgear AC327U. 

Here is a thread about the device: [https://forums.opensuse.org/showthread.php/502876-Netgear-AC327U-USB-mobile-broadband-issues/page2](https://forums.opensuse.org/showthread.php/502876-Netgear-AC327U-USB-mobile-broadband-issues/page2) 

In post #15, the poster reports that the device works with *sakis3g*. Next, here is a post about getting *sakis3g* working: [http://ubuntuforums.org/showthread.php?t=2238362](http://ubuntuforums.org/showthread.php?t=2238362) It is a bit abbreviated, so I am going to try to explain it more thoroughly.

DISCLAIMER: I know little about 3g modems, so this is a learning experince for us both. 

First, download the sakis3g script: [http://raspberry-at-home.com/files/sakis3g.tar.gz](http://raspberry-at-home.com/files/sakis3g.tar.gz) Drag and drop it to your desktop so we can find it. Right-click it and select 'Extract Here.' Now, in a terminal:```

 sudo chmod 755 ~/Desktop/sakis3g  
 sudo cp ~/Desktop/sakis3g  usr/bin/  
 sudo sakis3g
```A window will pop-up.

Click the 'Connect with 3G'
Click the 'USB device'
Click the 'USB receiver' [COLOR="#FF0000"]<--??[/COLOR]
Next, I'd suggest you experiment, starting with interface #0.

It will say “Preparing modem...”

Then... 


Click 'Reported by your modem (wap)'
A window will appear asking you to type in your APN username. Proceed to type in *anything you like*

The window might reappear, type in *anything you like* again.
According to the Sakis3G rules, you can type anything you like in the APN box, if your modem doesn't use an apn.


Hopefully, it will show the “Connected to the internet” message!

All this is pretty experimental. We look forward to your report.

---

