---
title: "D-Link DWL-G630 H/W Ver.:E2 F/W Ver.:5.0 Need Driver and WPA help (preferably GUI)"
date: 2007-06-14
forum: Networking &amp; Wireless
---

### Post by andersmaxx on 2007-06-14
Hi (I posted this at launchpad, but have had no bites... perhaps this wider forum can help?) :confused:

I need a driver for D-Link DWL-G630 Wireless card - H/W Ver.:E2 F/W Ver.:5.0 (Ralink chipset). I also need help to get WPA2-PSK working (it would be nice to have a gui program or applet to do this). I am using Feisty 7.04

Two things:
I am an absolute newbie to Linux, but not afraid of terminal windows. Just please be fairly explicit as to what I need to type.

I do not have any other way of connecting the laptop with Ubuntu to the net, so if I need to download anything, please give me the URLs to do so (I've trawled too many possible fixes that require a working net connection.

Great thanks to the guru out there who will help... [-o<
Max

---

### Post by Seisen on 2007-06-14
I found some drivers here for you card.


[http://doc.gwos.org/index.php/RalinkDrivers]("http://doc.gwos.org/index.php/RalinkDrivers")

---

### Post by andersmaxx on 2007-06-14
Thanks Seisen - that's a start... I'll give those drivers a try, but I'm still way confounded about WPA :shock:
Max

---

### Post by andersmaxx on 2007-06-23
Well, I've been trying for over a week now to get some... ANY support from here and from the official Ubuntu Launchpad (they have just ignored me). (I DO thank Seisen for finding the Ralink Drivers)

I may be one of the few with a D-Link card, but judging from all the posts I've staggered through, plenty of people have RT61 Ralink chipsets. 

I've tried every permutation of advice (well meaning as most of it is) from ndiswrapper, through to trying to jig the driver that comes with Feisty, to SerialMonkey, and the Ralink own linux diver (which doesn't work in Feisty apparently anyway).

Frankly I am really disappointed. Ubuntu is supposed to be 'linux for human beings'. After spending all this time with my head hunched over a terminal windows, trying to crunch through code, I feel like even my 'Second Life' could pass me by if I keep this up.

What I have learned is that linux is definitely NOT free. It has cost me a lot of time and I am no further forward.
If this had happened under Windows, D-Link would have sorted it out for me. Or MS - even if it was for a nominal dollar sum.

Much as I like what I've experience of functioning Ubuntu, and would love to give MS the heave-ho, this just proves a sad point that it's just too damn risky. And that really p*** me, because I wanted to be able to show off this brilliant alternative to others and now I don't even trust it myself. All over a lousy driver.

---

### Post by murmelhunter on 2007-06-26
Well I have a working solution for you, currently I'm using D-Link DWL-G630 Version E2 Firmware 5.0.

I have here a configuration sample for you which allows you to use the card with WPA and dhcp mode.

To get started:

The beginning is like what I found at this entry:
[http://ubuntuforums.org/showthread.php?t=419709&highlight=ethernet](http://ubuntuforums.org/showthread.php?t=419709&highlight=ethernet)

 1) Manual Configuration

After booting the live CD, or after a clean install, you will see Ubuntu has an interface for the network card already configured:

Code:

 ubuntu@ubuntu:~$ ifconfig ra0
ra0 Link encap:Ethernet HWaddr 00:08:A1:A3:C2:B0
inet6 addr: fe80::208:a1ff:fea3:c2b0/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:2248 errors:0 dropped:0 overruns:0 frame:0
TX packets:9630 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:235262 (229.7 KiB) TX bytes:0 (0.0 b)
Interrupt:16

ubuntu@ubuntu:~$ iwconfig
lo no wireless extensions.

eth0 no wireless extensions.

ra0 RT61 Wireless ESSID:"" Nickname:""
Mode:Managed Frequency:2.412 GHz Bit Rate=54 Mb/s
RTS thrff Fragment thrff
Link Quality=0/100 Signal level:-121 dBm Noise level:-111 dBm
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0

However, as ra0 is unconfigured (ESSID:"", etc), the network connection isn't working. We need to configure it manually. Interface configuration is done with 'ifconfig'. Wireless interfaces need additional configuration with 'iwconfig' and 'iwpriv'.


1.1) Disable the ra0 interface

First thing to note is that if the interface is enabled (listed in 'ifconfig' output), your iwconfig/iwpriv changes won't take effect:

Code:

 ubuntu@ubuntu:~$ iwconfig
lo no wireless extensions.

eth0 no wireless extensions.

ra0 RT61 Wireless ESSID:"" Nickname:""
Mode:Managed Frequency:2.412 GHz Bit Rate=54 Mb/s
RTS thrff Fragment thrff
Link Quality=0/100 Signal level:-121 dBm Noise level:-111 dBm
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0

ubuntu@ubuntu:~$ sudo iwconfig ra0 essid WHALENET
ubuntu@ubuntu:~$ iwconfig
lo no wireless extensions.

eth0 no wireless extensions.

ra0 RT61 Wireless ESSID:"" Nickname:""
Mode:Managed Frequency:2.412 GHz Bit Rate=54 Mb/s
RTS thrff Fragment thrff
Link Quality=0/100 Signal level:-121 dBm Noise level:-111 dBm
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0

ubuntu@ubuntu:~$

(note no change to ESSID)

So first bring down the ra0 interface:

Code:

 ubuntu@ubuntu:~$ sudo ifconfig ra0 down
ubuntu@ubuntu:~$ ifconfig
eth0 Link encap:Ethernet HWaddr 00:16:177:AC:C1
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 b) TX bytes:0 (0.0 b)
Interrupt:17 Base address:0x6000

