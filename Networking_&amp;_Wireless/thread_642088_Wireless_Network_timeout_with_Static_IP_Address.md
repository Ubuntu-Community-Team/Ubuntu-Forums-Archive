---
title: "Wireless Network timeout with Static IP Address"
date: 2007-12-16
forum: Networking &amp; Wireless
---

### Post by yeaitsdark on 2007-12-16
Hey all -

The problem is:  When I assign a static IP to the machine, it seems to go well for a while and then for whatever reason the network simply drops. When I set the network to "Roaming Mode" it locates the network, and everything works perfectly. In order for me to get it back to Static again, I have to play around for a while switching between the two options and eventually it accepts it and works perfectly  with a static IP, that is until it decides it's time to stop working again. 

My solution at the moment is the simple one, being as the machine never goes off line (or rarely does), I'm simply going to allow it go acquire it's IP from the router and simply make all the configuration changes if and when that IP changes (which is very rare) but none the less, if there's a more solid solution I'd be happy to hear it.

Network Card: Linksys WMP54G, using Gutsy.

Thanks in advance.
Also, the direct application of really needing a static IP via wireless is probably not that common, which I very much understand. Wireless is just so easy, fast and cheap these days for most needs.

---

### Post by csat on 2007-12-16
I am on wireless and using static IP.  When we change to static IP we SHOULD go through a console terminal and type sudo /etc/init.d/networking restart <enter>

---

### Post by yeaitsdark on 2007-12-16
Cool that bit of information is helpful in resolving a change, still my real concern is simply why would it just  drop connection, is there some designated interval of time networking wise that it tries to do something, and causes a drop? I would just like to know is all.

---

### Post by yeaitsdark on 2007-12-23
Still the problem persists I've decided to link some information just to see if anyone out there may have a solution. 

The network keep dropping randomly I'm not quite sure of the cause, but a simple 
sudo /etc/init.d/networking restart
fixes it everytime. However, it's most annoying to have to do that because it drops all the people connected to my server until I run the command. At anyrate:

sudo /etc/init.d/networking restart yields:

 * Reconfiguring network interfaces...                                          Ignoring unknown interface eth0=eth0.
Ignoring unknown interface eth1=eth1.
Ignoring unknown interface eth2=eth2.
Ignoring unknown interface ath0=ath0.
Ignoring unknown interface wlan0=wlan0.
ra1: ERROR while getting interface flags: No such device
Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device ra1 ; No such device.
SIOCSIFADDR: No such device
ra1: ERROR while getting interface flags: No such device
SIOCSIFNETMASK: No such device
ra1: ERROR while getting interface flags: No such device
Failed to bring up ra1.
                                                                         [ OK ]
iwconfig:

lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

ra0       IEEE 802.11g  ESSID:"linksys"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:1C:10:04:C4:3E
          Retry min limit:7   RTS thr: off   Fragment thr=2346 B
          Link Signal level=-50 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

ifconfig:

eth0      Link encap:Ethernet  HWaddr 00:17:31:65:70:4B
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:17 Base address:0xe000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:87 errors:0 dropped:0 overruns:0 frame:0
          TX packets:87 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:9908 (9.6 KB)  TX bytes:9908 (9.6 KB)

ra0       Link encap:Ethernet  HWaddr 00:1A:70:A5:10:0C
          inet addr:192.168.1.5  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21a:70ff:fea5:100c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:9817 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12498 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1770894 (1.6 MB)  TX bytes:2093286 (1.9 MB)

wmaster0  Link encap:UNSPEC  HWaddr 00-1A-70-A5-10-0C-00-00-00-00-00-00-00-00-00-00
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

netstat -nr:

Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
192.168.1.0     0.0.0.0         255.255.255.0   U         0 0          0 ra0
169.254.0.0     0.0.0.0         255.255.0.0     U         0 0          0 ra0
0.0.0.0         192.168.1.1     0.0.0.0         UG        0 0          0 ra0

---

### Post by yeaitsdark on 2007-12-23
Also, I think at one point I changed the hardware. I'd really prefer not to reinstall, but I wonder can I just purge these devices and retry or something?

---

