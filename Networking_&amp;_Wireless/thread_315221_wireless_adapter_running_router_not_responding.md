---
title: "wireless adapter running router not responding"
date: 2006-12-08
forum: Networking &amp; Wireless
---

### Post by albesan on 2006-12-08
hello team,

I installed te belkin wireless usb adapter painlesly thanks to [this great how to wireless]("https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_4000_%28ZyDas_zd1211b_driver%29?highlight=%28WifiDocs%2FDevice%29")by FrodoB, thanks FrodoB.

Now the problem is that for some reason beyon my little understanding it doesn't get on with the wireless router.

I thought there wouldn't be a problem since both the router and the adapter are belkin.the adapter is the Belkin F5D7050 ver 4000 (ZyDas zd1211b driver),and the router is the belkin F5D7230-4 6000.
I tried disabling encryption, disabling the firewall, enabling an open access point, dynamic and static ip with no luck.

I was following a similar thread dealt by Trublemaker but I got stuck since the output on my system was different to that of the other person with the problem .

Anyhow, here is the output:

iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     802.11b/g NIC  ESSID:"mynetwork"
          Mode:Managed  Frequency=2.462 GHz  Access Point: Not-Associated
          Bit Rate:11 Mb/s
          Retry:off   RTS thr=2432 B   Fragment thr:off
          Power Management:off
          Link Quality=96/100  Signal level=30/100  Noise level=0/100
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:77
          Tx excessive retries:99840  Invalid misc:0   Missed beacon:0

 iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: XX:XX:XX:XX:XX:XX
                    ESSID:"little tomato"
                    Mode:Master
                    Frequency=2.462 GHz (Channel 11)
                    Extra:SignalStrength=38%,LinkQuality:96%
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
 sudo dhclient wlan0
Password:
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/wlan0/XX:XX:XX:XX:XX:XX
Sending on   LPF/wlan0/XX:XX:XX:XX:XX:XX
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 17
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
No DHCPOFFERS received.
No working leases in persistent database - sleeping.


 ifconfig
lo        Link encap:Local Loopback
          inet addr:XXX.X.X.X  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:172 (172.0 b)  TX bytes:172 (172.0 b)

wlan0     Link encap:Ethernet  HWaddr XX:XX:XX:XX:XX:XX
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:86 dropped:0 overruns:0 frame:86
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

So yeah, "Not associated"... can't get 'em to be friends...

Anyone finds this easy to solve? any help would be great.
thanks


a.

---

### Post by FrodoB on 2006-12-08
Very nice outputs, thanks for providing good information.

I am a little confused, is you access point's network called:

"mynetwork"

or

"little tomato"

I think that you need to fix your ESSID in your interfaces file perhaps? My bet is that it should be:

auto wlan1
iface wlan1 inet dhcp
pre-up ifconfig wlan1 up
wireless-essid little tomato
wireless-key xxxxxxxxxxxxxxxxxxxxxxx

Then try:

sudo ifdown wlan0

sudo ifup wlan0

---

### Post by albesan on 2006-12-08
> **FrodoB said:**
> Very nice outputs, thanks for providing good information.

I am a little confused, is you access point's network called:

"mynetwork"

or

"little tomato"

I think that you need to fix your ESSID in your interfaces file perhaps? My bet is that it should be:

auto wlan1
iface wlan1 inet dhcp
pre-up ifconfig wlan1 up
wireless-essid little tomato
wireless-key xxxxxxxxxxxxxxxxxxxxxxx

Then try:

sudo ifdown wlan0

sudo ifup wlan0
hey, thanks for the reply and the how to...

I'm a bit confused, in the code you wrote wlan1, is that right?
I tried and didn't really work:

sudo ifup wlan1
wlan1: ERROR while getting interface flags: No such device

So I tried wlan0 instead and I got this:

sudo ifdown wlan0
/etc/network/interfaces:32: interface wlan0 declared allow-auto twice
ifdown: couldn't read interfaces file "/etc/network/interfaces"

My /etc/network/interfaces looks like this:


# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface


iface eth0 inet dhcp

# wireless usb adapter

auto wlan0
iface wlan0 inet dhcp
pre-up ifconfig wlan0 up
wireless-essid little tomato

I'm trying to get it to work unencrypted, so I left out the wireless-key.
One questio though, what do I type in the wireless-key entry? Not the key, is it?

Well, thanks for the help again...

a.

ps. yes, yes, little tomato ;)

---

### Post by FrodoB on 2006-12-08
I just used the example I had available. Yours is wlan0.

sudo ifdown wlan0
/etc/network/interfaces:32: interface wlan0 declared allow-auto twice
ifdown: couldn't read interfaces file "/etc/network/interfaces"


This seems to say that you have two instances of:

auto wlan0

in your file.

