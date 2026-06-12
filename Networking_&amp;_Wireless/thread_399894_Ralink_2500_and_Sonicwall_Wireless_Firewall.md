---
title: "Ralink 2500 and Sonicwall Wireless Firewall"
date: 2007-04-02
forum: Networking &amp; Wireless
---

### Post by dwalraven on 2007-04-02
Your mission, should choose to accept it...  (I hope you will!)

I have a Sonicwall TZ150W(wireless) Firewall for my router working fine in Windohs with the ralink card but I can't get diddly to work in the Ubuntu.  

I'm completely new to Linux, but I think I've got at least a clue.  I've downloaded the RutilT and rt2500 driver and copied nearly every page in this wireless forum before I begin the fry...er, fix my Ubunto network connection.

Before I get started, are there any words of advice from someone who may have fought this battle in the past?

Here are the stats from the ifconfig, iwconfig, and dhclient commands I issued in the terminal:

my:/$ ifconfig
ra0       Link encap:Ethernet  HWaddr 00:50:FC:8C:70:73
          inet addr:192.168.168.2  Bcast:192.168.168.255  Mask:255.255.255.0
          inet6 addr: fe80::250:fcff:fe8c:7073/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:23 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1923 errors:38 dropped:38 overruns:0 carrier:0
          collisions:288 txqueuelen:1000
          RX bytes:7208 (7.0 KiB)  TX bytes:110914 (108.3 KiB)
          Interrupt:185 Base address:0xc000

lo        no wireless extensions.

my:/$ iwconfig
ra0       RT2500 Wireless  ESSID:"DWHome"
          Mode:Managed  Frequency=2.432 GHz  Access Point: 00:06:B1:30:06:8D
          Bit Rate:54 Mb/s   Tx-Power:0 dBm
          RTS thr:off   Fragment thr:off
          Link Quality=58/100  Signal level=-76 dBm  Noise level:-192 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

my:/$ dhclient
Listening on LPF/ra0/00:50:fc:8c:70:73
Sending on   LPF/ra0/00:50:fc:8c:70:73
Sending on   Socket/fallback
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 16
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 12
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

---

### Post by Floppyjoe on 2007-04-02
> my:/$ ifconfig
ra0 Link encap:Ethernet HWaddr 00:50:FC:8C:70:73
inet addr:192.168.168.2 Bcast:192.168.168.255 Mask:255.255.255.0
inet6 addr: fe80::250:fcff:fe8c:7073/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:23 errors:0 dropped:0 overruns:0 frame:0
TX packets:1923 errors:38 dropped:38 overruns:0 carrier:0
collisions:288 txqueuelen:1000
RX bytes:7208 (7.0 KiB) TX bytes:110914 (108.3 KiB)
Interrupt:185 Base address:0xc000


Your Ifconfig here shows that you have an IP address from the router.

---

### Post by dwalraven on 2007-04-02
> **Floppyjoe said:**
> Your Ifconfig here shows that you have an IP address from the router.

I may have cut and pasted that as I was checking to see if setting a static IP would get me out to the net.  I see that IP address, but I still could not get out.

---

### Post by Floppyjoe on 2007-04-02
Do you have just the wireless card activated when you do the sudo dhclient ra0?
Sometimes it helps to turn off the wired connection.

---

### Post by dwalraven on 2007-04-02
I have removed the ethernet card after reading that it might cause a conflict.  

I logged back into ubuntu, deactivated the ra0 connection, logged out, then came back on and reset it through the System, Administration, Network interface to connect to my (now wide open) router.  Still nothing.  This is the current setting:

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:235 errors:0 dropped:0 overruns:0 frame:0
          TX packets:235 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:17484 (17.0 KiB)  TX bytes:17484 (17.0 KiB)

ra0       Link encap:Ethernet  HWaddr 00:50:FC:8C:70:73
          inet6 addr: fe80::250:fcff:fe8c:7073/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6467 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:297482 (290.5 KiB)
          Interrupt:185 Base address:0xc000

---

### Post by dwalraven on 2007-04-02
I'm in.  I love it when the docs work.  Thanks folks!

Now how do I post this as resolved, I wonder? :)

---

### Post by itsdaveperdue on 2007-06-26
What did you do to get this working?

---

