---
title: "Wireless: No DHCP/Ping, but can see router"
date: 2007-02-15
forum: Networking &amp; Wireless
---

### Post by GuidoWegener on 2007-02-15
My wireless DSL-router and WLAN-USB-stick are working fine with windows. WIth Ubuntu (Edgy), I had no trouble connecting to the router and the internet when using ethernet cables. But wireless does not work. (Well, it did work one or two times, but I lost connection after 30 minutes and was unable to reproduce the success.)

iwconfig seems to be happy:
> # iwconfig eth2
eth2      802.11g zd1211  ESSID:"Wegener"  
          Mode:Auto  Frequency=2.412 GHz  Access Point: 00:01:E3:08:06:44   
          Bit Rate=1 Mb/s   
          Encryption key:off
          Link Quality=21/100  Signal level=12/100  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

ifconfig:
> # ifconfig eth2
eth2      Protokoll:Ethernet  Hardware Adresse 00:02:72:5A:F3:ED  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

dhcp does not get an answer:
> # dhclient eth2
There is already a pid file /var/run/dhclient.pid with pid 5190
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth2/00:02:72:5a:f3:ed
Sending on   LPF/eth2/00:02:72:5a:f3:ed
Sending on   Socket/fallback
DHCPDISCOVER on eth2 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth2 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth2 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth2 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth2 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth2 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth2 to 255.255.255.255 port 67 interval 18
DHCPDISCOVER on eth2 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth2 to 255.255.255.255 port 67 interval 5
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

I did some experiments with static IPs, but did not succeed either.

I am all out of ideas how to continue.

---

### Post by gradedcheese on 2007-02-15
just to check, try:

```

sudo killall dhclient
sudo ifconfig eth2 up
sudo dhclient eth2

```

---

### Post by GuidoWegener on 2007-02-15
I tried the three commands after shutting down eth1 (cable-bound ethernet to the router). No errors, but dhclient still does not get an answer.

---

### Post by Floppyjoe on 2007-02-15
Make sure only one network interface is enabled if you are not using network-manager applet to connect. If you have installed network-manager then all interfaces must be disabled in System/Administration/Networking.

---

### Post by GuidoWegener on 2007-02-15
I usually enable only one interface (in addition to lo) by doing "ifconfig xxx down". Next time I will disable the interfaces in network-manager, too.

It may be interesting that ethereal does not display any traffic on eth2 when I run dhclient.

Another thing that I should have mentioned in my original post is that I disabled IPv6. Before I did that, ifconfig displayed an IPv6 address for eth2.

---

### Post by Floppyjoe on 2007-02-15
Maybe you have an ipv6 capable router and that is why you could connect properly before?

---

### Post by gradedcheese on 2007-02-15
I think an IPv6 router is still required to support IPv4 clients.  Just to confirm, the wireless radio actually works?  That is, you can do "sudo iwlist eth2 scanning" and you see your access point (and possibly others)?

---

### Post by Floppyjoe on 2007-02-15
If you are not using network-manager it might help us to see your /etc/network/interfaces file.
```
sudo gedit /etc/network/interfaces
```
I think you need:
```
wireless-essid YourEssid
wireless-channel 6
wireless-mode managed
```
Where you substitute your routers channel.

---

### Post by GuidoWegener on 2007-02-15
Yes, I can see the router when scanning on eth2. The router even displays the MAC address of my wlan stick in its configuration interface.

I disabled IPv6 only after having no success, hoping to simplify matters. Well, there seems to be no difference with or without it. And I do not think that my router is IPv6-enabled at all.

I will post etc/network/interfaces an scan results as soon as I get back home to my computer.

---

### Post by marx2k on 2007-02-15
Im having the same exact problem. The router is the one at school and the only difference is that the Mode for the router is "Master"

I hope we can find an answer to our problem!

---

### Post by GuidoWegener on 2007-02-15
Yay! I am actually posting this totally wireless. :wink:

I hope that it's not a one time affair.

