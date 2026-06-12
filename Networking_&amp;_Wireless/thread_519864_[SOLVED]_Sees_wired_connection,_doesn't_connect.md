---
title: "[SOLVED] Sees wired connection, doesn't connect"
date: 2007-08-07
forum: Networking &amp; Wireless
---

### Post by durrell on 2007-08-07
I've been using Ubuntu since May, and have never encountered a problem until now. I just bought a SATA hard drive and installed Ubuntu after Windows XP. Now, Ubuntu won't connect to the internet. It sees my ethernet connection, but DHCP won't assign an address to my computer in Ubuntu. I tried assigning a static IP as well as tried different DNS servers, but nothing works. It won't even show my router's administration screen when I type the gateway into my address bar. I have unplugged the router and checked all connections between the router and my computer. I know it's not a connection issue because I'm posting this from Windows and it's working just fine. Any ideas as to what the problem could be?

This problem is also occurring in my OS X install. I never had a problem with it either until this fresh install on the new drive.

Thanks in advance for any help.

---

### Post by noob12 on 2007-08-07
For starters, show us
```

lspci -nn

sudo lshw -C network

ifconfig -a

cat /etc/network/interfaces

```

---

### Post by durrell on 2007-08-07
```

darryl@darryl-desktop:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface [8086:2570] (rev 02)
00:01.0 PCI bridge [0604]: Intel Corporation 82865G/PE/P PCI to AGP Controller [8086:2571] (rev 02)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 [8086:24d2] (rev 02)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 [8086:24d4] (rev 02)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 [8086:24d7] (rev 02)
00:1d.3 USB Controller [0c03]: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 [8086:24de] (rev 02)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller [8086:24dd] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev c2)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge [8086:24d0] (rev 02)
00:1f.1 IDE interface [0101]: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller [8086:24db] (rev 02)
00:1f.2 IDE interface [0101]: Intel Corporation 82801EB (ICH5) SATA Controller [8086:24d1] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller [8086:24d3] (rev 02)
00:1f.5 Multimedia audio controller [0401]: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller [8086:24d5] (rev 02)
01:00.0 VGA compatible controller [0300]: nVidia Corporation NV44A [GeForce 6200] [10de:0221] (rev a1)
02:05.0 Communication controller [0780]: Agere Systems V.92 56K WinModem [11c1:048c] (rev 02)
02:0b.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)

```

```

darryl@darryl-desktop:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: b
       bus info: pci@02:0b.0
       logical name: eth0
       version: 10
       serial: 00:0c:76:ce:51:15
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full latency=32 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100MB/s
       resources: ioport:b400-b4ff iomemory:f7effe00-f7effeff irq:18

```

```

darryl@darryl-desktop:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:0C:76:CE:51:15  
          inet6 addr: fe80::20c:76ff:fece:5115/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:18 Base address:0x2e00 

eth0:avah Link encap:Ethernet  HWaddr 00:0C:76:CE:51:15  
          inet addr:169.254.5.16  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:18 Base address:0x2e00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:610 (610.0 b)  TX bytes:610 (610.0 b)

```

```

darryl@darryl-desktop:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback


iface eth0 inet dhcp
address 192.168.1.86
netmask 255.255.255.0
gateway 192.168.1.254

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp


auto eth0

```

---

### Post by noob12 on 2007-08-07
In your **/etc/network/interfaces**, do you mean to use static or dynamic configuration?
If dhcp, you should remove/comment out the address, netmask and gateway lines.  That's not the cause though.


> 
iface eth0 inet dhcp
address 192.168.1.86
netmask 255.255.255.0
gateway 192.168.1.254


I'd also bring the **auto eth0** line up from the bottom to just above **iface** to keep things readable for humans, but it will work like you have it.

Can you run **aptitude show dhcp3-client | grep State ** and **ps -ef | grep dhclient**

---

### Post by durrell on 2007-08-07
```
darryl@darryl-desktop:~$ aptitude show dhcp3-client | grep State
State: installed

```

```

darryl@darryl-desktop:~$ ps -ef | grep dhclient
dhcp      5415     1  0 17:23 ?        00:00:00 dhclient3 -pf /var/run/dhclient.eth0.pid -lf /var/lib/dhcp3/dhclient.eth0.leases eth0
darryl    5477  5387  0 17:25 pts/0    00:00:00 grep dhclient

```

And I also edited the /etc/network/interfaces like you said to.

Thanks!

---

### Post by noob12 on 2007-08-07
Everything looking normal so far.

So more diagnostics.  After full shutdown and reboot, can you post the result of
```

sudo ethtool eth0

grep dhclient /var/log/syslog

dmesg

```

If you don't have connectivity at that point, can you tell me what happens if you
manually cycle eth0 down and back up as follows?
```

sudo /sbin/ifdown eth0
sudo /sbin/ifup eth0

```

Does it work then?

what happens?

---

### Post by durrell on 2007-08-07
```
darryl@darryl-desktop:~$ sudo ethtool eth0
Settings for eth0:
        Supported ports: [ TP MII ]
        Supported link modes:   10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
        Supports auto-negotiation: Yes
        Advertised link modes:  10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
        Advertised auto-negotiation: Yes
        Speed: 100Mb/s
        Duplex: Full
        Port: MII
        PHYAD: 32
        Transceiver: internal
        Auto-negotiation: on
        Supports Wake-on: pumbg
        Wake-on: d
        Current message level: 0x00000007 (7)
        Link detected: yes

```

