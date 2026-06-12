---
title: "Ubuntu 7.04 -- No Network"
date: 2007-06-21
forum: Networking &amp; Wireless
---

### Post by ad_avis on 2007-06-21
Hello.

I've had Ubuntu 7.04 installed for about a week now, and I still cannot gain access to my home network or the internet.

I'm using a TP-LINK Gigabit Ethernet adapter (TG-3268/TG-3201) which is connected into my home machine (motherboard: ASUS A8V-SE). This then connects to my Belkin Broadband Voice Modem/Router - wireless 4 port (Part # F1PI241EGau).

This machine also runs Windows XP HOME and has no difficulty connecting to the router, login into the router or browsing the web. (I have an ADSL account with IINET)

Here below is the output of some commands I've run on my Ubuntu OS to troubleshoot.

Hope someone can help.

EDIT: I've tried using an static IP address to no avail. Also this is a WIRED connection, not Wireless.

Regards.
Ad Avis

$ ping -c2 10.1.1.1 
PING 10.1.1.1 (10.1.1.1) 56(84) bytes of data. 
From 169.254.7.208 icmp_seq=1 Destination Host Unreachable 
From 169.254.7.208 icmp_seq=2 Destination Host Unreachable 

--- 10.1.1.1 ping statistics --- 
2 packets transmitted, 0 received, +2 errors, 100% packet loss, time 1010ms 
, pipe 2 

zachary@zachary:~$ sudo dhclient 
Password: 
Internet Systems Consortium DHCP Client V3.0.4 
Copyright 2004-2006 Internet Systems Consortium. 
All rights reserved. 
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/) 

Listening on LPF/eth0/00:0a:eb:2f:f2:52 
Sending on   LPF/eth0/00:0a:eb:2f:f2:52 
Sending on   Socket/fallback 
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6 
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14 
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7 
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4 
No DHCPOFFERS received. 
No working leases in persistent database &#8211; sleeping. 

$ ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:0A:EB:2F:F2:52  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:190 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:17196 (16.7 KiB) 
          Interrupt:18 Base address:0x8000 

eth0:avah Link encap:Ethernet  HWaddr 00:0A:EB:2F:F2:52  
          inet addr:169.254.7.208  Bcast:169.254.255.255  Mask:255.255.0.0 
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          Interrupt:18 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:76 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:76 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:6763 (6.6 KiB)  TX bytes:6763 (6.6 KiB) 

$ lspci 
00:00.0 Host bridge: VIA Technologies, Inc. K8T890 Host Bridge 
00:00.1 Host bridge: VIA Technologies, Inc. K8T890 Host Bridge 
00:00.2 Host bridge: VIA Technologies, Inc. K8T890 Host Bridge 
00:00.3 Host bridge: VIA Technologies, Inc. K8T890 Host Bridge 
00:00.4 Host bridge: VIA Technologies, Inc. K8T890 Host Bridge 
00:00.5 PIC: VIA Technologies, Inc. K8T890 I/O APIC Interrupt Controller 
00:00.7 Host bridge: VIA Technologies, Inc. K8T890 Host Bridge 
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI bridge [K8T800/K8T890 South] 
00:02.0 PCI bridge: VIA Technologies, Inc. K8T890 PCI to PCI Bridge Controller 
00:03.0 PCI bridge: VIA Technologies, Inc. K8T890 PCI to PCI Bridge Controller 
00:03.1 PCI bridge: VIA Technologies, Inc. K8T890 PCI to PCI Bridge Controller 
00:03.2 PCI bridge: VIA Technologies, Inc. K8T890 PCI to PCI Bridge Controller 
00:03.3 PCI bridge: VIA Technologies, Inc. K8T890 PCI to PCI Bridge Controller 
00:0d.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8169 Gigabit Ethernet (rev 10) 
00:0f.0 RAID bus controller: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80) 
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06) 
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81) 
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81) 
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81) 
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81) 
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86) 
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South] 
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60) 
00:11.6 Communication controller: VIA Technologies, Inc. AC'97 Modem Controller (rev 80) 
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration 
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map 
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller 
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control 
02:00.0 VGA compatible controller: nVidia Corporation Unknown device 0295 (rev a1) 

$ lshw | grep net 
WARNING: you should run this program as super-user. 
        *-network         
             description: Ethernet interface 
             product: RTL-8169 Gigabit Ethernet 
             capabilities: bus_master cap_list ethernet physical 


$ netstat -rn 
Kernel IP routing table 
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface 
169.254.0.0     0.0.0.0         255.255.0.0     U         0 0          0 eth0 
0.0.0.0.0         0.0.0.0         U         0 0          0 eth0

---

### Post by SoulinEther on 2007-06-21
I've got the same problem as you... perhaps this will help you?

