---
title: "wireless help plea with all the details"
date: 2006-11-26
forum: Networking &amp; Wireless
---

### Post by redvox on 2006-11-26
Hi all,

After many problems with many distros, I went to a place called Linux Cafe yesterday (very cool cafe, if you find yourself in Toronto) and got a copy of Kubuntu 6.10 for my thinkpad 600x.  Everything is great now and working wonderfully, so I thought I push the envelop a try to get a wireless card working.  The card is an SMC 2635.    Here's where things stand:

1.  I believe I have successfully installed the windows driver, using the Windows Wireless Drivers thingy.  It accepted the driver, and now says that the card is present.  However, clicking the Configure Network button on the Windows Wireless Drivers dialog doesn't do anything.  There's some disk access and then nothing.  

2.  Network Settings shows that the card is active.  It is set to activate when the computer starts, and it's set to automatic obtain TCP/IP and DNS, which is right for my home network.

3.  Under KinfoCenter, it shows two listings for network cards: eth0 (my regular ethernet card) and "lo".  "lo" has an ip address of 127.0.0.1, type: loopback, state: up, hardware address of all zeros.  It seems to me that "lo" is some sort of virtual device, and that probably there ought to be another entry for ra0, which I believe is the device name for the wireless card.  ra0 appears under the IRQ settings as IRQ 11.  Several other things are sharing that IRQ, including my ethernet card.  

4.  I thought maybe the issue was that the regular ethernet card was considered default and nothing was managing the choice of network cards, so I installed knetwork-manager. Installation went well and it now appears in my taskbar on start up.  But, it doesn't seem to find the wireless card or the wireless network, or maybe both.  

If anyone has a suggestion on what I might be overlooking, I would appreciate your input.

Thanks.  Looking forward to getting to know Kubuntu,

Thom

---

### Post by redvox on 2006-11-26
wait a sec, now it's working.  All I did was deactive my ethernet card, and now I'm posting this message via wireless connection.  I'm goint to try restarting and see if I can replicate this.  Oddly enough, knetwork-manager still show a wireless connection, just a disconnected wire connection.

---

### Post by redvox on 2006-11-26
Oh that hurts.  I restarted and I'm right back where I started.  I can't seem to replicate my brief wireless success.  I tried deactivating the card again, but that didn't help.

---

### Post by FrodoB on 2006-11-26
Just open a terminal and try:

sudo ifdown wlan0

sudo ifup wlan0

assuming that your interface is called wlan0, change to match what you see when you type iwconfig.

Also to see access points use:

sudo iwlist wlan0 scanning

again change wlan0 to your interface name.

---

### Post by redvox on 2006-11-27
Thanks.  I dunno what it means, but here's what happened when I tried your advice:


root@thinkpad:~# ifconfig
eth0      Link encap:Ethernet  HWaddr 00:50:04:E9:92:1D
          inet addr:192.168.10.3  Bcast:192.168.10.255  Mask:255.255.255.0
          inet6 addr: fe80::250:4ff:fee9:921d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4815 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3835 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:3613356 (3.4 MiB)  TX bytes:583252 (569.5 KiB)
          Interrupt:11 Base address:0x4000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

ra0       Link encap:Ethernet  HWaddr 00:04:E2:D4:9A:49
          inet6 addr: fe80::204:e2ff:fed4:9a49/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:11 Base address:0x8000

root@thinkpad:~# sudo ifdown ra0
There is already a pid file /var/run/dhclient.ra0.pid with pid 4501
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/ra0/00:04:e2:d4:9a:49
Sending on   LPF/ra0/00:04:e2:d4:9a:49
Sending on   Socket/fallback
DHCPRELEASE on ra0 to 192.168.10.1 port 67
root@thinkpad:~# sudo ifup ra0
There is already a pid file /var/run/dhclient.ra0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/ra0/00:04:e2:d4:9a:49
Sending on   LPF/ra0/00:04:e2:d4:9a:49
Sending on   Socket/fallback
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 18
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 17
No DHCPOFFERS received.
No working leases in persistent database - sleeping.


root@thinkpad:~# sudo iwlist ra0 scanning
ra0       Interface doesn't support scanning.

---

### Post by FrodoB on 2006-11-27
Well it is disappointing that iwlist ra0 scanning does not work, that how I view what networks are available.  Maybe someone has some other ideas on this.

---