```
darryl@darryl-desktop:~$ grep dhclient /var/log/syslog
Aug  7 18:06:22 darryl-desktop dhclient: Internet Systems Consortium DHCP Client V3.0.4
Aug  7 18:06:22 darryl-desktop dhclient: Copyright 2004-2006 Internet Systems Consortium.
Aug  7 18:06:22 darryl-desktop dhclient: All rights reserved.
Aug  7 18:06:22 darryl-desktop dhclient: For info, please visit http://www.isc.org/sw/dhcp/
Aug  7 18:06:22 darryl-desktop dhclient: 
Aug  7 18:06:23 darryl-desktop dhclient: Listening on LPF/eth0/00:0c:76:ce:51:15
Aug  7 18:06:23 darryl-desktop dhclient: Sending on   LPF/eth0/00:0c:76:ce:51:15
Aug  7 18:06:23 darryl-desktop dhclient: Sending on   Socket/fallback
Aug  7 18:06:24 darryl-desktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
Aug  7 18:06:27 darryl-desktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
Aug  7 18:06:35 darryl-desktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
Aug  7 18:06:44 darryl-desktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
Aug  7 18:06:54 darryl-desktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 1
Aug  7 18:06:55 darryl-desktop dhclient: No DHCPOFFERS received.
Aug  7 18:06:55 darryl-desktop dhclient: No working leases in persistent database - sleeping.
Aug  7 16:51:17 darryl-desktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 20
Aug  7 16:51:37 darryl-desktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
Aug  7 16:51:42 darryl-desktop dhclient: No DHCPOFFERS received.
Aug  7 16:51:42 darryl-desktop dhclient: No working leases in persistent database - sleeping.
Aug  7 16:58:57 darryl-desktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
Aug  7 16:59:00 darryl-desktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
Aug  7 16:59:08 darryl-desktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
Aug  7 16:59:23 darryl-desktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
Aug  7 16:59:28 darryl-desktop dhclient: No DHCPOFFERS received.
Aug  7 16:59:28 darryl-desktop dhclient: No working leases in persistent database - sleeping.
Aug  7 17:22:56 darryl-desktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 16
Aug  7 17:23:12 darryl-desktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
Aug  7 17:23:20 darryl-desktop dhclient: No DHCPOFFERS received.
Aug  7 17:23:20 darryl-desktop dhclient: No working leases in persistent database - sleeping.
Aug  7 17:28:47 darryl-desktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
Aug  7 17:28:50 darryl-desktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
Aug  7 17:28:53 darryl-desktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
Aug  7 20:19:06 darryl-desktop dhclient: There is already a pid file /var/run/dhclient.eth0.pid with pid 134993440
Aug  7 20:19:07 darryl-desktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
Aug  7 20:19:10 darryl-desktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
Aug  7 20:19:16 darryl-desktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
Aug  7 20:19:17 darryl-desktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
Aug  7 20:19:25 darryl-desktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
Aug  7 20:19:29 darryl-desktop dhclient: No DHCPOFFERS received.
Aug  7 20:19:29 darryl-desktop dhclient: No working leases in persistent database - sleeping.
Aug  7 20:19:36 darryl-desktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
Aug  7 20:19:41 darryl-desktop dhclient: No DHCPOFFERS received.
Aug  7 20:21:02 darryl-desktop dhclient: There is already a pid file /var/run/dhclient.eth0.pid with pid 5466
Aug  7 20:21:02 darryl-desktop dhclient: killed old client process, removed PID file
Aug  7 20:21:02 darryl-desktop dhclient: Internet Systems Consortium DHCP Client V3.0.4
Aug  7 20:21:02 darryl-desktop dhclient: Copyright 2004-2006 Internet Systems Consortium.
Aug  7 20:21:02 darryl-desktop dhclient: All rights reserved.
Aug  7 20:21:02 darryl-desktop dhclient: For info, please visit http://www.isc.org/sw/dhcp/
Aug  7 20:21:02 darryl-desktop dhclient: 
Aug  7 20:21:02 darryl-desktop dhclient: Listening on LPF/eth0/00:0c:76:ce:51:15
Aug  7 20:21:02 darryl-desktop dhclient: Sending on   LPF/eth0/00:0c:76:ce:51:15
Aug  7 20:21:02 darryl-desktop dhclient: Sending on   Socket/fallback
Aug  7 20:21:10 darryl-desktop dhclient: There is already a pid file /var/run/dhclient.eth0.pid with pid 134993416
Aug  7 20:21:10 darryl-desktop dhclient: Internet Systems Consortium DHCP Client V3.0.4
Aug  7 20:21:10 darryl-desktop dhclient: Copyright 2004-2006 Internet Systems Consortium.
Aug  7 20:21:10 darryl-desktop dhclient: All rights reserved.
Aug  7 20:21:10 darryl-desktop dhclient: For info, please visit http://www.isc.org/sw/dhcp/
Aug  7 20:21:10 darryl-desktop dhclient: 
Aug  7 20:21:11 darryl-desktop dhclient: Listening on LPF/eth0/00:0c:76:ce:51:15
Aug  7 20:21:11 darryl-desktop dhclient: Sending on   LPF/eth0/00:0c:76:ce:51:15
Aug  7 20:21:11 darryl-desktop dhclient: Sending on   Socket/fallback
Aug  7 20:21:12 darryl-desktop dhclient: There is already a pid file /var/run/dhclient.eth0.pid with pid 134993440
Aug  7 20:21:13 darryl-desktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
Aug  7 20:21:16 darryl-desktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
Aug  7 20:21:19 darryl-desktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
Aug  7 20:21:23 darryl-desktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
Aug  7 20:21:27 darryl-desktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
Aug  7 20:21:37 darryl-desktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
Aug  7 20:21:38 darryl-desktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
Aug  7 20:21:44 darryl-desktop dhclient: No DHCPOFFERS received.
Aug  7 20:21:44 darryl-desktop dhclient: No working leases in persistent database - sleeping.
Aug  7 20:21:47 darryl-desktop dhclient: No DHCPOFFERS received.

```

```
darryl@darryl-desktop:~$ sudo /sbin/ifdown eth0
RTNETLINK answers: No such process
There is already a pid file /var/run/dhclient.eth0.pid with pid 5466
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:0c:76:ce:51:15
Sending on   LPF/eth0/00:0c:76:ce:51:15
Sending on   Socket/fallback
darryl@darryl-desktop:~$ sudo /sbin/ifup eth0
There is already a pid file /var/run/dhclient.eth0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:0c:76:ce:51:15
Sending on   LPF/eth0/00:0c:76:ce:51:15
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```