eth0:avah Link encap:Ethernet HWaddr 00:16:177:AC:C1
inet addr:169.254.9.63 Bcast:169.254.255.255 Mask:255.255.0.0
UP BROADCAST MULTICAST MTU:1500 Metric:1
Interrupt:17 Base address:0x6000

lo Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:20 errors:0 dropped:0 overruns:0 frame:0
TX packets:20 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:1432 (1.3 KiB) TX bytes:1432 (1.3 KiB)

ubuntu@ubuntu:~$

Notice that the ra0 interface is gone.


1.2) Configure ra0 with iwconfig and iwpriv.

Now we want to configure the ra0 interface so it connects to the wireless network. I am using WPA with a shared key (WPA PSK), connecting to a network called WHALENET. Your essid and WPAPSK will be different (possibly other settings too, but start with those).

Code:

 ubuntu@ubuntu:~$ sudo iwconfig ra0 essid WHALENET
ubuntu@ubuntu:~$ sudo iwpriv ra0 set AuthMode=WPAPSK
ubuntu@ubuntu:~$ sudo iwpriv ra0 set WPAPSK="My secret WPA key"
ubuntu@ubuntu:~$ sudo iwpriv ra0 set EncrypType=TKIP
ubuntu@ubuntu:~$ iwconfig
lo no wireless extensions.

eth0 no wireless extensions.

ra0 RT61 Wireless ESSID:"WHALENET" Nickname:""
Mode:Managed Frequency:2.462 GHz Access Point: 00:0F:B5:1D:C2:CE
Bit Rate=54 Mb/s
RTS thrff Fragment thrff
Link Quality=85/100 Signal level:-50 dBm Noise level:-79 dBm
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0

ubuntu@ubuntu:~$

Make sure that ESSID has taken the value you set it to. If the interface is working, the 'Link Quality' should be something other than 0/100.

Not working? Then check if the wireless network is even visible with 'iwlist scan':
Code:

 ubuntu@ubuntu:~$ sudo iwlist scan
lo Interface doesn't support scanning.

eth0 Interface doesn't support scanning.

ra0 Scan completed :
Cell 01 - Address: 00:0F:B5:1D:C2:CE
ESSID:"WHALENET"
Mode:Managed
Channel:11
Encryption keyn
Quality:84/100 Signal level:-53 dBm Noise level:-256 dBm

ubuntu@ubuntu:~$


__________________________

So the card is working already now ping the router (if you can ever ping a router, congratulations, the worst is over) ( IP adrres of your router is available in the userguide of your router)

Code:

 ubuntu@ubuntu:~$ ping 192.168.0.1
PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data.
64 bytes from 192.168.0.1: icmp_seq=1 ttl=64 time=9.52 ms
64 bytes from 192.168.0.1: icmp_seq=2 ttl=64 time=1.63 ms
64 bytes from 192.168.0.1: icmp_seq=3 ttl=64 time=1.59 ms

double check now if you ping google

ubuntu@ubuntu:~$ ping google.com

Normally you should see something like this:

PING google.com(64.233.187.99) 56(84) bytes of data.
64 bytes from 192.168.0.1: icmp_seq=1 ttl=64 time=9.52 ms
64 bytes from 192.168.0.1: icmp_seq=2 ttl=64 time=1.63 ms
64 bytes from 192.168.0.1: icmp_seq=3 ttl=64 time=1.59 ms

Now comes the differnce to save the info at the network conf. correctly

 2) Automatic configuration on startup

We want to do all the above steps automatically when Ubuntu starts. The
/etc/init.d/networking script will invoke 'ifup', which in turn runs the
'ifconfig' and 'route' commands we performed manually above. ifup's
configuration file is /etc/network/interfaces.

So edit /etc/network/interfaces:

Code:

ubuntu@ubuntu:~$ sudo gedit /etc/network/interfaces

and at the beginning, add a section like:

Code:

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface

iface wlan0 inet dhcp
        wpa-conf /etc/wpa_supplicant/wpa_supplicant.conf
auto wlan0

iface eth0 inet dhcp

auto eth0

auto ra0

iface ra0 inet dhcp
pre-up iwpriv ra0 set AuthMode=WPAPSK
pre-up iwpriv ra0 set EncrypType=TKIP
pre-up iwconfig ra0 essid WHALENET
pre-up iwpriv ra0 set WPAPSK="My secret WPA key"



Save the file Interface conf file.


Now unplug your lan cable :-) and reboot while your D Link Card is plugged in and you will see your card working by using the WPA.

View points to add :
I have removed the Network manager completely ( can may overule some settings and done no tests with the networkmanager yet.

You can monitor the wfifi conncetion with wifi  radar

If you see in wifi radar an old connection wifi setup please remove it and select the new connection.(it will be listed)

Normally everything should work now like a dream.

I'm using my card since yesteday (WPA with auto DHCP) and done 20 reboot's without any problems.

I hope the solution is clear enough to help you too..

My special thanks goes to amniarix  who gave me with his info at this forum as newbie a clear info understanding how to configure a D-Link G630 wifi card.

Using currently Feisty fawn 7.04 with Beryl correctly configured on a Vaio GRZ 2.4 GHZ 512 MB Ram Ati Raedon mobilty 7500 32 MB and finally the grapic card does direct rendering

---

### Post by andersmaxx on 2007-06-27
Huge thanks for murmelhunter's effort in posting this reply! I'm heartened that someone is willing to help.

As I have a cold right now, I don't think it's the right time to blearily work on but I WILL get onto it and let you know how it went.

Max

---

