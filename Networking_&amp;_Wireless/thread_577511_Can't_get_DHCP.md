---
title: "Can't get DHCP"
date: 2007-10-16
forum: Networking &amp; Wireless
---

### Post by slink on 2007-10-16
This is my ifconfig output:

```
eth0      Link encap:Ethernet  HWaddr   
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:17 Base address:0xb400 

eth0:avah Link encap:Ethernet  HWaddr  
          inet addr:169.254.9.22  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:17 Base address:0xb400 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:32 errors:0 dropped:0 overruns:0 frame:0
          TX packets:32 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2256 (2.2 KiB)  TX bytes:2256 (2.2 KiB)
```

That 169.254.x.x seems to be related with no valid IP adress from DHCP server, I believe. So I've tried to restart my ethernet interface (wired DSL modem):

```
felix@ordinador:~$ sudo ifdown eth0
Password:
RTNETLINK answers: No such process
There is already a pid file /var/run/dhclient.eth0.pid with pid 5188
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/
Listening on LPF/eth0/
Sending on   LPF/eth0/
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 10.127.36.140 port 67


felix@ordinador:~$ sudo ifup eth0
There is already a pid file /var/run/dhclient.eth0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/
Listening on LPF/eth0/
Sending on   LPF/eth0/
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
No DHCPOFFERS received.
No working leases in persistent database - sleeping.


felix@ordinador:~$ sudo dhclient eth0
There is already a pid file /var/run/dhclient.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/
Listening on LPF/eth0/
Sending on   LPF/eth0/
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```

But I still have no internet connection, no IP adress...

Can anyone help me diagnose my problem ?

My provider claims that I have to change the network card, but I can "see" it:

```
felix@ordinador:~$ lspci | grep Ethernet
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 74)
```

Does that make sense that my NIC can be damaged ?

Thanks in advance.

---

### Post by Hero of Time on 2007-10-16
Bring down the interface, then navigate to the location mentioned about the existing PID file. Use sudo to remove the file. Then bring the interface back up manually by using 'sudo ifconfig eth0 up'. Then use sudo dhclient eth0. Check your interfaces file, post the part about eth0 here for review if there are any mistakes in it.

---

### Post by slink on 2007-10-16
Just to confirm. Do you mean...?

```
sudo ifconfig eth0 down

sudo mv var/run/dhclient.eth0.pid var/run/dhclient.eth0.pid.backup

sudo ifconfig eth0 up

sudo dhclient eth0

cat /etc/network/interfaces  (and "grep" the eth0 related lines) 
```

I will post the output in 24 hours. If you can give ANY advice, it will be greatly apreciated.

---

### Post by Hero of Time on 2007-10-16
> **slink said:**
> Just to confirm. Do you mean...?

```
sudo ifconfig eth0 down

sudo mv var/run/dhclient.eth0.pid var/run/dhclient.eth0.pid.backup

sudo ifconfig eth0 up

sudo dhclient eth0

cat /etc/network/interfaces  (and "grep" the eth0 related lines) 
```

I will post the output in 24 hours. If you can give ANY advice, it will be greatly apreciated.
Yes, that is what I mean. Bringing the interface down can be done by ifdown, only to bring the interface up needs ifconfig.

As for your interfaces file, best to open it in gEdit and copy paste the info, or use nano if you are stuck on commandline and retype it.

---

### Post by slink on 2007-10-16
Ok.

---

### Post by Hero of Time on 2007-10-16
And did it work? Did you get an IP address or haven't your tried yet?

---

### Post by slink on 2007-10-16
Not yet, Hero of Time, I'll do it tonight and I'll post tomorrow morning (Central European Time :)). Any comments will be of much help!

---

### Post by noob12 on 2007-10-16
Noticed this earlier
```

RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000 
RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

```

You should probably check that you actually have link state established on the device.
Running **sudo ethtool eth0** will generally tell you.  Check that it says "Link detected: yes".
If not, you should look at that first.

---

### Post by slink on 2007-10-17
I hope I did it right, but no luck...

```
felix@ordinador:~$ sudo ifdown eth0
RTNETLINK answers: No such process
There is already a pid file /var/run/dhclient.eth0.pid with pid 5148
killed old client process, removed PID file
Listening on LPF/eth0/
Sending on   LPF/eth0/
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 10.127.36.140 port 67

felix@ordinador:~$ sudo mv /var/run/dhclient.eth0.pid /var/run/dhclienteth0pidbackup

felix@ordinador:~$ sudo ifconfig eth0 up

felix@ordinador:~$ sudo dhclient eth0
Listening on LPF/eth0/
Sending on   LPF/eth0/
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```

/etc/network/interfaces appears to be so small that I post the whole of it:

```
auto lo
iface lo inet loopback

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp



iface eth0 inet dhcp



auto eth0
```

---

### Post by Hero of Time on 2007-10-17
I noticed in your interfaces file, that thers is no entry for eth0. All it says is 'auto eth0'. Add the following under it:
iface eth0 inet dhcp
That is all I can think of.

---

### Post by slink on 2007-10-17
> You should probably check that you actually have link state established on the device.
Running sudo ethtool eth0 will generally tell you. Check that it says "Link detected: yes".
If not, you should look at that first.

I guess you're right. 

```
sudo ethtool eth0
Password:
Settings for eth0:
        Supported ports: [ TP MII ]
        Supported link modes:   10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
        Supports auto-negotiation: Yes
        Advertised link modes:  10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
        Advertised auto-negotiation: Yes
        Speed: 10Mb/s
        Duplex: Half
        Port: MII
        PHYAD: 1
        Transceiver: internal
        Auto-negotiation: on
        Supports Wake-on: pumbg
        Wake-on: d
        Current message level: 0x00000001 (1)
        Link detected: no
```

But the wire between PC and MODEM is new!

Modem's PC-LINK light is off.

What can I do?

---

### Post by slink on 2007-10-17
> Add the following under it:
iface eth0 inet dhcp
That is all I can think of.

I did it... same thing :sad:

---

### Post by noob12 on 2007-10-17
The ethtool output indicated you have no link state.  That is the equivalent of being disconnected.  You need to solve the link state issue first.  Check your cables and make sure you are plugged into an active port on the other side.

Can you post the output of these commands:
```

lspci -nn

sudo lshw -C network

```

---

### Post by slink on 2007-10-17
I'm not in front of the "damaged" PC, I'll be tonight but I have an [FONT="Courier New"]lspci[/FONT] output right now, does it serve to you?

```
lspci
00:00.0 Host bridge: VIA Technologies, Inc. VT8377 [KT400/KT600 AGP] Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8235 PCI Bridge
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 74)
01:00.0 VGA compatible controller: nVidia Corporation NV18 [GeForce4 MX 440 AGP 8x] (rev a4)
```

```
lshw -C network
WARNING: you should run this program as super-user.

sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: VT6102 [Rhine-II]
       vendor: VIA Technologies, Inc.
       physical id: 12
       bus info: pci@00:12.0
       logical name: eth0
       version: 74
       serial: 
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.4.2 duplex=half latency=32 link=no maxlatency=8 mingnt=3 multicast=yes port=MII speed=10MB/s
       resources: ioport:b400-b4ff iomemory:e5000000-e50000ff irq:17
```


Does it make sense that the MODEM is damaged?

Does it make sense that the NIC is damaged? I think not.

Can I ping my modem if I don't remember its IP ?

---