I didn't do dmesg because I couldn't get it all to copy. If you can tell me how to copy the output to a text file, I can show it.

---

### Post by noob12 on 2007-08-07
So far everything looks good except you are getting no DHCP responses at all.

The file **/var/log/dmesg** would already have dmesg output.  That would be a good
check to be sure, but it looks less likely that we'll see any issue there at this point.

We either aren't getting a packet out to the DHCP service or it isn't sending a response back or we aren't receiving it.   Link state in ethtool looks fine.  Let's make sure we aren't running a firewall blocking things.  This will tell us:
```

sudo iptables -nL

```

---

### Post by durrell on 2007-08-07
```

darryl@darryl-desktop:~$ sudo iptables -nL
Password:
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination

```

---

### Post by noob12 on 2007-08-08
No firewall issue.

I think we do need to look at the dmesg log; I'm starting to suspect a driver issue.  I'm seeing some old posts related to 8139too having similar behavior, but I'm not sure we're in the same situation.

However, before we try diving into driver stuff, let's try to manually configure the interface again and make sure we can't ping anything locally.

We need an address, netmask, gateway.  I'm assuming that the values you had earlier in your config are ok.   The only one that looks odd is the gateway.  Most people put their gateways at the .1 address rather than the .254.  Verify yours and correct the values below if needed.

Replace the current eth0 stanza in /etc/network/interfaces with this, which will
look familiar, but we now have the important word **static** here now.
```

auto eth0
iface eth0 inet static
address 192.168.1.86
netmask 255.255.255.0
gateway 192.168.1.254

```
then once again
```

sudo /sbin/ifdown eth0
sudo /sbin/ifup eth0

```

Then
```

ping 192.168.1.254

```
and any other addresses you know to be live on the LAN.

After all that see if **ifconfig** shows values of TX packets > 0 or RX packets > 0 for eth0.

If this doesn't work, we have to look at the driver-level stuff.

---

### Post by durrell on 2007-08-08
[IMG]http://img.photobucket.com/albums/v157/Durrell12/ip.jpg[/IMG]

Those are the settings I'm using in Windows. I'll try what you suggested and see what happens.

---

### Post by OpticalIllusion on 2007-08-08
I have a feeling you're having the same problem as I am.  You also have a Realtek 8139 ethernet adapter I see.  The problem is that the adapter isn't even being turned on by the OS.  If you look in the back of your computer, you will see that neither of the LED's around the port are lighting up.  The adapter is identified through lspci and such, but it isn't being activated by the OS.  Mine used to work with Fiesty for about 5 days and one day just quit working completely.

---

### Post by durrell on 2007-08-08
Well nothing worked. I even tried a different network card, and although it did assign me an IP..it still wouldn't connect to the router nor the internet. :(

This same computer has never had any issues with any of my Linux installs until now.

---

### Post by noob12 on 2007-08-08
WIth the 8139 card, I think we need to look at driver issues.  The same card is working in Windows. In the worst case we should be able to use ndiswrapper and the windows driver.  If you want to use the other card, on which you say you got an IP,  we have to make sure your DNS is working.  You seem very close.

---

### Post by OpticalIllusion on 2007-08-08
> **noob12 said:**
> WIth the 8139 card, I think we need to look at driver issues.  The same card is working in Windows. In the worst case we should be able to use ndiswrapper and the windows driver.  If you want to use the other card, on which you say you got an IP,  we have to make sure your DNS is working.  You seem very close.
I thought ndiswrapper was for wireless cards only.  We are talking about a wired ethernet adapter.

---

### Post by noob12 on 2007-08-08
Actually ndiswrapper is for any NDIS Windows driver.  Hard or wireless.  

It's just that most hard cards are covered by the linux native drivers.  We're just having a bit of a problem with 8139too just now.  

Being a bit too myopic perhaps, I'll look for solutions to the driver problem in the forums.

---

### Post by durrell on 2007-08-08
The weird thing is the other card appeared to be using the 8139 driver as well. So let's just go from there.

What should I try next?

And yes, this is a wired connection.

Edit: Since I never had any issues with this card before, should I wipe the Ubuntu install and try a fresh one?

---

### Post by noob12 on 2007-08-08
Hey durrell.  You never showed me the dmesg log! I might see something there.

---

### Post by durrell on 2007-08-08
Dang I had it saved and then deleted it because I didn't think we needed it.

---

### Post by noob12 on 2007-08-08
It's always there for you sitting in /var/log/dmesg.

---

### Post by durrell on 2007-08-08
Getting it now.

---

