---
title: "Still can't connect to internet (anybody??)"
date: 2008-12-11
forum: New to Ubuntu
---

### Post by tegnoto89 on 2008-12-11
I recently downloaded wicd because the default ubuntu and kubuntu network managers kept kicking me off and taking multiple attempts to reconnect.

But now with wicd I can't connect at all! The slower connection designed for PDA's works, but the one with encryption required does not.

This is what the university gives me in terms of requirements:

* WPA-1 protocol (WPA).
* TKIP session encryption.
* PEAP authentication type.
* MSCHAPv2 password encryption.
* AuthServers secure1.syr.edu;secure2.syr.edu;

These settings are NOT required for AirOrangeX and can be ignored:

* Anonymous Identity
* Client Certificate File
* CA Certificate File
* Private Key File
* Private Key Password

I've tried many different setups under advanced controls for the connection (I don't have a CA cert though). Any advice? I've been posting this in the beginner forum and nobody has helped me. Here's all the information:

lspci:

Code:

00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 0c)
00:19.0 Ethernet controller: Intel Corporation 82566MM Gigabit Network Connection (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HBM (ICH8M-E) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation Quadro NVS 140M (rev a1)
02:00.0 Memory controller: Intel Corporation Turbo Memory Controller (rev 01)
03:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)
15:00.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev ba)
15:00.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 04)
15:00.2 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 21)
15:00.3 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev ff)
15:00.4 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 11)
15:00.5 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 11)

lsusb:

Code:

Bus 007 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 0483:2016 SGS Thomson Microelectronics Fingerprint Reader
Bus 001 Device 003: ID 0a5c:2110 Broadcom Corp. Bluetooth Controller
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

---

### Post by tegnoto89 on 2008-12-12
i'll paypal a dollar to anyone who can fix this

---

### Post by jay li on 2008-12-12
Is there any chance that you problem with wifi adaptor?

---

### Post by anubhavrocks on 2008-12-12
I do not have any idea about wicd.But what version of ubuntu were you using?

---

### Post by Peter09 on 2008-12-12
Can you post the output of

```
lshw -C network
```

and

```
ifconfig
```

---

### Post by anubhavrocks on 2008-12-12
Also try the latest firmware:

```
http://www.intellinuxwireless.org/iwlwifi/downloads/iwlwifi-4965-ucode-228.57.2.23.tgz
```

You will have to extract the firmware and place it in
```
/lib/firmware/`uname -r`
```

---

### Post by tegnoto89 on 2008-12-12
lshw -C network:

```
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 82566MM Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 03
       serial: 00:1a:6b:38:aa:48
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e1000e driverversion=0.3.3.3-k6 firmware=0.3-0 latency=0 module=e1000e multicast=yes
  *-network
       description: Wireless interface
       product: PRO/Wireless 4965 AG or AGN [Kedron] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wmaster0
       version: 61
       serial: 00:13:e8:76:8f:7f
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn ip=128.230.193.97 latency=0 module=iwlagn multicast=yes wireless=IEEE 802.11abgn
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 72:3c:53:ab:10:62
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

```

ifconfig:

```
eth0      Link encap:Ethernet  HWaddr 00:1a:6b:38:aa:48  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Memory:fe200000-fe220000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 B)  TX bytes:100 (100.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:13:e8:76:8f:7f  
          inet addr:128.230.193.97  Bcast:128.230.199.255  Mask:255.255.248.0
          inet6 addr: fe80::213:e8ff:fe76:8f7f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:25273 errors:0 dropped:0 overruns:0 frame:0
          TX packets:25752 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:28302140 (28.3 MB)  TX bytes:4269194 (4.2 MB)

wmaster0  Link encap:UNSPEC  HWaddr 00-13-E8-76-8F-7F-66-37-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

I'll try the firmware now.

---

### Post by weezerisrock on 2008-12-12
before you do that, it looks like you grabbed an IP address... can you ping google or anything?

At the risk of insulting your intelligence (which I promise I don't mean to do) open terminal and type
```
ping www.google.com
```

do you get a response?

---

### Post by Peter09 on 2008-12-12
Agree with Weezerisrock,
you've got an ip address and it looks like your machine is connected. I think we a presuming that you are getting your ip address from your wireless router, not a static ip address.

---

### Post by Peter09 on 2008-12-12
Note that if you get a cannot find host message try

```
ping 216.239.59.99
```

Thats googles ip address.

---

### Post by tegnoto89 on 2008-12-12
Yes, I do get a response.  It gives me "64 bytes from yo-in-f99.google.com..."

I should note that I'm connected to a network other than the one I'm trying to connect to for the sake of posting here to fix the one I need.

Please don't worry about insulting my intelligence; I really have no idea what I'm doing here :p

---

### Post by Peter09 on 2008-12-12
Right - so your wireless interface is working. 

Can you post the output of

```
route -n
```

---

### Post by tegnoto89 on 2008-12-12
route -n:

```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
128.230.192.0   0.0.0.0         255.255.248.0   U     0      0        0 wlan0
0.0.0.0         128.230.192.1   0.0.0.0         UG    0      0        0 wlan0

```

---

### Post by Peter09 on 2008-12-12
that looks ok, so what happens when you try to get to google through firefox?

---

### Post by ibuclaw on 2008-12-12
May I just chip in that I noticed that you are using an Intel Wireless 4965, they are one of the most beautifulest wireless cards out there. They perform like a dream on my HP DV2700 Laptops. :)

Secondly, can you connect to your router directly?
type in: **192.168.1.1** or **192.168.0.1** in your browser window.

You can ping google, so it can't be a DNS problem (though, you could try switching to opendns, just incase).

This is done by setting these as your default and alternative DNS servers:
208.67.222.222
208.67.220.220 


The only viable reason I can think of at the moment... May sound strange, but have you setup a firewall on Ubuntu ?
You may be blocking port 80, for some wild/bizarre reason. :)

Regards
Iain

---

### Post by tegnoto89 on 2008-12-12
Well with this connection I'm free to browse whatever.  With the other, wicd is telling me I'm not connected so I get the "page cannot be displayed" page.  I haven't actually set up a firewall with ubuntu..

I tried to directly connect to my router, and I got a "failed to connect" message.

---

### Post by Peter09 on 2008-12-12
If you cannot connect to your University network, but can to this one then its not really a hardware /driver problem.

When you try to connect to the Uni network do you get a request for a pass phrase or key. Is it the correct one?

---

### Post by tegnoto89 on 2008-12-12
Yes.  Well, with my old network manager I did.  With Wicd I have to selected "encryped network" (or something along those lines) and put in the information before I attempt to connect.  But the university network does require an ID and password

---

### Post by Peter09 on 2008-12-12
Yes, but the ID and password will be presented once you have made the wireless connection.

---

### Post by tegnoto89 on 2008-12-12
Okay, so what does that mean?

---

### Post by Peter09 on 2008-12-12
It means that it's most probably not your computer thats the problem.

---

### Post by tegnoto89 on 2008-12-12
That's annoying.  Could it be the fact that I don't have a CA cert or I'm using the wrong type of encryption?  It says to use PEAP with TKIP, but I put "none" in CA cert because I don't have one (to my knowledge).

---

### Post by Peter09 on 2008-12-12
Most probably, you'll need to talk to the University IT people.

---

