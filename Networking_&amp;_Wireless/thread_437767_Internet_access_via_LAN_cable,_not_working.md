---
title: "Internet access via LAN cable, not working"
date: 2007-05-09
forum: Networking &amp; Wireless
---

### Post by r_choitram on 2007-05-09
Hello,

Please advise.

FYI:
- I am unsure what is the first step to correct the Networking problem.

- UBUNTU 7.04 is installed on my laptop

- Connected a LAN cable from my router to access the Internet, and it does not work.

- Pings are only working to one address: 
>>ping -c 5 192.168.1.1

Best Regards,
-Raj Choitram

---

### Post by chili555 on 2007-05-09
How about:```
ping -c3 216.239.51.99
```May we please see the output of:```
cat /etc/resolv.conf
```Thanks.

---

### Post by r_choitram on 2007-05-09
Please advise further.

FYI:
- Thank you for replying.

- FYI: 
Wired is via my cable modem & router
Wireless is via my Toshiba Centrino laptop

- To answer your questions:

* ping -c3 216.239.51.99
- Wired: Unknown host
- Wireless: 3 packets transmitted, 0 received, 100% loss, time 1999ms

May we please see the output of:
Code:
* cat /etc/resolv.conf
- Wired: nameserver 192.168.2.1
- Wireless: No such file or directory

Thanks.

-Raj

---

### Post by chili555 on 2007-05-09
> - Wireless: No such file or directoryDon't quite understand this, there is only one /etc/resolv.conf file for wired, wireless, modem, whatever; it's /etc/resolv.conf.

I am also concerned that you said you can ping 192.168.1.1, which I assume is the IP address of your router. However, /etc/resolv.conf says the nameserver is 192.168.2.1.

Where does the laptop get its wireless signal?

Are you trying to connect both wired and wireless at the same time?

---

### Post by r_choitram on 2007-05-09
Please advise what to try next.

FYI:
- Let's keep it simple - WIRED connection first.

- ping -c3 216.239.51.99
>> 3 packets transmitted, 0 received, 100% loss, time 2010ms

- cat /etc/resolve.conf
>> nameserver 192.168.2.1

- Perhaps I confused things earlier.

-Raj

---

### Post by chili555 on 2007-05-09
> Perhaps I confused things earlierYes. And I'm no less confused now. I don't understand what you are trying to do. First of all, as you suggested, let's concentrate on wired.

As I asked before: I am also concerned that you said you can ping 192.168.1.1, which I assume is the IP address of your router. However, /etc/resolv.conf says the nameserver is 192.168.2.1. 

What is the IP address of your router? Can you get a gateway address from:```
route -n
``` If your router is 192.168.1.1 and /etc/resolv.conf tells the computer to look to resolve names to IP addresses at 192.168.2.1, you are sending it down a dead end.

What is the IP address of the router?

---

### Post by dbott67 on 2007-05-09
Just to add to chili's request, can you post the output of the following commands:
```
dbott@feisty:~$ **cat /etc/network/interfaces**
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp

``````
dbott@feisty:~$** ifconfig -a**
eth0      Link encap:Ethernet  HWaddr 00:E0:29:7C:65:3F
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::2e0:29ff:fe7c:653f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:732483 errors:0 dropped:0 overruns:0 frame:0
          TX packets:101659 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:352562729 (336.2 MiB)  TX bytes:6776681 (6.4 MiB)
          Interrupt:9 Base address:0x4c00

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:20 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1740 (1.6 KiB)  TX bytes:1740 (1.6 KiB)

sit0      Link encap:IPv6-in-IPv4
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

``````
dbott@feisty:~$ **iwlist scanning**
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

sit0      Interface doesn't support scanning.

``````
dbott@feisty:~$ **[COLOR=black]sudo lshw -C network[/COLOR]**
  *-network
       description: Ethernet interface
       product: SMC2-1211TX
       vendor: Accton Technology Corporation
       physical id: b
       bus info: pci@02:0b.0
       logical name: eth0
       version: 10
       serial: 00:e0:29:7c:65:3f
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
       configuration: autonegociation=on broadcast=yes driver=8139too driverversion=0.9.27 duplex=full ip=192.168.1.100 link=yes multicast=yes port=MII speed=100MB/s
       resources: ioport:d800-d8ff iomemory:feafbc00-feafbcff irq:9

``````
dbott@feisty:~$ **route -n**
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0


```*Note: if you can't get online with your system & you have a USB thumb drive (or floppy or some other removable media you can write to) you can use the 'redirect' function to write the output of the commands to a file and then copy them to the USB. Start in your home directory (**cd ~**):*

```
cat /etc/network/interfaces > interfaces.txt
``````
ifconfig -a > ifconfig.txt
``````
iwlist scanning > iwlist.txt
``````
sudo lshw -C network > lshw.txt
``````
route -n > route.txt
```Copy all 5 files to floppy/USB, bring them over to Windows and then post them here. All five files should be in your home directory.

-Dave

---

### Post by r_choitram on 2007-05-09
> **chili555 said:**
> Yes. And I'm no less confused now. I don't understand what you are trying to do. First of all, as you suggested, let's concentrate on wired.

