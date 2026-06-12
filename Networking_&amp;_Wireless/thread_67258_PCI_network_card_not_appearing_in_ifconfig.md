---
title: "PCI network card not appearing in ifconfig"
date: 2005-09-19
forum: Networking &amp; Wireless
---

### Post by markeq on 2005-09-19
Hi

The integrated NIC is find and appears in the System/Administration/Networking dialog box. The PCI card, D-Link DE-528 (Realtek 8029 chipset) does not. The lspci -v out put is as follows

[FONT=Courier New]0000:02:04.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8029(AS)
	Subsystem: D-Link System Inc DE-528
	Flags: medium devsel, IRQ 16
	I/O ports at 1040 [size=32]

0000:02:08.0 Ethernet controller: Intel Corp. 82801BA/BAM/CA/CAM Ethernet Controller (rev 01)
	Subsystem: Compaq Computer Corporation EtherExpress PRO/100 VM
	Flags: bus master, medium devsel, latency 66, IRQ 20
	Memory at 40000000 (32-bit, non-prefetchable) [size=4K]
	I/O ports at 1000 [size=64]
	Capabilities: <available only to root>[/FONT]

The ifconfig -a output is as follows:
[FONT=Courier New]
eth0      Link encap:Ethernet  HWaddr 00:02:A5:1F:9B:AE  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:16696 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16696 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1260691 (1.2 MiB)  TX bytes:1260691 (1.2 MiB)

sit0      Link encap:IPv6-in-IPv4  
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)[/FONT]

As you can see the eth0 interface is there. How do I get the DLink PCI ethernet card to appear as eth1? What have I missed?

Cheers, Mark

---

### Post by mlomker on 2005-09-19
> As you can see the eth0 interface is there. How do I get the DLink PCI ethernet card to appear as eth1? What have I missed?

Apparently that is an NE2000 clone.

Check if the driver is loaded:

```

lsmod | grep ne2

```

If nothing:

```

sudo modprobe ne2k-pci

```

In either case, post the output of:

```

dmesg | grep ne2k

```

---

### Post by markeq on 2005-09-20
Hi

Thanks for looking at this.

Here's the output from dmesg | grep ne2
[SIZE=2][FONT=Courier New]ne2k-pci.c:v1.03 9/22/2003 D. Becker/P. Gortmaker
  [http://www.scyld.com/network/ne2k-pci.html](http://www.scyld.com/network/ne2k-pci.html)
ne2k-pci.c:v1.03 9/22/2003 D. Becker/P. Gortmaker
  [http://www.scyld.com/network/ne2k-pci.html](http://www.scyld.com/network/ne2k-pci.html)[/FONT][/SIZE]

It shows twice, once for boot up and once because I did a sudo modprobe as you suggested.

Here's what lsmod | grep ne2 gives
[SIZE=2][FONT=Courier New]ne2k_pci               10080  0 
8390                    9984  1 ne2k_pci[/FONT][/SIZE]

So as far as I can see the drivers are installing just fine. Yet I still can't see it in System/Administration/Networking

I'm trying to install a second Ethernet card, the onboard Ethernet (Intel EtherExpress 100) works fine and shows up in System/Administration/Networking as eth0. The machine is a Compaq Deskpro EN PIII 800 Mhz SFF.

Cheers, Mark

---

### Post by mlomker on 2005-09-20
> 
So as far as I can see the drivers are installing just fine. Yet I still can't see it in System/Administration/Networking


Yup, but usually if it finds a card it'll come back and tell you what port number was assigned to it.

```

dmesg | grep eth

```

Try just bringing it up manually...it should be eth1 if it's the second card.

```

sudo ifconfig eth1 up

```

---

### Post by markeq on 2005-09-24
Thanks for your help on this. Turns out that the network card has a hardware fault, and is only good for the dustbin.

Grrrr.

Regards, Mark

---