Delete one of them and retry.

---

### Post by albesan on 2006-12-09
Doh! did not look all the way down the file...
Anyway I tried it and got this:

 sudo ifup wlan0
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/wlan0/XX:XX:XX:XX:XX:XX
Sending on   LPF/wlan0/XX:XX:XX:XX:XX:XX
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
DHCPOFFER from 192.168.2.1
DHCPREQUEST on wlan0 to 255.255.255.255 port 67
DHCPREQUEST on wlan0 to 255.255.255.255 port 67
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 16
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
postconf: fatal: open /etc/postfix/main.cf: No such file or directory

$ sudo ifdown wlan0
postconf: fatal: open /etc/postfix/main.cf: No such file or directory
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/wlan0/XX:XX:XX:XX:XX:XX
Sending on   LPF/wlan0/XX:XX:XX:XX:XX:XX
Sending on   Socket/fallback


At least this time it found one dhcp offer...

hmm... what now? 

thanks. 

a.

---

### Post by albesan on 2006-12-10
bump

---

### Post by albesan on 2006-12-11
hello, it's me again.
I'm sorry to be a pain in the neck but I was wondering if someone could help me figure out the avobe described issue which still remains unsolved.

any help will be usefull, thanks

a.

---

### Post by FrodoB on 2006-12-12
Well it looks like you are closer:

DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
DHCPOFFER from 192.168.2.1
DHCPREQUEST on wlan0 to 255.255.255.255 port 67
DHCPREQUEST on wlan0 to 255.255.255.255 port 67
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 16
No DHCPOFFERS received.

We had a offer, but it did not take for some reason.  Are you close enough to your access point? What does the signal look like? See iwconfig.

---

### Post by albesan on 2006-12-12
hey FrodoB, thanks for the reply.

today iwconfig says:

wlan0     802.11b/g NIC  ESSID:"little tomato"
          Mode:Managed  Frequency=2.462 GHz  Access Point: Not-Associated
          Bit Rate:1 Mb/s
          Retry:off   RTS thr=2432 B   Fragment thr:off
          Power Management:off
          Link Quality=72/100  Signal level=38/100  Noise level=0/100
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:260  Invalid misc:0   Missed beacon:0

So yeah, "not associated".
I installed "wi-fi radar" and the signal is at it's fullest, I have no problem connecting on this same network on this same computer on Mac OSX.

todays output for other commands:

wlan0     Scan completed :
          Cell 01 - Address: XX:XX:XX:XX:XX:XX
                    ESSID:"little tomato"
                    Mode:Master
                    Frequency=2.462 GHz (Channel 11)
                    Extra:SignalStrength=30%,LinkQuality:48%
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100


 sudo ifdown -a
postconf: fatal: open /etc/postfix/main.cf: No such file or directory
postconf: fatal: open /etc/postfix/main.cf: No such file or directory
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/wlan0/XX:XX:XX:XX:XX:XX
Sending on   LPF/wlan0/XX:XX:XX:XX:XX:XX
Sending on   Socket/fallback
DHCPRELEASE on wlan0 to 192.168.2.1 port 67
send_packet: Network is unreachable
send_packet: please consult README file regarding broadcast address.

$ sudo ifup -a
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)


Listening on LPF/wlan0/XX:XX:XX:XX:XX:XX
Sending on   LPF/wlan0/XX:XX:XX:XX:XX:XX
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
postconf: fatal: open /etc/postfix/main.cf: No such file or directory

I'm way over my head, I thought I was following some kind of logic but I'm totally lost.


I look forward hearing from you or anyone who can make sense of this one.

a.

---

### Post by FrodoB on 2006-12-12
What are the present contents of /etc/network/interfaces

---

### Post by albesan on 2006-12-13
hello, thanks for the reply, I've got a fresh batch of output:

/etc/network/interfaces:

# and how to activate them. For more information, see interfaces(5).

# The loopback network interface

auto lo
iface lo inet loopback



# The primary network interface

auto eth0
iface eth0 inet dhcp



# wireless usb adapter

auto wlan0
iface wlan0 inet dhcp
pre-up ifconfig wlan0 up
wireless-essid little tomato
wireless-key XXXXXXXXXXX


iwlist scanning
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: XX:XX:XX:XX:XX:XX
                    ESSID:"little tomato"
                    Mode:Master
                    Frequency=2.462 GHz (Channel 11)
                    Extra:SignalStrength=38%,LinkQuality:96%
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100


$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     802.11b/g NIC  ESSID:"little tomato"
          Mode:Managed  Frequency=2.462 GHz  Access Point: XX:XX:XX:XX:XX:XX
          Bit Rate:11 Mb/s
          Retry:off   RTS thr=2432 B   Fragment thr:off
          Power Management:off
          Link Quality=84/100  Signal level=49/100  Noise level=0/100
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:18
          Tx excessive retries:263149  Invalid misc:0   Missed beacon:0