As I asked before: I am also concerned that you said you can ping 192.168.1.1, which I assume is the IP address of your router. However, /etc/resolv.conf says the nameserver is 192.168.2.1. 

What is the IP address of your router? Can you get a gateway address from:```
route -n
``` If your router is 192.168.1.1 and /etc/resolv.conf tells the computer to look to resolve names to IP addresses at 192.168.2.1, you are sending it down a dead end.

What is the IP address of the router?

The IP address of my router is:
Gateway = 192.168.2.1

Flag = UG

IFace = eth1

---

### Post by r_choitram on 2007-05-09
Here are the requested text files:

*ifconfig.txt:
eth0      Link encap:Ethernet  HWaddr 00:08:0D:D9:66:CB  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

eth1      Link encap:Ethernet  HWaddr 00:04:23:84:CE:EA  
          inet addr:192.168.2.100  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::204:23ff:fe84:ceea/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:319 errors:0 dropped:0 overruns:0 frame:0
          TX packets:61 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:18847 (18.4 KiB)  TX bytes:6950 (6.7 KiB)
          Interrupt:11 Base address:0x2000 Memory:c2005000-c2005fff 

eth0:avah Link encap:Ethernet  HWaddr 00:08:0D:D9:66:CB  
          inet addr:169.254.8.61  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:535 (535.0 b)  TX bytes:535 (535.0 b)

*interfaces.txt:
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

*iwlist.txt:
eth1      No scan results

*lshw.txt:
  *-network:0
       description: Ethernet interface
       product: 82801DB PRO/100 VE (MOB) Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@02:08.0
       logical name: eth0
       version: 83
       serial: 00:08:0d:d9:66:cb
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.17-k2-NAPI duplex=half firmware=N/A latency=66 link=no maxlatency=56 mingnt=8 multicast=yes port=MII speed=10MB/s
       resources: iomemory:c2004000-c2004fff ioport:3000-303f irq:11
  *-network:1
       description: Wireless interface
       product: PRO/Wireless LAN 2100 3B Mini PCI Adapter
       vendor: Intel Corporation
       physical id: a
       bus info: pci@02:0a.0
       logical name: eth1
       version: 04
       serial: 00:04:23:84:ce:ea
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2100 driverversion=git-1.2.2 firmware=712.0.3:3:00000001 ip=192.168.2.100 latency=64 link=yes maxlatency=34 mingnt=2 multicast=yes wireless=IEEE 802.11b
       resources: iomemory:c2005000-c2005fff irq:11

*route.txt:
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.2.0     0.0.0.0         255.255.255.0   U     0      0        0 eth1
169.254.0.0     0.0.0.0         255.255.0.0     U     0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth1
0.0.0.0         192.168.2.1     0.0.0.0         UG    0      0        0 eth1
0.0.0.0         0.0.0.0         0.0.0.0         U     1000   0        0 eth0


Best Regards,
-Raj Choitram

> **dbott67 said:**
> Just to add to chili's request, can you post the output of the following commands:
```
dbott@feisty:~$ **cat /etc/network/interfaces**
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp

``````
dbott@feisty:~$** ifconfig -a**
eth0      Link encap:Ethernet  HWaddr 00:E0:29:7C:65:3F
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::2e0:29ff:fe7c:653f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:732483 errors:0 dropped:0 overruns:0 frame:0
          TX packets:101659 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:352562729 (336.2 MiB)  TX bytes:6776681 (6.4 MiB)
          Interrupt:9 Base address:0x4c00

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:20 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1740 (1.6 KiB)  TX bytes:1740 (1.6 KiB)

sit0      Link encap:IPv6-in-IPv4
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

``````
dbott@feisty:~$ **iwlist scanning**
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

sit0      Interface doesn't support scanning.

``````
dbott@feisty:~$ **[COLOR=black]sudo lshw -C network[/COLOR]**
  *-network
       description: Ethernet interface
       product: SMC2-1211TX
       vendor: Accton Technology Corporation
       physical id: b
       bus info: pci@02:0b.0
       logical name: eth0
       version: 10
       serial: 00:e0:29:7c:65:3f
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
       configuration: autonegociation=on broadcast=yes driver=8139too driverversion=0.9.27 duplex=full ip=192.168.1.100 link=yes multicast=yes port=MII speed=100MB/s
       resources: ioport:d800-d8ff iomemory:feafbc00-feafbcff irq:9

``````
dbott@feisty:~$ **route -n**
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0


```*Note: if you can't get online with your system & you have a USB thumb drive (or floppy or some other removable media you can write to) you can use the 'redirect' function to write the output of the commands to a file and then copy them to the USB. Start in your home directory (**cd ~**):*

```
cat /etc/network/interfaces > interfaces.txt
``````
ifconfig -a > ifconfig.txt
``````
iwlist scanning > iwlist.txt
``````
sudo lshw -C network > lshw.txt
``````
route -n > route.txt
```Copy all 5 files to floppy/USB, bring them over to Windows and then post them here. All five files should be in your home directory.

-Dave

---

### Post by r_choitram on 2007-05-23
Thank you for helping.

FYI:
- Internet is fixed.

- Needed to setup the IP addresses, and Subnet thingies.

Bye for now,
-Raj

---

