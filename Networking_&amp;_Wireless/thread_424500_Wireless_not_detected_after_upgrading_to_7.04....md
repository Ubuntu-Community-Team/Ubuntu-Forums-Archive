---
title: "Wireless not detected after upgrading to 7.04..."
date: 2007-04-26
forum: Networking &amp; Wireless
---

### Post by erechm on 2007-04-26
I'm new to Linux. so go easy.  My desktop wireless worked fine on my previous version of Ubuntu, but since I upgraded to 7.04, wireless card doesn't even show up.  I believe the wireless card is a ZyXEL G-302.  I've been searching the forums, but I can't seem to figure out where to start.  Help!  Thanks!

---

### Post by erechm on 2007-04-26
I figured out an alternative.  I installed "Windows Wireless Drivers" (ndiswrapper) from the ADD/REMOVE APPLICATIONS.  Then I downloaded the windows driver from the ZyXEL website and installed it using Windows Wireless Drivers.  I rebooted and it works like a charm.

Thanks for ALL the imput!  :p  You guys really know how to make a newbie feel comfortable.  ;)

---

### Post by fathefner on 2007-04-26
how do u turn on ur wireless card in ubuntu it was working yesterday then it was shutdown and now it doesnt see my card? And im not sure what to do it there a terminal command i used iwconfig
and it told me
lo no wireless extensions.

eth0 no wireless extensions.

wlan0 IEEE 802.11b+/g+ ESSID:"toho" Nickname:"toho"
Mode:Auto Channel:255 Access Point: Not-Associated
Bit Rate:54 Mb/s Tx-Power=15 dBm Sensitivity=1/3
Retry min limit:7 RTS thrff
Power Managementff
Link Quality:55/100 Signal level:37/100 Noise level:0/100
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0

vmnet8 no wireless extensions.

vmnet1 no wireless extensions.

---

### Post by mattymattysidebyeach on 2007-04-27
greetings,

assuming that "wlan0" is the iface that you are looking to activate, it looks like your system is loading the driver and that your wireless device itself is configured properly.

it may be that the ifconfig component is not getting the info set with iwconfig. 
ifconfig gets info from iwconfig/wireless-tools. it is what manages the different physical connections to the network.

before anything try this in a terminal:
**sudo /etc/init.d/networking restart **

still no?

[LIST]
[*]in a terminal type **ifconfig**
do you see wlan0 among the resulting items?
[/LIST]
 
[INDENT][LIST]
[*]if so try typing **ifup wlan0**
[/LIST][/INDENT]

if that does not work, then the network is not being made aware of the physical wireless-device interface
 

[LIST]
[*]check this ***file* : /etc/network/interfaces**
[/LIST]
it most commonly (does not absolutely have to) contains an entry which describes your wlan0 interface:
[INDENT]*(fyi this is mine, i disabled auto connect - meaning that i have to type **ifup wlan0** - and i'm using dhcp over internet connection)*
[INDENT]### Dlink wireless adapter
# auto wlan0
iface wlan0 inet dhcp[/INDENT]
[/INDENT]


to be sure, there are several apps that could be accessing these files.
not sure what other variables are involved without knowing the contents of "interfaces"


regards

---