alberto@copitux:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr XX:XX:XX:XX:XX:XX
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:41 Base address:0xf800

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:172 (172.0 b)  TX bytes:172 (172.0 b)

wlan0     Link encap:Ethernet  HWaddr XX:XX:XX:XX:XX:XX
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:18 dropped:0 overruns:0 frame:18
          TX packets:7 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:2352 (2.2 KiB)

sudo ifdown wlan0
postconf: fatal: open /etc/postfix/main.cf: No such file or directory
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/wlan0/XX:XX:XX:XX:XX:XX
Sending on   LPF/wlan0/XX:XX:XX:XX:XX:XX
Sending on   Socket/fallback
DHCPRELEASE on wlan0 to 192.168.2.1 port 67
send_packet: Network is unreachable
send_packet: please consult README file regarding broadcast address.

$ sudo ifup wlan0
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/wlan0/XX:XX:XX:XX:XX:XX
Sending on   LPF/wlan0/XX:XX:XX:XX:XX:XX
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 21
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 17
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
postconf: fatal: open /etc/postfix/main.cf: No such file or directory


that was today's output, thanks again for your help.


a.

---

### Post by FrodoB on 2006-12-13
I am completely puzzled, I have installed this thing myself multiple times and tried WEP, removing WEP, and it always just works.

If you are are not using 128bit WEP try that as that is what most drivers seem to get tested at these days.

Here are my access point settings for you to check yours against:

The ViewSonic uses WEP and the Linksys WPA-PSK, though they both work in either mode.

ViewSonic WAPR-100 Wireless Access Point Settings: (Linksys WRT54GL differences noted)


Authentication Type: Open System

Basic Rate: All  (Linksys only)
      
Transmission Rates: Auto (All for my Linksys)

Frame Burst: Disable  (Only on my Linksys)

RTS/CTS: Disable 

CTS Protection Mode : Disable (Linksys only)

Beacon Interval: 100 ms

RTS Threshold: 2346

Fragmentation Threshold: 2346 (2347 on my Linksys)

DTIM Interval: 3

Xpress mode: Disable   (Maybe this is the same as preamble on this router?)

Access Control: Disable

Wireless Mode 802.11b 11Mbps

Channel: 11         (Channel 1 for Linksys)

SSID Broadcast: Disable  (You could try enabling this to see if there is any difference.)

SecureEasySetup : Disable    (Linksys only)

Preamble: Long   (Short seems to trouble some devices)

---

### Post by albesan on 2006-12-13
FrodoB my man!

got it working, using it to write this.

I think it might have had to do with the 64 bit encryption.
Once I changed to 128 it worked.

But mainly I think this particular router is a piece of crap.

Anyway, thanks so much for your help :)

---

### Post by FrodoB on 2006-12-13
A lot of wireless routers have this problem anymore.  64bit WEP has become kind of rare. 

Also it could be that the problem is in the Linux driver's use of 64bit WEP I suppose, I have never tried it.

What kind of wireless router do you have?

---

### Post by albesan on 2006-12-14
hello,

the router is the belkin F5D7230-4 6000. In the search for the answer to this problem I stumbled upon several accounts from people cursing belkin and this router model in particular.
I can't really complain, cost me £3 on ebay.

---

### Post by FrodoB on 2006-12-14
Well that was a good deal, considering that it works now.

---

### Post by garlicsalt2 on 2006-12-21
#albesan: By any chance, does the "6000" mean hardware revision 6000? By any chance, is it actually a hardware version less than 1444? Look on the label on the bottom of the unit. If the revision is less than 1444, then it should run openwrt. [http://openwrt.org/](http://openwrt.org/)

I used to have that router. Yeah, it was full of problems. I had so many problems with it, that I gave it away. That was before I discovered OpenWrt. :mad: 

I love openwrt. A great many routers actually run an embedded version of Linux!! As such, the source code has been released for these models. This router has 4mb flash & 16mb ram for the pre-1444 models. The newer ones have only 2mb flash & 8mb ram. 2mb is just not enough flash to run Linux. If this interests anyone here, checkout the table of supported hardware, here:
[Supported Hardware]("http://wiki.openwrt.org/TableOfHardware")

With a compatible router, and enough knowledge of Linux, your wireless router can be a samba client/server, a kismet sniffer, a tor node, an OpenVPN server, FreeRADIUS server, gmediaserver, bittorrent tracker, pptp client/server, l2tp client/server, and much, much more

--Aaron :cool:

---

### Post by albesan on 2006-12-21
hey Aaron,

openwrt sounds good to me. The hardware version is 6000ea though....

Thnaks for the info, I'll have it in mind when I give this router away ;)

a.

---