### Post by durrell on 2007-08-08
```
[    0.000000] Linux version 2.6.20-15-generic (root@palmer) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Sun Apr 15 07:36:31 UTC 2007 (Ubuntu 2.6.20-15.27-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000] sanitize start
[    0.000000] sanitize end
[    0.000000] copy_e820_map() start: 0000000000000000 size: 000000000009fc00 end: 000000000009fc00 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000000009fc00 size: 0000000000000400 end: 00000000000a0000 type: 2
[    0.000000] copy_e820_map() start: 00000000000d0000 size: 0000000000008010 end: 00000000000d8010 type: 2
[    0.000000] copy_e820_map() start: 00000000000f0000 size: 0000000000010000 end: 0000000000100000 type: 2
[    0.000000] copy_e820_map() start: 0000000000100000 size: 000000003fef0000 end: 000000003fff0000 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000003fff0000 size: 0000000000008000 end: 000000003fff8000 type: 3
[    0.000000] copy_e820_map() start: 000000003fff8000 size: 0000000000008000 end: 0000000040000000 type: 4
[    0.000000] copy_e820_map() start: 00000000fec00000 size: 0000000000001000 end: 00000000fec01000 type: 2
[    0.000000] copy_e820_map() start: 00000000fee00000 size: 0000000000001000 end: 00000000fee01000 type: 2
[    0.000000] copy_e820_map() start: 00000000fff00000 size: 0000000000100000 end: 0000000100000000 type: 2
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000d0000 - 00000000000d8010 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003fff0000 (usable)
[    0.000000]  BIOS-e820: 000000003fff0000 - 000000003fff8000 (ACPI data)
[    0.000000]  BIOS-e820: 000000003fff8000 - 0000000040000000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000] 127MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] found SMP MP-table at 000fc120
[    0.000000] Entering add_active_range(0, 0, 262128) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   262128
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   262128
[    0.000000] On node 0 totalpages: 262128
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 255 pages used for memmap
[    0.000000]   HighMem zone: 32497 pages, LIFO batch:7
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP (v000 AMI                                   ) @ 0x000fa3c0
[    0.000000] ACPI: RSDT (v001 AMIINT INTEL865 0x00000010 MSFT 0x00000097) @ 0x3fff0000
[    0.000000] ACPI: FADT (v001 AMIINT INTEL865 0x00000011 MSFT 0x00000097) @ 0x3fff0030
[    0.000000] ACPI: MADT (v001 AMIINT INTEL865 0x00000009 MSFT 0x00000097) @ 0x3fff00c0
[    0.000000] ACPI: DSDT (v001  INTEL    I865G 0x00001000 MSFT 0x0100000d) @ 0x00000000
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] Processor #0 15:2 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] Processor #1 15:2 APIC version 20
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 50000000 (gap: 40000000:bec00000)
[    0.000000] Detected 3000.158 MHz processor.
[   17.947471] Built 1 zonelists.  Total pages: 260081
[   17.947475] Kernel command line: root=UUID=645555aa-44e3-4607-b8eb-3fa97c6b6c00 ro quiet splash
[   17.947615] mapped APIC to ffffd000 (fee00000)
[   17.947618] mapped IOAPIC to ffffc000 (fec00000)
[   17.947621] Enabling fast FPU save and restore... done.
[   17.947623] Enabling unmasked SIMD FPU exception support... done.
[   17.947634] Initializing CPU#0
[   17.947704] PID hash table entries: 4096 (order: 12, 16384 bytes)
[   17.949960] Console: colour VGA+ 80x25
[   17.950467] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   17.950957] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   17.975763] Memory: 1028060k/1048512k available (1992k kernel code, 19720k reserved, 893k data, 328k init, 131008k highmem)
[   17.975773] virtual kernel memory layout:
[   17.975774]     fixmap  : 0xfff4e000 - 0xfffff000   ( 708 kB)
[   17.975775]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   17.975776]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   17.975777]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   17.975778]       .init : 0xc03d7000 - 0xc0429000   ( 328 kB)
[   17.975778]       .data : 0xc02f2264 - 0xc03d16d4   ( 893 kB)
[   17.975779]       .text : 0xc0100000 - 0xc02f2264   (1992 kB)
[   17.975782] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   18.055614] Calibrating delay using timer specific routine.. 6004.56 BogoMIPS (lpj=12009132)
[   18.055656] Security Framework v1.0.0 initialized
[   18.055665] SELinux:  Disabled at boot.
[   18.055680] Mount-cache hash table entries: 512
[   18.055835] CPU: After generic identify, caps: bfebfbff 00000000 00000000 00000000 00004400 00000000 00000000
[   18.055846] CPU: Trace cache: 12K uops, L1 D cache: 8K
[   18.055849] CPU: L2 cache: 512K
[   18.055851] CPU: Physical Processor ID: 0
[   18.055853] CPU: After all inits, caps: bfebfbff 00000000 00000000 00003080 00004400 00000000 00000000
[   18.055865] Compat vDSO mapped to ffffe000.
[   18.055869] Remapping vsyscall page to ffffe000
[   18.055882] Checking 'hlt' instruction... OK.
[   18.071705] SMP alternatives: switching to UP code
[   18.072094] Early unpacking initramfs... done
[   18.338251] ACPI: Core revision 20060707
[   18.339037] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
[   18.340763] CPU0: Intel(R) Pentium(R) 4 CPU 3.00GHz stepping 09
[   18.340786] SMP alternatives: switching to SMP code
[   18.340963] Booting processor 1/1 eip 3000
[   18.351295] Initializing CPU#1
[   18.431280] Calibrating delay using timer specific routine.. 6000.64 BogoMIPS (lpj=12001280)
[   18.431289] CPU: After generic identify, caps: bfebfbff 00000000 00000000 00000000 00004400 00000000 00000000
[   18.431298] CPU: Trace cache: 12K uops, L1 D cache: 8K
[   18.431301] CPU: L2 cache: 512K
[   18.431303] CPU: Physical Processor ID: 0
[   18.431305] CPU: After all inits, caps: bfebfbff 00000000 00000000 00003080 00004400 00000000 00000000
[   18.431515] CPU1: Intel(R) Pentium(R) 4 CPU 3.00GHz stepping 09
[   18.431554] Total of 2 processors activated (12005.20 BogoMIPS).
[   18.431675] ENABLING IO-APIC IRQs
[   18.431854] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   18.579158] checking TSC synchronization across 2 CPUs: passed.
[    0.003995] Brought up 2 CPUs
[    0.062974] migration_cost=223
[    0.063277] Booting paravirtualized kernel on bare hardware
[    0.063358] Time:  1:35:34  Date: 07/08/107
[    0.063389] NET: Registered protocol family 16
[    0.063491] EISA bus registered
[    0.063496] ACPI: bus type pci registered
[    0.064749] PCI: PCI BIOS revision 2.10 entry at 0xfdb81, last bus=2
[    0.064751] PCI: Using configuration type 1
[    0.064752] Setting up standard PCI resources
[    0.081520] ACPI: Interpreter enabled
[    0.081524] ACPI: Using IOAPIC for interrupt routing
[    0.081994] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.081999] PCI: Probing PCI hardware (bus 00)
[    0.082873] PCI quirk: region 0800-087f claimed by ICH4 ACPI/GPIO/TCO
[    0.082877] PCI quirk: region 0400-043f claimed by ICH4 GPIO
[    0.083133] Boot video device is 0000:01:00.0
[    0.083331] PCI: Transparent bridge - 0000:00:1e.0
[    0.083356] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.086016] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.ICHB._PRT]
[    0.088387] ACPI: Power Resource [URP1] (off)
[    0.088460] ACPI: Power Resource [URP2] (off)
[    0.088533] ACPI: Power Resource [FDDP] (off)
[    0.088604] ACPI: Power Resource [LPTP] (off)
[    0.089356] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 6 7 *10 11 12 14 15)
[    0.089586] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 6 7 *10 11 12 14 15)
[    0.089815] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 6 7 10 *11 12 14 15)
[    0.090082] ACPI: PCI Interrupt Link [LNKD] (IRQs *3 4 6 7 10 11 12 14 15)
[    0.090308] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 6 7 10 11 12 14 15) *0, disabled.
[    0.090528] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 6 7 10 11 12 14 15) *0, disabled.
[    0.090753] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 6 7 10 11 12 14 15) *0, disabled.
[    0.091014] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 *5 6 7 12 14 15)
[    0.091138] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.091151] pnp: PnP ACPI init
[    0.093772] pnp: PnP ACPI: found 10 devices
[    0.093778] PnPBIOS: Disabled by ACPI PNP
[    0.093849] PCI: Using ACPI for IRQ routing
[    0.093853] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[    0.097591] NET: Registered protocol family 8
[    0.097593] NET: Registered protocol family 20
[    0.098196] PCI: Bridge: 0000:00:01.0
[    0.098199]   IO window: disabled.
[    0.098203]   MEM window: f3d00000-f7dfffff
[    0.098207]   PREFETCH window: d3c00000-f3bfffff
[    0.098212] PCI: Bridge: 0000:00:1e.0
[    0.098215]   IO window: b000-bfff
[    0.098220]   MEM window: f7e00000-f7efffff
[    0.098224]   PREFETCH window: 50000000-500fffff
[    0.098240] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[    0.098275] NET: Registered protocol family 2
[    0.135946] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.136120] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.136827] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.137265] TCP: Hash tables configured (established 131072 bind 65536)
[    0.137270] TCP reno registered
[    0.148019] checking if image is initramfs... it is
[    0.681892] Freeing initrd memory: 7004k freed
[    0.682340] audit: initializing netlink socket (disabled)
[    0.682352] audit(1186536934.392:1): initialized
[    0.682485] highmem bounce pool size: 64 pages
[    0.682587] VFS: Disk quotas dquot_6.5.1
[    0.682607] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.682659] io scheduler noop registered
[    0.682663] io scheduler anticipatory registered
[    0.682665] io scheduler deadline registered
[    0.682676] io scheduler cfq registered (default)
[    0.682989] isapnp: Scanning for PnP cards...
[    1.036102] isapnp: No Plug & Play device found
[    1.065220] Real Time Clock Driver v1.12ac
[    1.065274] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[    1.065380] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.066175] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.066439] mice: PS/2 mouse device common for all mice
[    1.067135] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[    1.067299] input: Macintosh mouse button emulation as /class/input/input0
[    1.067342] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[    1.067346] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[    1.067649] PNP: No PS/2 controller found. Probing ports directly.
[    1.069965] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.069971] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.070102] EISA: Probing bus 0 at eisa.0
[    1.070140] EISA: Detected 0 cards.
[    1.100214] TCP cubic registered
[    1.100222] NET: Registered protocol family 1
[    1.100248] Starting balanced_irq
[    1.100257] Using IPI No-Shortcut mode
[    1.100363] ACPI: (supports S0 S1 S4 S5)
[    1.100406]   Magic number: 3:743:558
[    1.100502]   hash matches device ptya4
[    1.100856] Freeing unused kernel memory: 328k freed
[    1.103020] Time: tsc clocksource has been installed.
[    2.342443] Capability LSM initialized
[    2.388505] ACPI: Processor [CPU1] (supports 8 throttling states)
[    2.388522] ACPI: Processor [CPU2] (supports 8 throttling states)
[    3.052217] usbcore: registered new interface driver usbfs
[    3.052255] usbcore: registered new interface driver hub
[    3.052294] usbcore: registered new device driver usb
[    3.053687] USB Universal Host Controller Interface driver v3.0
[    3.053767] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 16 (level, low) -> IRQ 16
[    3.053783] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[    3.053789] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    3.053923] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[    3.053969] uhci_hcd 0000:00:1d.0: irq 16, io base 0x0000cc00
[    3.054134] usb usb1: configuration #1 chosen from 1 choice
[    3.054191] hub 1-0:1.0: USB hub found
[    3.054206] hub 1-0:1.0: 2 ports detected
[    3.063210] Floppy drive(s): fd0 is 1.44M
[    3.066093] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[    3.084975] FDC 0 is a post-1991 82077
[    3.161242] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 17
[    3.161261] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[    3.161267] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    3.161299] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[    3.161330] uhci_hcd 0000:00:1d.1: irq 17, io base 0x0000d000
[    3.161471] usb usb2: configuration #1 chosen from 1 choice
[    3.161523] hub 2-0:1.0: USB hub found
[    3.161536] hub 2-0:1.0: 2 ports detected
[    3.269146] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
[    3.269163] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[    3.269168] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    3.269207] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[    3.269236] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000d400
[    3.269389] usb usb3: configuration #1 chosen from 1 choice
[    3.269440] hub 3-0:1.0: USB hub found
[    3.269452] hub 3-0:1.0: 2 ports detected
[    3.377045] ACPI: PCI Interrupt 0000:00:1d.3[A] -> GSI 16 (level, low) -> IRQ 16
[    3.377060] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[    3.377066] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    3.377107] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[    3.377131] uhci_hcd 0000:00:1d.3: irq 16, io base 0x0000d800
[    3.377276] usb usb4: configuration #1 chosen from 1 choice
[    3.377329] hub 4-0:1.0: USB hub found
[    3.377342] hub 4-0:1.0: 2 ports detected
[    3.404885] usb 1-2: new low speed USB device using uhci_hcd and address 2
[    3.485115] ACPI: PCI Interrupt 0000:00:1d.7[D] -> GSI 23 (level, low) -> IRQ 19
[    3.485134] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[    3.485139] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    3.485186] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[    3.485238] ehci_hcd 0000:00:1d.7: debug port 1
[    3.485249] PCI: cache line size of 128 is not supported by device 0000:00:1d.7
[    3.485265] ehci_hcd 0000:00:1d.7: irq 19, io mem 0xf7fff800
[    3.489154] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    3.489321] usb usb5: configuration #1 chosen from 1 choice
[    3.489371] hub 5-0:1.0: USB hub found
[    3.489385] hub 5-0:1.0: 8 ports detected
[    3.605078] SCSI subsystem initialized
[    3.605199] 8139cp 0000:02:0b.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip
[    3.605203] 8139cp 0000:02:0b.0: Try the "8139too" driver instead.
[    3.620968] libata version 2.20 loaded.
[    3.620997] 8139too Fast Ethernet driver 0.9.28
[    3.621080] ACPI: PCI Interrupt 0000:02:0b.0[A] -> GSI 23 (level, low) -> IRQ 19
[    3.621428] eth0: RealTek RTL8139 at 0xf8876e00, 00:0c:76:ce:51:15, IRQ 19
[    3.621433] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[    3.628048] ata_piix 0000:00:1f.1: version 2.10ac1
[    3.628066] PCI: Enabling device 0000:00:1f.1 (0005 -> 0007)
[    3.628074] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 18
[    3.628110] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[    3.628208] ata1: PATA max UDMA/133 cmd 0x0001ec00 ctl 0x0001e802 bmdma 0x0001dc00 irq 18
[    3.628257] ata2: PATA max UDMA/133 cmd 0x0001e400 ctl 0x0001e002 bmdma 0x0001dc08 irq 18
[    3.628272] scsi0 : ata_piix
[    3.784581] scsi1 : ata_piix
[    3.940383] usb 1-2: device not accepting address 2, error -71
[    4.112565] ata2.00: ATAPI, max UDMA/33
[    4.284503] ata2.00: configured for UDMA/33
[    4.286684] scsi 1:0:0:0: CD-ROM            _NEC     DVD+RW ND-1100A  1.90 PQ: 0 ANSI: 5
[    4.286805] ata_piix 0000:00:1f.2: MAP [ P1 -- P0 -- ]
[    4.286830] ACPI: PCI Interrupt 0000:00:1f.2[A] -> GSI 18 (level, low) -> IRQ 18
[    4.286854] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[    4.287056] ata3: SATA max UDMA/133 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x0001fc00 irq 14
[    4.287099] ata4: SATA max UDMA/133 cmd 0x00010170 ctl 0x00010376 bmdma 0x0001fc08 irq 15
[    4.287118] scsi2 : ata_piix
[    4.490261] ata3.00: ata_hpa_resize 1: sectors = 976773168, hpa_sectors = 976773168
[    4.490268] ata3.00: ATA-7: MAXTOR STM3500630AS, 3.AAE, max UDMA/133
[    4.490271] ata3.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    4.551830] usb 5-5: new high speed USB device using ehci_hcd and address 3
[    4.556850] ata3.00: ata_hpa_resize 1: sectors = 976773168, hpa_sectors = 976773168
[    4.556857] ata3.00: configured for UDMA/133
[    4.556871] scsi3 : ata_piix
[    4.700073] usb 5-5: configuration #1 chosen from 1 choice
[    4.726273] ATA: abnormal status 0x7F on port 0x00010177
[    4.726418] scsi 2:0:0:0: Direct-Access     ATA      MAXTOR STM350063 3.AA PQ: 0 ANSI: 5
[    4.737480] SCSI device sda: 976773168 512-byte hdwr sectors (500108 MB)
[    4.737499] sda: Write Protect is off
[    4.737503] sda: Mode Sense: 00 3a 00 00
[    4.737539] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.737633] SCSI device sda: 976773168 512-byte hdwr sectors (500108 MB)
[    4.737652] sda: Write Protect is off
[    4.737656] sda: Mode Sense: 00 3a 00 00
[    4.737689] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.737697]  sda:sr0: scsi3-mmc drive: 40x/40x writer cd/rw xa/form2 cdda tray
[    4.745306] Uniform CD-ROM driver Revision: 3.20
[    4.745378] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    4.754635]  sda1 sda2 < sda5 sda6 sda7 >
[    4.788299] sd 2:0:0:0: Attached scsi disk sda
[    4.793951] sr 1:0:0:0: Attached scsi generic sg0 type 5
[    4.793981] sd 2:0:0:0: Attached scsi generic sg1 type 0
[    4.943472] usb 1-2: new low speed USB device using uhci_hcd and address 4
[    5.128826] usb 1-2: configuration #1 chosen from 1 choice
[    5.131985] usbcore: registered new interface driver libusual
[    5.139023] Initializing USB Mass Storage driver...
[    5.139124] scsi4 : SCSI emulation for USB Mass Storage devices
[    5.139217] usbcore: registered new interface driver usb-storage
[    5.139224] USB Mass Storage support registered.
[    5.139401] usb-storage: device found at 3
[    5.139404] usb-storage: waiting for device to settle before scanning
[    5.157469] usbcore: registered new interface driver hiddev
[    5.170834] input: Logitech USB Receiver as /class/input/input1
[    5.170858] input: USB HID v1.10 Keyboard [Logitech USB Receiver] on usb-0000:00:1d.0-2
[    5.179946] Attempting manual resume
[    5.179950] swsusp: Resume From Partition 8:6
[    5.179951] PM: Checking swsusp image.
[    5.180145] PM: Resume from disk failed.
[    5.200830] input: Logitech USB Receiver as /class/input/input2
[    5.200881] input: USB HID v1.10 Mouse [Logitech USB Receiver] on usb-0000:00:1d.0-2
[    5.200905] usbcore: registered new interface driver usbhid
[    5.200909] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[    5.216289] kjournald starting.  Commit interval 5 seconds
[    5.216309] EXT3-fs: mounted filesystem with ordered data mode.
[   10.134847] usb-storage: device scan complete
[   10.138735] scsi 4:0:0:0: Direct-Access              USB DISK 2.0     PMAP PQ: 0 ANSI: 0 CCS
[   10.151806] SCSI device sdb: 246272 512-byte hdwr sectors (126 MB)
[   10.152454] sdb: Write Protect is off
[   10.152461] sdb: Mode Sense: 23 00 00 00
[   10.152464] sdb: assuming drive cache: write through
[   10.154671] SCSI device sdb: 246272 512-byte hdwr sectors (126 MB)
[   10.155294] sdb: Write Protect is off
[   10.155297] sdb: Mode Sense: 23 00 00 00
[   10.155299] sdb: assuming drive cache: write through
[   10.155302]  sdb: sdb1
[   10.156124] sd 4:0:0:0: Attached scsi removable disk sdb
[   10.156164] sd 4:0:0:0: Attached scsi generic sg2 type 0
[   11.780958] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[   12.179061] NET: Registered protocol family 10
[   12.179216] lo: Disabled Privacy Extensions
[   13.557471] intel_rng: FWH not detected
[   13.589952] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   13.592421] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   13.603049] iTCO_vendor_support: vendor-support=0
[   13.604510] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (11-Nov-2006)
[   13.604614] iTCO_wdt: Found a ICH5 or ICH5R TCO device (Version=1, TCOBASE=0x0860)
[   13.604652] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   13.807106] Linux agpgart interface v0.102 (c) Dave Jones
[   13.809400] agpgart: Detected an Intel 865 Chipset.
[   13.812536] agpgart: AGP aperture is 64M @ 0xf8000000
[   13.863782] input: PC Speaker as /class/input/input3
[   14.083222] parport: PnPBIOS parport detected.
[   14.083265] parport0: PC-style at 0x378, irq 7 [PCSPP]
[   14.307095] ACPI: PCI Interrupt 0000:00:1f.5[B] -> GSI 17 (level, low) -> IRQ 20
[   14.307130] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[   14.626577] intel8x0_measure_ac97_clock: measured 58748 usecs
[   14.626581] intel8x0: clocking to 48000
[   14.774549] fuse init (API version 7.8)
[   14.793147] lp0: using parport0 (interrupt-driven).
[   14.829104] Adding 2048248k swap on /dev/disk/by-uuid/eb9e1c94-eec0-4729-a2cd-b2df784bb3bb.  Priority:-1 extents:1 across:2048248k
[   15.004806] EXT3 FS on sda5, internal journal
[   15.267047] NTFS driver 2.1.28 [Flags: R/O MODULE].
[   15.315113] NTFS volume version 3.1.
[   16.682401] NET: Registered protocol family 17

```