The biggest change I made was to disable all interfaces in the network-manager, and disable them slowly. Then I edited /etc/network/interfaces to this:
> auto lo
iface lo inet loopback

#iface eth0 inet dhcp

#iface eth1 inet dhcp

iface eth2 inet dhcp
wireless-essid Wegener
wireless-channel 3
wireless-mode managed

Up to now I never commented out eth0 and eth1. I just did ifdown eth1. This may be a second diffence between broken and running setup.

After that, I tried to connect:
ifconfig eth2 down
ifconfig eth2 up
dhclient eth2

Bingo!

Thank you all for your support and fresh ideas! And next weekend I will tackle encryption...

---

### Post by GuidoWegener on 2007-02-16
Oops, I tried again this morning and nothing worked. eth1 (ethernet) and eth2 (wireless) did not respond. Rebooting did not help, so I gave up and went to work.

Now that I am home again I booted again and everything works ok, even though I had to start the connections by hand. Strange...

I think that I saw some error messages on boot up this morning. Something like "USB 5-3 does not accept address 8 error -110".

I will try to gather more information and post my experiences during the next few days, to help other users with similar problems.

---

### Post by wej1971 on 2007-02-17
I also have the same problem, and while I can occasionally connect, it never stays up for long and after dying it doesn't usually reconnect.

I don't understand how, with the wifi device working and the access point visible, the connection doesn't work and the dhcpdiscover fails!

---

### Post by Cloudane on 2007-02-17
Add me to the long list of people having this problem.  Something seems to be seriously broken with wireless networking in Ubuntu (if not in the Linux kernel itself) and nobody seems to know how to fix it.

Very close to handing my money over to Microsoft in frustration.  If I could just get wireless networking, *decent* results out of my camera (not the flat boring results out of Bibble or the freebies) and WoW going I'd be happy.  Seemingly this is a huge thing to ask of Linux.

---

### Post by gradedcheese on 2007-02-17
I have some development experience in this area, so I can shine a little light on the topic if you wish:

There's nothing really 'wrong' with wireless in Linux, it just depends on drivers (as you would expect).  However there is a major architecture change in progress that will make these drivers easier to write and support (and will hopefully also improve the vendor support in the long run).  That said, it all depends on your card's chipset.  I have an Atheros chipset that happens to be fully supported by a pretty solid driver.  My wireless works perfectly (in fact, better than a Windows PC with Belkin's drivers as I've noticed).  On the other hand, if you are using something like ndiswrapper, you have to realize that your wireless is supported by a pretty dirty 'hack' and you can't expect it to work particularly well: you are loading a Windows binary driver via a wrapper that translates API calls.  This is clever, but miles behind supportable compared to an open source kernel module.

I'm not in the position to tell you "hey, buy a different card", but that will indeed solve your problems.  You can look at this as a bad thing, or you can look at it as "I'll only use hardware supported by high-quality drivers, then I will evaluate the OS fairly".  If you do that, you'll find that the OS is quiet good.

Why does wireless suck in Linux?
- the FCC has many rules about what a WiFi card can and cannot do.  If these rules are violated because of an accidental change in the driver, the manufacturer (not the driver maker) is in trouble.  This, I think, has never happened, but it worries the vendors constantly.  This is different from Ethernet, for example, where there's no radio for the PHY.  As a result, chipset makers are very hard to work with.
- wireless is still considered relatively hot intellectual properly, so chipset makers are very secretive (compare, again, with Ethernet which is now trivial to implement).  Many drivers are reverse-engineered as a result, this is very hard to do.  Intel is a reasonably good example of a chipset maker that 'gets it', while Broadcom and Marvell are bad examples.
- there are actually two types of WiFi chipsets (hardware and software MAC).  This makes a huge difference in the driver architecture and also affects the FCC risk significantly.  The kernel community is currently addressing this.  In a software MAC, the driver actually implements most of the stuff that the FCC is worried about, right in the driver source code.  There has to be a way for the hardware or firmware on the card to ensure that the rules aren't violated, and so on.

---