[http://omingo.zorngrid.com/](http://omingo.zorngrid.com/)

---

### Post by ad_avis on 2007-06-21
Tried it but no luck so far.

dhclient fails and still can't ping my router.

---

### Post by darkrose on 2007-06-21
what is the output of

route

cat /etc/network/interfaces

---

### Post by DaBigEd on 2007-06-21
Could it be IPv6 error.

Try this
[http://ubuntuforums.org/archive/index.php/t-6841.html](http://ubuntuforums.org/archive/index.php/t-6841.html)

---

### Post by ad_avis on 2007-06-21
No luck with the ipv6 disabling.

Heres the output of route and /etc/network/interfaces

$ route 
Kernel IP routing table 
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface 
link-local      *               255.255.0.0     U     0      0        0 eth0 
default         *               0.0.0.0         U     1000   0        0 eth0 

$ cat /etc/network/interfaces 
auto lo 
iface lo inet loopback

---

### Post by darkrose on 2007-06-21
Well, your connection is trying to acces the network through eth0, but eth0 is not being set up.
Open /etc/network/interfaces:
gksudo gedit /etc/network/interfaces

and make it look like this:
```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

```

save it, then run:
sudo /etc/init.d/networking restart

and try to ping your router.

---

### Post by ad_avis on 2007-06-22
I'll give it a shot but I don't think thats the problem, my eth0 connection was set to roaming mode at that time.

EDIT: Alright gave it a shot and it didn't work, heres the output as I restarted the network and attempted to ping my router.

$ sudo /etc/init.d/networking restart 
 * Reconfiguring network interfaces...                                          There is already a pid file /var/run/dhclient.eth0.pid with pid 4792 
removed stale PID file 
Internet Systems Consortium DHCP Client V3.0.4 
Copyright 2004-2006 Internet Systems Consortium. 
All rights reserved. 
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/) 

Listening on LPF/eth0/00:0a:eb:2f:f2:52 
Sending on   LPF/eth0/00:0a:eb:2f:f2:52 
Sending on   Socket/fallback 
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3 
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4 
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4 
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5 
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12 
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3 
No DHCPOFFERS received. 
No working leases in persistent database - sleeping. 

$ ping -c2 10.1.1.1 
PING 10.1.1.1 (10.1.1.1) 56(84) bytes of data. 
From 169.254.7.208 icmp_seq=1 Destination Host Unreachable 
From 169.254.7.208 icmp_seq=2 Destination Host Unreachable 

--- 10.1.1.1 ping statistics --- 
2 packets transmitted, 0 received, +2 errors, 100% packet loss, time 1010ms 
, pipe 2

---

### Post by darkrose on 2007-06-22
Ok, no dhcp on eth0, yet you say it works in win, so...

If what you are using is a NIC plugged into a pci slot, and not the one one the motherboard itself (which is how your first post reads), then the interace is most likely eth1 not eth0, so...

stop networking
sudo /etc/init.d/networking stop

edit /etc/network/interfaces
sudo gedit /etc/network/interfaces
and change:
```

auto eth0
iface eth0 inet dhcp

```
to:
```

auto eth1
iface eth1 inet dhcp

```
save it and start networking.
sudo /etc/init.d/networking start

try to ping your router, if you still can't then...

check if eth1 has been assigned an IP address:
ifconfig eth1

if it does, then you might just need to change your routing tabe to get network requests sent down eth1:
sudo route add default eth1

try to ping again.

---

### Post by ad_avis on 2007-06-22
Nope no luck. The onboard network card/device was disabled at BIOS anyway.

Heres the output when I attempted to restart the network after changing the /etc/network/interfaces file.

$ sudo /etc/init.d/networking start 
 * Configuring network interfaces...                                            eth1: ERROR while getting interface flags: No such device 
Internet Systems Consortium DHCP Client V3.0.4 
Copyright 2004-2006 Internet Systems Consortium. 
All rights reserved. 
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/) 

SIOCSIFADDR: No such device 
eth1: ERROR while getting interface flags: No such device 
eth1: ERROR while getting interface flags: No such device 
Bind socket to interface: No such device 
Failed to bring up eth1.

---

### Post by kevdog on 2007-06-22
What does your 
dmesg

say??

---

### Post by TurboPotato on 2007-06-22
I would say...

Trying rebooting your router.  You're getting a 169.x.x.x IP address.  And you say you can't ping the router (because of this reason)  If you are SURE you are getting a link light on the router and you know your hard connection is connected then there has to be something wrong with the router. 

1.) reboot your router
2.) ```
 ifconfig eth0 down
```
3.) ```
 ifconfig eth0 up 
```

See if you can grab an IP address now.  If you can't, then this would indicate that something is actually wrong with the laptop/desktop hardware and its not the router device itself.

---

### Post by giuseppe.dem on 2007-06-23
I have the same problems. After a reboot the connection to the ADSL router is impossible.
In Windows no problem. But in Ubuntu and also in FC7 I have to reset the router in order to get some chance to work on !!!!!
I am really stucked with this problem and I am thinking that Linux flavors are not so good for laptop as for PC (I have a laptop). Or rather, they cannot handle very well complicated interaction with thirdy party hardware like ADSL router.

---

### Post by ad_avis on 2007-06-25
Did you want all the output from dmesg? Cause it's alot.

I checked my routers security log and it seems when I login to Ubuntu it produces the following

06/25/2007  12:31:13 REGISTER[0862620599]: 200 OK for CSeq 4
06/25/2007  12:31:13 REGISTER[0862620599]: 401 Unauthorized for CSeq 3

---

### Post by SyberKowboy on 2007-07-24
I'm having a similar issue. When I go from a wireless network to a wired network I'm not getting DHCP. If I restart the whole system it works fine but if I just restart networking I don't get DHCP. Looking to fix this.  Thanks

---