---

### Post by noob12 on 2007-08-08
OK.  Can you try a boot with **acpi=off**?

Here is how to set boot flags.

While booting you'll see a message like 'Grub loading', hit ESC to get the boot menu. The top line is generally your default boot setup and will be selected.

Hit the e key to edit commands. A list of the commands is shown.

Use the down arrow key to go down to the line that starts with kernel. Hit e again. This puts you in a mode where you are editing this line. Your cursor will be typically be after the word splash. Enter a space and **acpi=off** and Enter. This puts you back in the menu. Then press b to boot.

After you boot you can use the command dmesg | grep 'Kernel command' to check whether you added the flag properly or not. If you did, it will be shown there.

This will only last for that one boot. If it works I can give you step by step instructions on how to make it permanent.

---

### Post by durrell on 2007-08-08
That did nothing. And I checked to ensure I did it right, and I did.

I just reinstalled Ubuntu because I wanted to take it off of the extended partition and just make it a primary partition. Still doesn't work. :(

---

### Post by noob12 on 2007-08-08
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/118835](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/118835) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				OK.  I think this is related to the bug reported here:

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/118835](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/118835)

The situation is the same as you have down to specific revs of the card and kernel.  The symptoms sound like what we are seeing.

There's a suggestion there by the person who posted that bug that indicates he was successful getting the card to work at 10mbps by forcing link state using **mii-tool**.  We could try this but it's going to be a substandard solution.

