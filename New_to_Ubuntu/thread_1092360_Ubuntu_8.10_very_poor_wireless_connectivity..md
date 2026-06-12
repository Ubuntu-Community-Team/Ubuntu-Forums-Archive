---
title: "Ubuntu 8.10 very poor wireless connectivity."
date: 2009-03-10
forum: New to Ubuntu
---

### Post by Gp. on 2009-03-10
I'm using Ubuntu 8.10 on my laptop and one of the other home Pc's.

Both use wireless.

Under windows the reception is excellent and works great, but under Ubuntu it's only a single bar and it's very slow.

Help?

---

### Post by Nxion on 2009-03-10
> **Gp. said:**
> I'm using Ubuntu 8.10 on my laptop and one of the other home Pc's.

Both use wireless.

Under windows the reception is excellent and works great, but under Ubuntu it's only a single bar and it's very slow.

Help?


So on your desktop and laptop, do they both use the same brand of wireless? To find out open a terminal and type this. Please post the output.

```
sudo lspci
```

```
sudo lshw -C network
```

---

### Post by Gp. on 2009-03-10
The desktop uses Wireless G and the laptop Wireless N.
My router is wireless N.

---

### Post by Nxion on 2009-03-11
> **Gp. said:**
> The desktop uses Wireless G and the laptop Wireless N.
My router is wireless N.

Can you post the output of the commands I had in th last post, that will give us a detailed output so maybe we can get a specific driver for it. Also just so you know that as of now, you wont get N speeds in Linux. G is the fastest right now. I don't believe that they will be adding N capabilities till it is finalized and not in draft form anymore.

---

### Post by Gp. on 2009-03-12
Do you know when 802.11 N will be final?

and I'll get back to you on that message.

---

### Post by Nxion on 2009-03-12
[http://en.wikipedia.org/wiki/IEEE_802.11n](http://en.wikipedia.org/wiki/IEEE_802.11n)

---

### Post by Gp. on 2009-03-13
Here is what the command responded with:

```
00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation 82G33/G31/P35/P31 Express PCI Express Root Port (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 02)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 02)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 92)
00:1f.0 ISA bridge: Intel Corporation 82801IR (ICH9R) LPC Interface Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801IR/IO/IH (ICH9R/DO/DH) 4 port SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 02)
00:1f.5 IDE interface: Intel Corporation 82801I (ICH9 Family) 2 port SATA IDE Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8500 GT (rev a1)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8056 PCI-E Gigabit Ethernet Controller (rev 12)
03:00.0 SATA controller: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 03)
03:00.1 IDE interface: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 03)
05:03.0 FireWire (IEEE 1394): Agere Systems FW323 (rev 70)
05:04.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8110SC/8169SC Gigabit Ethernet (rev 10)
```

and

```
 *-network               
       description: Ethernet interface
       product: 88E8056 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 12
       serial: 00:1b:fc:c1:cb:22
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.22 firmware=N/A latency=0 link=no module=sky2 multicast=yes port=twisted pair
  *-network
       description: Ethernet interface
       product: RTL-8110SC/8169SC Gigabit Ethernet
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 4
       bus info: pci@0000:05:04.0
       logical name: eth1
       version: 10
       serial: 00:1b:fc:c1:c3:bd
       size: 10MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=64 link=no maxlatency=64 mingnt=32 module=r8169 multicast=yes port=twisted pair speed=10MB/s
  *-network:0
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:15:af:1a:34:b0
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.0.197 multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 4a:74:94:f5:b1:90
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
```

---

### Post by Gp. on 2009-03-15
Bump.

What now?

---

### Post by Nxion on 2009-03-17
Have you tried changing the channel on  the router? Also make sure that you have selected Wireless G only.  If you have it setup in the router to use A/G/N then you can run into issues. This was the same in my case. I had A/G/N wireless running on my router and all my wireless clients where having issues connecting.

---

### Post by Gp. on 2009-03-23
I changed it to wireless G only, and it's still the exactly same quality. Terrible.

What else can I try?

---

### Post by 3rdalbum on 2009-03-23
What you've posted has not actually told us the necessary information: What the model of your wireless device is. (Not your fault)

Looks like your device is connected through USB, even if it is sitting on your motherboard. Could you please give us the output of this command:

```
lsusb
```

I can guess what wireless card you have, from your description of your problem. But I need to know for sure. Of course, once you know what chipset your card uses, you could always go searching for a HOWTO or a workaround on your own; it could be quicker than waiting for someone here to reply.

---

### Post by Gp. on 2009-03-23
```
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 0bda:8187 Realtek Semiconductor Corp. RTL8187 Wireless Adapter
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 002: ID 045e:0084 Microsoft Corp. Basic Optical Mouse
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```


That's the output.

---

### Post by 3rdalbum on 2009-03-23
Hahahaha yes that was the wireless adapter I was going to guess :-)

The slow speed and low signal quality is a known problem in the kernel. The bad news is that it hasn't been fixed upstream (in the kernel). The good news is that there is a replacement driver that works really well.

Check out this web page for details on how to install it:

[http://zenzike.blogspot.com/2008/11/wireless-woes.html]("http://zenzike.blogspot.com/2008/11/wireless-woes.html")

Note that the driver doesn't support WPA encryption, only WEP; and you will need to run the "sudo make clean", "sudo make" and "sudo make install" commands after each time you upgrade your kernel. Make sure you tell your router to work with WEP otherwise your network will not appear in Network Manager.

Alternatively, ndiswrapper is said to work "with WPA and everything" but I haven't tried it.

---

### Post by Gp. on 2009-03-23
Will it be fixed with the next ubuntu release?

and I need it to work for WPA.

You got a link for ndiswrapper stuff?

Thanks for the help btw.

---

