---
title: "Wireless problems"
date: 2006-11-25
forum: Networking &amp; Wireless
---

### Post by The_Swede78 on 2006-11-25
Hi!

I have recently switched from Windows to Linux so I'm more or less a complete newbie to Linux. I have installed Ubuntu and everything seemed to work just fine until I tries to access the Internet trough my wireless card (which is a: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)). The card comes up under admin - networking but I still can't access the Internet. After having read some troubleshooting on this forum I downloaded the windows drivers (at least I think it's the right) for my card. Then I used the admin - windows wireless drivers meny to add the appropriate .inf file (which in my case would be bcmwl5). It reads hardware present: yes. But I still haven't any wireless Internet access. Please, can someone help me. I'm getting very desperate and my last resort is to switch back to Windows again which I hope to avoid.

Thanks in advance

---

### Post by Spin Doctor on 2006-11-25
What version of Ubuntu are you running?

---

### Post by The_Swede78 on 2006-11-25
Hi, I'm running v.6.10, Edgy.

---

### Post by Finn&gt;Potatoe on 2006-11-25
I'm having the same problem...

---

### Post by Spin Doctor on 2006-11-25
> **The_Swede78 said:**
> 
... I have installed Ubuntu and everything seemed to work just fine until I tries to access the Internet trough my wireless card (which is a: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)). 


Go to this page ([http://ndiswrapper.sourceforge.net/mediawiki/index.php/List)]("http://ndiswrapper.sourceforge.net/mediawiki/index.php/List%29"), and download the driver specified for your card. I saw your wireless network card represented in the list.

As quoted on the Ndiswrapper wiki, > **Important: Do NOT use the drivers on your CD. They may work, but you may experience kernel crashes, etc., if the driver on your CD has not been tested**> **The_Swede78 said:**
> 
The card comes up under admin - networking but I still can't access the Internet. After having read some troubleshooting on this forum I downloaded the windows drivers (at least I think it's the right) for my card. Then I used the admin - windows wireless drivers meny to add the appropriate .inf file (which in my case would be bcmwl5). It reads hardware present: yes. 

Yes, this happend for me aswell. I downloaded a more recent driver to my Dlink DWL-g650+ wireless network card, and it showed hardware present on this driver, but refused to work anyway. Then I downloaded the driver that was on the ndiswrapper list (even if it was an older version), and it starts working.  So having hardware present in your settings is no guarantee it will work anyway.

Are you running any kind of encryption?

---

### Post by Spin Doctor on 2006-11-25
Also make sure you have the following line in /etc/modules

ndiswrapper

---

### Post by dbott67 on 2006-11-25
Please post the output of the following commands:
```
ifconfig -a
```
```
cat /etc/network/interfaces
```
```
iwlist scanning
```
```
sudo lshw -C network
```

Thanks,
Dave

---

### Post by The_Swede78 on 2006-11-25
First of all, thanks guys for your replies.

Spin doctor, no there is no encryption.

dbott67, here are my results:

ifconfig -a

eth0      Link encap:Ethernet  HWaddr 00:C0:9F:9C:DA:9A  
          inet addr:192.168.0.160  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::2c0:9fff:fe9c:da9a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3201 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3114 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2116648 (2.0 MiB)  TX bytes:475601 (464.4 KiB)
          Interrupt:169 Base address:0x1800 

eth1      Link encap:Ethernet  HWaddr 00:0E:9B:CD:47:44  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:4 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)

sit0      Link encap:IPv6-in-IPv4  
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

------------------------------------------------------------------------

cat /etc/network/interfaces

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp


auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp





iface eth1 inet dhcp
wireless-essid SU

-------------------------------------------------------------

iwlist scanning

lo        Interface doesn't support scanning.

eth1      No scan results
eth0      Interface doesn't support scanning.

sit0      Interface doesn't support scanning.


--------------------------------------------------------------

sudo lshw -C network

 *-network:0             
       description: Ethernet interface
       product: SiS900 PCI Fast Ethernet
       vendor: Silicon Integrated Systems [SiS]
       physical id: 4
       bus info: pci@00:04.0
       logical name: eth0
       version: 91
       serial: 00:c0:9f:9c:da:9a
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
       configuration: autonegociation=on broadcast=yes driver=sis900 driverversion=v1.08.09 Sep. 19 2005 duplex=full ip=192.168.0.160 link=yes multicast=yes port=MII speed=100MB/s
       resources: ioport:1800-18ff iomemory:e2005000-e2005fff irq:169
  *-network:1 DISABLED
       description: Wireless interface
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: b
       bus info: pci@00:0b.0
       logical name: eth1
       version: 02
       serial: 00:0e:9b:cd:47:44
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=bcm43xx driverversion=2.6.17-10-generic link=no multicast=yes wireless=IEEE 802.11b/g
       resources: iomemory:e2000000-e2001fff irq:217



