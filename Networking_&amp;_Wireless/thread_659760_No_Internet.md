---
title: "No Internet"
date: 2008-01-06
forum: Networking &amp; Wireless
---

### Post by Didad on 2008-01-06
I have been through umpteen forum posts, read several articles and checked the manual settings, etc. etc. It won't ping, connect, it won't do anything. It works perfectly through XP (obviously). I print here the following details of my IP Static address.

auto eth0
iface eth0 inet static
address 192.168.1.10
netmask 255.255.255.0
broadcast 192.168.1.255
network 192.168.1.0
gateway 192.168.1.1

I am at a complete loss as to why it won't connect. In fact it won't read the modem (Netcomm NB5).
ANY help would be appreciated.

---

### Post by ugm6hr on 2008-01-06
> **Didad said:**
> I have been through umpteen forum posts, read several articles and checked the manual settings, etc. etc. It won't ping, connect, it won't do anything. It works perfectly through XP (obviously). I print here the following details of my IP Static address.

auto eth0
iface eth0 inet static
address 192.168.1.10
netmask 255.255.255.0
broadcast 192.168.1.255
network 192.168.1.0
gateway 192.168.1.1

I am at a complete loss as to why it won't connect. In fact it won't read the modem (Netcomm NB5).
ANY help would be appreciated.

You need to give more information if anyone is going to help.
1. How do you connect - wifi / ethernet / router / USB etc.
2. Hardware details.
3. Are you trying to use Network Manager with a static IP?  If so - try Wicd instead (linked below).

The relevant outputs from some or all of these:
```
lspci
lsusb
lshw -C network
```

---

### Post by Predator[23rd] on 2008-01-06
> **Didad said:**
> I am at a complete loss as to why it won't connect. In fact it won't read the modem (Netcomm NB5).

If I am right your NETCOMM NB5 is an ADSL MODEM with build-in ROUTER. in that case your modem is only connected via an ethernet cable to your computer, right? that means your OS will not read your modem and it does not have to.

Can you change your eth0 configuration from static to DHCP by editing */etc/network/interfaces* to be

[I]auto eth0
iface eth0 inet dhcp[/I]

and restart your network with **sudo /etc/init.d/networking restart**. Maybe that will solve the problem...

---

### Post by Didad on 2008-01-22
My Netcomm NB5 is modem only.
Here are results of the various printouts

william@delta:~$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. VT8366/A/7 [Apollo KT266/A/333] (rev 80)
00:01.0 PCI bridge: VIA Technologies, Inc. VT8366/A/7 [Apollo KT266/A/333 AGP]
00:0a.0 Parallel controller: Timedia Technology Co Ltd Unknown device 7268 (rev 01)
00:0c.0 Communication controller: ESS Technology ES2838/2839 SuperLink Modem (rev 01)
00:0d.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon RV100 QY [Radeon 7000/VE]

william@delta:~$ sudo lshw -C network
[sudo] password for william:
  *-network               
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: d
       bus info: pci@0000:00:0d.0
       logical name: eth0
       version: 10
       serial: 00:40:f4:87:a6:91
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full latency=32 link=yes maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=100MB/s

william@delta:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...SIOCADDRT: No such process
Failed to bring up eth0.

william@delta:~$ sudo ifconfig eth0
eth0      Link encap:Ethernet  HWaddr 00:40:F4:87:A6:91  
          inet6 addr: fe80::240:f4ff:fe87:a691/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:16 Base address:0x8000 

william@delta:~$ sudo ifdown eth0
There is already a pid file /var/run/dhclient.eth0.pid with pid 5968
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:40:f4:87:a6:91
Sending on   LPF/eth0/00:40:f4:87:a6:91
Sending on   Socket/fallback
william@delta:~$ sudo ifup eth0
There is already a pid file /var/run/dhclient.eth0.pid with pid 134519120
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:40:f4:87:a6:91
Sending on   LPF/eth0/00:40:f4:87:a6:91
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
sudoDHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
william@delta:~$ sudo dhclient eth0
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:40:f4:87:a6:91
Sending on   LPF/eth0/00:40:f4:87:a6:91
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 18
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

Thanks for the help everyone

---

### Post by ugm6hr on 2008-01-22
```
My Netcomm NB5 is modem only.
```

That doesn't make sense with your fixed IP given.  Your IP looks like a local network IP, so there must be a router involved somewhere.

Post the output from:
```
ifconfig
route -n
```

---

### Post by Didad on 2008-01-22
Sorry, it is a modem router.
william@delta:~$ sudo route -n
[sudo] password for william:
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
169.254.0.0     0.0.0.0         255.255.0.0     U     0      0        0 eth0
0.0.0.0         0.0.0.0         0.0.0.0         U     1000   0        0 eth0

william@delta:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:40:F4:87:A6:91  
          inet6 addr: fe80::240:f4ff:fe87:a691/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:16 Base address:0x8000 

eth0:avah Link encap:Ethernet  HWaddr 00:40:F4:87:A6:91  
          inet addr:169.254.9.43  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:16 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1184 (1.1 KB)  TX bytes:1184 (1.1 KB)

Thanks for the help.

---

### Post by doug-M on 2008-01-22
So when you have the same machine booted to XP what does this command give you?
ipconfig /all

---

### Post by ugm6hr on 2008-01-22
Your problem may just be that your modem expects to have a fixed IP, but Ubuntu (Network Manager) will only work with DHCP.

I would suggest you turn roaming off (in manual config), and put your settings there, and then try rebooting with the ethernet plugged in.


If that doesn't work, can you post a screenshot of the router's setup page?

---

### Post by Didad on 2008-01-23
DHCP has been selected. I've taken a screenshot but how do I paste it?

---

### Post by Didad on 2008-01-23
william@delta:~$ sudo ipconfig /all
[sudo] password for william:
sudo: ipconfig: command not found

---

### Post by Didad on 2008-02-02
Thank you for your disinterest - I'm going back to XP

---

### Post by Didad on 2008-02-04
Well that's it I'm going back to XP - at least I know that that works. Obviously it's too hard to fix. But thanks to those who tried.

---

### Post by ugm6hr on 2008-02-04
> **Didad said:**
> Well that's it I'm going back to XP - at least I know that that works. Obviously it's too hard to fix. But thanks to those who tried.

Sorry.  Saw the last message and figured you'd gone.  Potential problems:
ipv6
ethernet driver

Still interested?  Someone will try and help.

---

### Post by be4truth on 2008-02-04
I have the same problem. Dual Boot with XP and Ubuntu can't ping out. First time that happened to me. I use a static IP. Strange

---

### Post by dying4004 on 2008-02-04
i have the same problem too.   it shud be pretty simple straight forward setup.  just plug in cable in lan...... give static ip and gateway add and browse.   but this simple task has become very complicated in ubuntu. in fedora and mandriva it takes 2 mins to setup.  is there any can shed some light of help on us?? cheerz

---

### Post by be4truth on 2008-02-05
Here is one guess:

[http://manufacturedenvironments.com/2008/01/26_no_network_connection_on_ubuntu_710.html]("http://manufacturedenvironments.com/2008/01/26_no_network_connection_on_ubuntu_710.html")


Maybe for some that will help.

---

