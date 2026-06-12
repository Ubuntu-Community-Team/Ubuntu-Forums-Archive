---
title: "Wireless Internet Sharing Problem"
date: 2005-06-03
forum: Networking &amp; Wireless
---

### Post by Daysleeper on 2005-06-03
Hi,

I am having some issues setting up an ad-hoc wireless link between my desktop (running Ubuntu Hoary) and my laptop (running Windows XP Home).  I really only want to be able to browse the internet from my laptop using my desktops internet connection as a gateway, but I will probably set up SAMBA later for file sharing too.

I am using a Ralink 2400 PCI card in my desktop and have successfully compiled the driver and the interface can be brought up but it has no signal strength or apparent connection.

Here are the details of iwconfig for ra0:

ra0       RT2400PCI  ESSID:"dsfilms"
          Mode:Ad-Hoc  Channel=1  Bit Rate:11 Mb/s
          RTS thr:off   Fragment thr:off
          Encryption key:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

and ifconfig results:

ra0       Link encap:Ethernet  HWaddr 00:08:A1:78:BD:9A
          inet addr:192.168.0.1  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::208:a1ff:fe78:bd9a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:5 Base address:0xc000

and my setup in /etc/network/interfaces

iface ra0 inet static
	wireless-essid dsfilms
	wireless-mode ad-hoc
	address 192.168.0.1
	netmask 255.255.255.0
#	network 192.168.0.255
	broadcast 192.168.0.255

Note:  I have encryption off for testing purposes and intend to activate it once the link is proven to work.

I have my laptop set up with the same ESSID and IP addresses but it can't find my desktop, nor will it find my desktops ESSID while scanning for access points.

Any help would be appreciated.  I get the feeling I am very close, but don't know what to check next.

Thanks!

---

### Post by xristos on 2005-06-03
Did you do an "iwlist ra0 scanning" from desktop ?

---

### Post by Daysleeper on 2005-06-03
The response to

> iwlist ra0 scanning

is

ra0     Interface doesn't support scanning.

---

### Post by Daysleeper on 2005-06-03
Research would indicate that I need to set the card up as a software wireless access point.

I tried:

> man iwconfig

which suggests that I set the mode to Master, but when I type:

> iwconfig iwconfig ra0 mode Master

I get:

Error for wireless request "Set Mode" (8B06) :
    SET failed on device ra0 ; Invalid argument.

Are there any apps which can set up a wireless access point?

---

