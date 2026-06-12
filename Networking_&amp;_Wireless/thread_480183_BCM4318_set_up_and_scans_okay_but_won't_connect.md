---
title: "BCM4318 set up and scans okay but won't connect"
date: 2007-06-21
forum: Networking &amp; Wireless
---

### Post by SkyFalling on 2007-06-21
I have a Broadcom BCM4318 wireless card and am running Feisty Fawn
7.04 on a Dell D610.  I went the fwcutter route to get the firmware
set up, and got as far as "iwlist eth1 scan" showing a list of
networks, and the same networks showing up in NetworkManager.
However, I'm unable to connect to any of these networks (secure or
not).  In trying to sort this out, I've run into a lot of cases where
manipulating the System/Administration/Network tool, or running
ifdown/ifup, not only doesn't help but actually makes the iwlist scan
stop working, requiring a reboot before it will work again (presumably
there's an easier way than reboot, but I don't know it).

Here, first, is the output from lspci, ifconfig, and iwconfig:

```

 luke@luke-laptop:~$ lspci | grep -i bcm
 02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5751 Gigabit Ethernet PCI Express (rev 01)
 03:03.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
 
 luke@luke-laptop:~$ ifconfig
 eth0      Link encap:Ethernet  HWaddr 00:14:22:C1:6B:02  
           inet addr:172.16.0.116  Bcast:172.16.0.255  Mask:255.255.255.0
           inet6 addr: fe80::214:22ff:fec1:6b02/64 Scope:Link
           UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
           RX packets:685 errors:0 dropped:0 overruns:0 frame:0
           TX packets:653 errors:0 dropped:0 overruns:0 carrier:0
           collisions:0 txqueuelen:1000 
           RX bytes:555548 (542.5 KiB)  TX bytes:95173 (92.9 KiB)
           Interrupt:16 
 
 eth1      Link encap:Ethernet  HWaddr 00:14:A4:43:A5:9A  
           UP BROADCAST MULTICAST  MTU:1500  Metric:1
           RX packets:194 errors:0 dropped:1 overruns:0 frame:0
           TX packets:287 errors:0 dropped:0 overruns:0 carrier:0
           collisions:0 txqueuelen:1000 
           RX bytes:31289 (30.5 KiB)  TX bytes:14832 (14.4 KiB)
           Interrupt:10 Base address:0x8000 
 
 lo        Link encap:Local Loopback  
           inet addr:127.0.0.1  Mask:255.0.0.0
           inet6 addr: ::1/128 Scope:Host
           UP LOOPBACK RUNNING  MTU:16436  Metric:1
           RX packets:4 errors:0 dropped:0 overruns:0 frame:0
           TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
           collisions:0 txqueuelen:0 
           RX bytes:200 (200.0 b)  TX bytes:200 (200.0 b)
 
 luke@luke-laptop:~$ iwconfig
 lo        no wireless extensions.
 
 eth0      no wireless extensions.
 
 eth1      IEEE 802.11b/g  ESSID:off/any  Nickname:"Broadcom 4318"
           Mode:Managed  Frequency=2.484 GHz  Access Point: Invalid   
           Bit Rate=1 Mb/s   Tx-Power=18 dBm   
           RTS thr:off   Fragment thr:off
           Link Quality=0/100  Signal level=-256 dBm  Noise level=-256 dBm
           Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
           Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

Also, here's my /etc/network/interfaces:

```

 auto lo
 iface lo inet loopback
 
 auto eth0
 iface eth0 inet dhcp
 
 auto eth1
 iface eth1 inet dhcp
 wireless-essid littleD

```

Here's what I get when I run iwlist eth1 scan:

```

 luke@luke-laptop:~$ iwlist eth1 scan
 eth1      Scan completed :
           Cell 01 - Address: 00:17:9A:2D:54:54
                     ESSID:"littleD"
                     Protocol:IEEE 802.11bg
                     Mode:Master
                     Channel:11
                     Encryption key:off
                     Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                               11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                               48 Mb/s; 54 Mb/s
                     Quality=100/100  Signal level=-25 dBm  Noise level=-70 dBm
                     Extra: Last beacon: 40ms ago

```

Sometimes I get other networks as well, and they also show up in the
NetworkManager applet, but "littleD" is the one I actually care
about.  It's an unsecured network (though once I get this working I'd
like to turn WPA back on).

I tried running ifdown from this state and got this:

```

 luke@luke-laptop:~$ sudo ifdown eth1
 ifdown: interface eth1 not configured