Thanks again for your asistance and sorry for my late response.

/Thomas

---

### Post by dbott67 on 2006-11-25
It looks like 'eth1' is your wireless interface and it needs enabling *(notice how there is no 'wlan0' when your type 'ifconfig -a', but when you type 'iwlist scanning', your 'eth1' reports 'No scan results').*

Just try 'enabling' your wireless interface using this command:
```
sudo ifup eth1
```
```
sudo dhclient eth1
```

If this doesn't work, post the output of the above 2 commands.  If it does work, modify your /etc/network/interfaces file to look like this:
```
gksudo gedit /etc/network/interfaces
```
```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp


auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

**[COLOR="Red"]auto eth1[/COLOR]**
iface eth1 inet dhcp
wireless-essid SU
```

-Dave

---

### Post by The_Swede78 on 2006-11-26
Hi Dave!

This is the results from the commands you've posted.

sudo ifup eth1

Password:
/etc/network/interfaces:23: duplicate interface
ifup: couldn't read interfaces file "/etc/network/interfaces"

-----------------------------------------------------------------

sudo dhclient eth1

Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFFLAGS: No such file or directory
SIOCSIFFLAGS: No such file or directory
Listening on LPF/eth1/00:0e:9b:cd:47:44
Sending on   LPF/eth1/00:0e:9b:cd:47:44
Sending on   Socket/fallback
receive_packet failed on eth1: Network is down
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
send_packet: Network is down
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
send_packet: Network is down
--------------------------------------------------------------

/Thomas

---

### Post by The_Swede78 on 2006-11-26
Hmmm, why does "it" try to send an DHCPDiscover to the address  255.255.255.255 on eth1? Is that the reason to why I can't access the Internet? Or is that some sort of broadcast address?

/Thomas

---

### Post by dbott67 on 2006-11-26
It's the broadcast address:
```
dbott@edgy:~$ sudo dhclient eth0
Password:
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:50:ba:c0:a7:55
Sending on   LPF/eth0/00:50:ba:c0:a7:55
Sending on   Socket/fallback
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 192.168.1.1
bound to 192.168.1.106 -- renewal in 256370 seconds.

```

-Dave

---

### Post by dbott67 on 2006-11-26
It could be a munged interfaces file... or possibly a permissions thing.  Can you post the output of:
```
ls -all /etc/network/interfaces
```
```
dbott@edgy:~$ ls -all /etc/network/interfaces 
-rw-r--r-- 1 root root 194 2006-11-10 20:36 /etc/network/interfaces

```
Next, let's try re-configuring the network card:

```
sudo ip addr flush dev eth1 && sudo ip link set eth1 down
```
```
sudo ip link set eth1 up
```
```
sudo /sbin/dhclient eth1
```

If this doesn't work you can set a static ip by changing the file to:
```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

auto eth1
**[COLOR="Red"]#iface eth1 inet dhcp[/COLOR]**
[COLOR="Blue"]iface eth1 inet static
address 192.168.0.99
netmask 255.255.255.0
gateway 192.168.0.1[/COLOR]
wireless-essid SU
```

After changing this file, you can do one of the following to enable the change:
```
sudo /etc/init.d/networking restart
```
OR
```
sudo ifdown eth1 && sudo ifup eth1
```

-Dave

---

### Post by The_Swede78 on 2006-11-26
Hi Dave! I really appreciate your time and effort to help me.

This is the results from the commands:

 thomas@ttlaptop:~$ ls -all /etc/network/interfaces
-rw-r----- 1 root admin 265 2006-11-26 02:02 /etc/network/interfaces


(This seems to match your output)
-------------------------------------------------------------------------

thomas@ttlaptop:~$ sudo ip addr flush dev eth1 && sudo ip link set eth1 down
Password:
Nothing to flush.

-------------------------------------------------------------------------

thomas@ttlaptop:~$ sudo ip link set eth1 up
SIOCSIFFLAGS: No such file or directory

-------------------------------------------------------------------------

thomas@ttlaptop:~$ sudo /sbin/dhclient eth1
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFFLAGS: No such file or directory
SIOCSIFFLAGS: No such file or directory
Listening on LPF/eth1/00:0e:9b:cd:47:44
Sending on   LPF/eth1/00:0e:9b:cd:47:44
Sending on   Socket/fallback
receive_packet failed on eth1: Network is down
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
send_packet: Network is down
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
send_packet: Network is down

I will try to set a static IP as you suggested.

Thanks

/Thomas

---