At this point, I'd really suggest you swap in a different card with a different chipset.

You had mentioned you tried another card, configured it manually and had some basic connectivity but had other problems.  You could try to pursue that route. I suspect that in that case you may have forgotten to configure DNS server addresses manually, but not sure.

---

### Post by durrell on 2007-08-08
So let me ask you this..number one, why has it never had any issue with this card before? I've installed Ubuntu probably 4 times on this same machine and never had an issue. The only difference now is I'm running a SATA hard drive instead of an IDE.

Number two, why would OS X be doing the same thing?

And lastly, what if I went back to Gentoo or switched to Fedora instead?

---

### Post by clive_pearce on 2007-08-08
Recently I reloaded windows. I already had ubuntu installed via wubi. When I tried to reinstall ubuntu with wubi, I couldn't get an internet connection.

I used wubi on my other pc connected to the same router & had no problems. 

So for the last couple of days, I have been searching forums about this problems. No ping to my router adding ip addresses etc.

I also couldn't connect to the internet using live cd's of ubuntu & Pclinuxos. 

The network card drivers were mentioned. Recently there was a microsoft update. I went into device manager in windows rolled back the driver, rebooted a live cd, & it worked. 

I had internet access from the live cd. I'm puzzled as to why changing a driver in windows, will affect a Linux live cd.