```

Okay, so it's not configured.  Let's try ifup to configure it:

```

 luke@luke-laptop:~$ sudo ifup eth1
 There is already a pid file /var/run/dhclient.eth1.pid with pid 5501
 removed stale PID file
 Internet Systems Consortium DHCP Client V3.0.4
 Copyright 2004-2006 Internet Systems Consortium.
 All rights reserved.
 For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
 
 Listening on LPF/eth1/00:14:a4:43:a5:9a
 Sending on   LPF/eth1/00:14:a4:43:a5:9a
 Sending on   Socket/fallback
 DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
 DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
 DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 13
 DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
 No DHCPOFFERS received.
 No working leases in persistent database - sleeping.

```

That first line looks suspect -- namely, to me it looks like eth1 is
in a "sort of running" state.  There's a pid for it, but ifdown didn't
think it was configured.  But this could explain why I'm still able to
scan.  Anyway, at this point iwlist eth1 scan still works.  Let's try
ifdown/ifup again now that it's recognizing it as configured:

```

 luke@luke-laptop:~$ sudo ifdown eth1
 There is already a pid file /var/run/dhclient.eth1.pid with pid 6719
 removed stale PID file
 Internet Systems Consortium DHCP Client V3.0.4
 Copyright 2004-2006 Internet Systems Consortium.
 All rights reserved.
 For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
 
 Listening on LPF/eth1/00:14:a4:43:a5:9a
 Sending on   LPF/eth1/00:14:a4:43:a5:9a
 Sending on   Socket/fallback
 DHCPRELEASE on eth1 to 172.16.0.1 port 67

```

Hmmm, stale pid again, this time in ifdown.  Curious...

```

 luke@luke-laptop:~$ sudo ifup eth1
 There is already a pid file /var/run/dhclient.eth1.pid with pid 134993416
 Internet Systems Consortium DHCP Client V3.0.4
 Copyright 2004-2006 Internet Systems Consortium.
 All rights reserved.
 For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
 
 Listening on LPF/eth1/00:14:a4:43:a5:9a
 Sending on   LPF/eth1/00:14:a4:43:a5:9a
 Sending on   Socket/fallback
 DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
 DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
 DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 9
 DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
 No DHCPOFFERS received.
 No working leases in persistent database - sleeping.

```

Whoa... 134993416?  That can't be a valid pid.  Anomaly?  Clue?

Anyway, throughout this whole thing I keep trying to connect to
littleD via the NetworkManager icon.  All it does is time out and
eventually switch back over to the wired eth0.

So, that's about all I've got.  Anyone have a clue what's going on, or
ideas for things to try?  Let me know if there's any more useful
information I can provide.  Many thanks in advance -- I've been trying
off and on for WAY too long to get wireless working on this damn
laptop.

Cheers,
Luke

---

### Post by yj09 on 2007-06-21
same problem with my wireless.. everything look good.. iwlist can scan availeble AP. already try dhcp..also static ip.... hopefully somebody will help us.. maybe it is about key..

sudo dhclient eth1
There is already a pid file /var/run/dhclient.pid with pid 6342
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth1/00:02:8a:99:a7:18
Sending on   LPF/eth1/00:02:8a:99:a7:18
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

here /network/interface
auto eth1
iface eth1 inet static
address 192.168.0.110
netmask 255.255.255.0
gateway 192.168.0.1
wireless-essid ****
wireless-key s:*******

---

### Post by wieman01 on 2007-06-21
I think it has nothing to do with the PID as this message keeps occurring as well:
> killed old client process, removed PID file
If this problem keeps recurring I'd revert to "ndiswrapper".

---

### Post by SkyFalling on 2007-06-21
Hmm, I haven't been getting the "killed PID" message though, just the one about removing the stale PID file.  Messing around a bit, I find that I do get the "killed PID" message if I run dhclient as yj09 did, but only if I have run ifdown more recently than ifup.

If this thread stalls out for other ideas, I'll certainly give ndiswrapper a go -- I actually did have ndiswrapper working on this laptop under Fedora Core 4, quite a while ago, and very briefly.  But hey, working.

---

### Post by wieman01 on 2007-06-21
Guess this one might help:

[http://ubuntuforums.org/showthread.php?t=285809&highlight=howto+4318]("http://ubuntuforums.org/showthread.php?t=285809&highlight=howto+4318")

---

### Post by SkyFalling on 2007-06-22
I wound up going the ndiswrapper route, and it worked great.  Used the python script from this thread: [http://ubuntuforums.org/showthread.php?t=405990](http://ubuntuforums.org/showthread.php?t=405990)

Cheers

---

