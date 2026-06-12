---
title: "Snags with Hardy and Wireless!"
date: 2008-04-25
forum: Networking &amp; Wireless
---

### Post by FokkerCharlie on 2008-04-25
Hello!

I know, I'm not alone in having a problem with my wifi on Hardy, after having it working fine with Gutsy.  This is a clean install after installing a new HDD on my Acer Aspire laptop.

My wireless card is an unbranded; I had it working with NDISWrapper- and this aspect  appears to be OK now:

```
charlie@charlie-laptop:~$ ndiswrapper -l
tnet1130 : driver installed
	device (104C:9066) present (alternate driver: acx)
```

Here's some other stuff that looks OK to me:

```
charlie@charlie-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"CharlesNet"  
          Mode:Managed  Frequency:2.442 GHz  Access Point: 00:16:E3:13:30:B9   
          Bit Rate=54 Mb/s   Tx-Power:10 dBm   Sensitivity=0/3  
          RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:89/100  Signal level:-39 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

Network Manager (which isn't very nice) also detects my network, and others around here.  However, I can't connect to the router:

```
charlie@charlie-laptop:~$ sudo /etc/init.d/networking restart
[sudo] password for charlie: 
 * Reconfiguring network interfaces...                                          There is already a pid file /var/run/dhclient.wlan0.pid with pid 6934
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan0/00:12:0e:47:72:18
Sending on   LPF/wlan0/00:12:0e:47:72:18
Sending on   Socket/fallback
DHCPRELEASE on wlan0 to 192.168.1.1 port 67
RTNETLINK answers: No such process
There is already a pid file /var/run/dhclient.eth0.pid with pid 6994
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:0a:e4:4d:a0:a0
Sending on   LPF/eth0/00:0a:e4:4d:a0:a0
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 192.168.1.1 port 67
ioctl[SIOCSIWPMKSA]: Invalid argument
There is already a pid file /var/run/dhclient.wlan0.pid with pid 134519072
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan0/00:12:0e:47:72:18
Sending on   LPF/wlan0/00:12:0e:47:72:18
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```

I have been trying to get this fixed for 24 hours now- I have disabled ipv6 (I think), tried Wieman's /etc/network/interfaces setup that was working for me under Gutsy, and had a good fiddle in general.

Can anyone point me in the right direction?

PLLLEEEEEAAAAAASSSSEEEEE!

Thanks
Charlie

---

### Post by FokkerCharlie on 2008-04-25
Go on!  Give me a clue.

I am sure that it's something straightforward that I have missed...

Cheers
Charlie

---

### Post by FokkerCharlie on 2008-04-26
OK- so I've been having a good old fiddle, including trying out Wcid.  When I try to connect there, it gets as far as 'Obtaining IP Address', and then stops.

By the way- I'm connecting fine with my Wii, the ethernet works OK, and I am still pulling my hair out because this is very similar to what I had working in Gutsy!

Here's the wcid log:
[http://www.pastebin.ca/998300](http://www.pastebin.ca/998300)

It doesn't seem to matter whether security is on or not- I can't connect with WPA, WEP or no security.

Does that give us a clue?

Thanks in advance for your help.

Charlie

---

### Post by epee on 2008-04-28
I had my wireless working flawlessly with Gutsy - A Belkin USB adapter with the RT73 driver - no problems.

As of a couple of days ago, when I switched to Hardy Heron (incidentally, a bloody heron took all of my goldfish from the pond this weekend. Co-incidence? I don't think so!) and I followed the same setup route, it simply doesn't work.

The interface is recognised and gets signal, but doesn't get an IP address.

BTW - my wireless is WPA, AND I'm on AMD64 running 64-bit - so I guess I'll be waiting forwever for a solution...

---

### Post by ezekielrage on 2008-04-28
I just upgraded to hardy and i might have a clue... or maybe not. I had my broadcom BCM4401 working without ndiswrapper in gutsy. When I upgraded, I had some monitoring enabled on my gnome panel (namely nm-applet and network monitor) and it kept showing the network in nm-applet but kept showing eth1 disconnected in Network monitor. So after fiddling around, i found out that if i restart my laptop and log in as root, the network connection worked fine and on logging back in as a regular user, it continues to work fine... i dunno why that happens... but like they say in all forums out there... it might be a permissions issue.

---

### Post by mlewis-everley on 2008-04-28
Seems I am not alone with this issue. I have a Linksys WMP54G Card (Broadcom Based) which worked perfectly through the restricted drivers app on Gutsy. Now in Hardy it detects the network but the router seems to refuse to provide an IP.

Is it perhaps a problem with the drivers that Hardy is using for the restricted drivers manager? Have they changed at all?

Does anyone know if this is has been reported as a bug? If not its probably worth it :confused:.

Mo

---

### Post by ezekielrage on 2008-05-01
I did some research and found out that hardy uses gvfs-fuse-daemon (whatever that is) to keep track of its network connections... so that legacy applications like terminal can use the network service... gvfs is a replacement for gnome-vfs... 
i seriously do not know what any of this means but it might give another clue...

---