I'm now going to try to reinstall ubuntu via wubi. I'll let you know how I get on.:)

---

### Post by durrell on 2007-08-08
Hey, that is an idea..I just did a Windows Update to the Realtek driver. I suppose it's definitely worth a shot..I don't see any other ideas.

---

### Post by durrell on 2007-08-08
Well you guys are not going to believe this, but that worked. I rolled back the driver from 6/1/2007 to 7/1/2001 and booted into Ubuntu..and guess what? I'm posting this from Ubuntu. It makes absolutely no sense, but hey..I'm just glad it worked.

Thanks for all the help guys.

---

### Post by clive_pearce on 2007-08-08
Hi, back again, I have just reinstalled Ubuntu with Wubi. It works, I now have internet access through Ubuntu. 

:-\":-\":-\"

---

### Post by durrell on 2007-08-08
As do I. :D It makes no sense, but I'm happy it worked!

---

### Post by noob12 on 2007-08-08
Thanks.  That's very interesting information.  For my notes, were both of you dual booting Windows?  DId it only occur when warm-rebooting from/between Windows and Linux?  Or did you have the same behavior on both cold and warm boots?

Also, one of you might post your findings on the bug I related.  He might have the same dual-boot situation, in which case this might help him.

---

### Post by durrell on 2007-08-08
Mine was from cold boot, warm boot, and Live CD. Nothing worked. I have my partitions setup with Windows, then Ubuntu, then Swap, then OSX86. Neither Ubuntu nor OSX would see the network. Rolling back the driver fixed the problem completely, though. I'll be sure to let him know to try.

