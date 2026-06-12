---
title: "lspci shows nothing"
date: 2007-01-03
forum: Networking &amp; Wireless
---

### Post by dibblego on 2007-01-03
I am struggling to get either of my PCI wireless NICs to configure. I have spent countless hours googling trying to find a solution to no avail. The reason, it seems, is that all avenues seem to make the assumption that the wireless NIC is listed - somehow - with lspci. I see nothing with either card when I use lspci.

The two cards are:
* NETGEAR WG511T Rev: A3
* DLink DWL-G510 H/W Ver: C2 F/W Ver: 5.00

Here are some of the things I have tried in a desperate attempt to make progress:
* boot into Dapper 6.06.1 with the CD (I am currently running edgy)
* swapped the cards in the PCI slots (I have two)
* fiddle with ndiswrapper (despite seeing nothing in lspci)

It should be noted that the wireless NIC has an active power light when the machine is booted.

I am truly exhausted in trying to figure this problem out and I appreciate any thoughts of any kind at all. If I can just get the card to list in lspci I could probably make my own progress. I only need one of these cards to work - whichever one I do not care so much, but it seems I cannot even take the first step that so many paths seem to assume are a given.

> 
$ lspci
00:00.0 Host bridge: Intel Corporation 915G/P/GV/GL/PL/910GL Express Memory Controller Hub (rev 04)
00:01.0 PCI bridge: Intel Corporation 915G/P/GV/GL/PL/910GL Express PCI Express Root Port (rev 04)
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 4 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d3)
00:1f.0 ISA bridge: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801FB/FW (ICH6/ICH6W) SATA Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation NV37GL [Quadro FX 330/GeForce PCX 5300] (rev a2)
06:08.0 Ethernet controller: Intel Corporation 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller (rev 01)
$ uname -a
Linux vtr 2.6.17-10-generic #2 SMP Tue Dec 5 22:28:26 UTC 2006 i686 GNU/Linux
</pre>


---

### Post by mojoman on 2007-01-03
The active power light is, I think, at least one positive sign. What is the output of: ```
ifconfig
``` and ```
ifconfig -a
```

---

### Post by dibblego on 2007-01-03
Thanks for the response. Here is the output:
> 
$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:13:20:50:BA:6F
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:476 (476.0 b)  TX bytes:476 (476.0 b)

rausb0    Link encap:Ethernet  HWaddr 00:11:D8:01:80:53
          inet addr:192.168.1.130  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::211:d8ff:fe01:8053/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7123 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7424 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:38210141 (36.4 MiB)  TX bytes:1517754 (1.4 MiB)

vmnet1    Link encap:Ethernet  HWaddr 00:50:56:C0:00:01
          inet addr:192.168.86.1  Bcast:192.168.86.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

vmnet8    Link encap:Ethernet  HWaddr 00:50:56:C0:00:08
          inet addr:172.16.171.1  Bcast:172.16.171.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:13:20:50:BA:6F
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:476 (476.0 b)  TX bytes:476 (476.0 b)

rausb0    Link encap:Ethernet  HWaddr 00:11:D8:01:80:53
          inet addr:192.168.1.130  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::211:d8ff:fe01:8053/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7155 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7443 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:38220295 (36.4 MiB)  TX bytes:1523790 (1.4 MiB)

sit0      Link encap:IPv6-in-IPv4
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

vmnet1    Link encap:Ethernet  HWaddr 00:50:56:C0:00:01
          inet addr:192.168.86.1  Bcast:192.168.86.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

vmnet8    Link encap:Ethernet  HWaddr 00:50:56:C0:00:08
          inet addr:172.16.171.1  Bcast:172.16.171.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)


---

### Post by mojoman on 2007-01-04
Hmm, ok. I *think* that the device we should be looking at is rausb0 but I'm not sure. Normally, a wireless connection shows up as ra0 (or ra1, ra2 etc if you have several). Anyway, you said it was a card so it isn't connected via USB, right? Otherwise, rausb0 sounds like a wireless hooked up through usb...

Anyway, I managed to find a howto for the Netgear card. As I don't have this card myself I haven't tried it out and aren't familiar with all the steps in it but try it out.

[http://ubuntuforums.org/showthread.php?t=76804](http://ubuntuforums.org/showthread.php?t=76804)

Also, check here for the hardware compability list for Ubuntu and Netgear:

[https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsNetgear](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsNetgear)

As for the D-Link, there is a list for those cards as well:

[https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsDlink](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsDlink)

The D-link should work out-of-the-box, or so they claim.

That leaves you with to options. You could try the Netgear howto or you could try to bring up the D-link using the drivers in native to Ubuntu. Personally, I'd try the D-link first, given that it *should* be simpler. 

For the D-link, I'd plug it in and disconnect the other and then boot up. Then I'd run ```
ifconfig -a
``` just to check what it's connected as (ra0, rausb0 or whatever) and then just try to bring it up with ```
sudo ifconfig ra0 up
``` (or "sudo ifconfig rausb0 up" depending on what it shows up as).

If that doesn't work, there are some more things we can try out on the D-link as well but hey, this might be enough. :rolleyes: 

BTW, are both cards lit up? And were both cards connected when you ran ifconfig?

/Mojoman

---

### Post by dibblego on 2007-01-04
Sorry, I should have mentioned that I have another WLAN card plugged into a USB port - which is the one that is showing up as rausb0. Both my NETGEAR and DLink cards are PCI cards.

Since I am not at home, I cannot try those things that you mention, so I will try ASAP. However, I suspect that I will see nothing additional, because I have already tried it.

Yep, both cards are lit up when I connect them.

Thanks again for the help so far.

---