Thanks again for all the help, I'm posting this from OSX now that it's finished installing. :)

---

### Post by clive_pearce on 2007-08-09
Hi, I have installed Ubuntu using Wubi. This put Ubuntu in the windows boot.ini file. So it was a cold boot. I also had trouble using a live cd of Ubuntu & live cd of PclinuxOS.

.

---

### Post by durrell on 2007-08-10
Just for a follow up on how bad this driver really is, I was having problems with Windows Vista a few weeks ago. My network connected, but it was in bursts..making anything other than web surfing impossible. Any kind of sustained connection like downloading from the internet or instant messaging, would timeout. I was stumped, so I dumped Vista and went back to XP. I was thinking tonight that my problem in Vista could possibly be related to the same problem I had in Ubuntu and OSX. I reinstalled Vista and tried it, and sure enough..Vista runs like a charm now.

So thanks clive, your suggestion really made my life a lot easier..haha.

---

### Post by Ptero-4 on 2007-08-10
The problem, I think is that M$ rolled a custom made firmware designed to make the card XP-only and it didn't came down until now. When you updated it made it's thing and rendered your nic useless on *NIX (both Canonical's and Apple's variants) and Vista, it got fixed b/c when you rolled it back you restored the nic to it's original OS-agnostic mode.

---

### Post by leadasbestos on 2007-08-12
Thanks guys,

I had this exact same problem and the fix worked beautifully.  Dual boot between WinXP Pro and Ubuntu 7.04 with the RealTek 8100c nic using the 8139too driver (incidentally I too have a SATA drive).  This was really driving me crazy before I found this because both of my partitions were new installs (on new hardware) so I didn't even have the 'just ran a windows update' reference.  

My question is this: How is this possible?  Is the windows driver fiddling some bits on the nic that the linux driver can't touch or something?  Man I shudder to thing that Ptero-4 may be right.

Anyway thank you folks the fix worked.

---

### Post by dangmc on 2007-08-12
this is my first post-just wanted to add my bit-:) same problem with network loss-same fix! I read in another forum (Microsoft) the lastest Realtek nic driver update (winxp pro) v. 5.671.601.2007 somehow causes failure to turn on network card in Linux. Rolled back in  controlpanel>system>hardware devices>network devices>realtek *******>properties>driver rollback--Realtek needs to get their act together! According to Microsoft forum they evidently didn't do enough testing. Iv'e been playing with Ubuntu for about 9 months and I really like it so far--even though i have had a few problems. Thanks to everybody on this forum who has helped me over the past few months





Homemade,Antec p180 case, Antec 480w pws, abit is7 p4 2.8 g. 3g ram
dual boot win XP Pro-Ubuntu 7.0.4

---

### Post by kmartens on 2007-08-13
Hi all,
Same problem with this !@#$%^&^&& Realtek card...also resolved by rolling back the driver.
Find it VERY hard to believe that behaviour this specific is accidental - insufficient testing my left nut!:mad:

---

### Post by durrell on 2007-08-13
Glad to hear the fix worked as good for everyone else as it did for me..clive suggested it, thank him..haha. It saved me a lot of trouble..now I can run Vista with no networking issues as well.

---

### Post by tednyc on 2007-08-15
Just another thanks for figuring this out! Also a warning -- Vista can cause the same problem. I let my Vista Ultimate update the Realtek driver last weekend, suddenly no access from Ubuntu. After seeing this thread, I did a driver rollback, now everything works again. Make me think seriously about deleting the offending OS.

---

### Post by lightninglord2000 on 2007-09-27
I was also experiencing the same problems in my dual boot Windows XP SP2 / Ubuntu 7.04 on my computer with the same NIC chipset. After also doing a rollback of the NIC drivers in WinXP, the NIC in Linux is now working properly! :)

But I still don't get it. How come such a thing work? Does the not-working-up-to-date drivers in WinXP do something in the hardware NIC itself (like change something in the EEPROM, if any)? Does anybody have a logical explanation to this?

---

### Post by noob12 on 2007-09-27
See this thread: [http://ubuntuforums.org/showthread.php?t=538448](http://ubuntuforums.org/showthread.php?t=538448)

---

### Post by HughR on 2007-10-20
This looks a lot like the problem described here: [http://ubuntuforums.org/showthread.php?t=538448](http://ubuntuforums.org/showthread.php?t=538448)

That article explains the problem and suggests two solutions.  Adding a setting to the current MSWindows driver seems less severe than rolling back the driver.

---

