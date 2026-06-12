---
title: "Yet...another no internet thread"
date: 2006-10-02
forum: Networking &amp; Wireless
---

### Post by soopafly on 2006-10-02
Hello all.  Brand new Ubuntu user so please be gentle.  I just purchased a box from a friend with a ASUS A7N266-VM motherboard with onboard ethernet card.  I'm not getting any internet connection.

lspci -v
```

0000:00:04.0 Ethernet controller: nVidia Corporation nForce Ethernet Controller (rev c2)
        Subsystem: ASUSTeK Computer Inc.: Unknown device 0c11
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 185
        Memory at be800000 (32-bit, non-prefetchable) [size=1K]
        I/O ports at d800 [size=8]
        Capabilities: <available only to root>

``` 


lsconfig
```

byuen@byuen-desktop:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:E0:18:75:20:76
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:185 Base address:0xe000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:25 errors:0 dropped:0 overruns:0 frame:0
          TX packets:25 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1656 (1.6 KiB)  TX bytes:1656 (1.6 KiB)

sit0      Link encap:IPv6-in-IPv4
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)


``` 

Any help would be great!! Thanks!!

---

### Post by x64Jimbo on 2006-10-02
well, you have an ethernet card recognized all right. 
Try this to get an IP manually:
sudo dhclient eth0 
(if that doesn't work, try resetting your router and try again)
Then, I recommend installing this:
[http://www.gnome.org/projects/NetworkManager/](http://www.gnome.org/projects/NetworkManager/)
to manage your interfaces automatically.

---

### Post by dmizer on 2006-10-02
looks like you have two active ethernet adapters there.  you'll have to disable one before making the other active.

depending on which one is your onboard ethernet (sit0 is usually pcmcia?), you'll have to do something like:
```
sudo ifdown sit0
```
or eth0 if sit0 is your onboard card.

then try:
```
sudo ifup eth0
```

see if that does the trick.

if you don' t already know, you should be able to determine which is which by doing the following:
```
dmesg | grep eth0
dmesg | grep sit0
```

---

### Post by x64Jimbo on 2006-10-02
sit0 is IPv6, not pcmcia. and it doesn't matter if you have more than one interface active at once. I have about 5 interfaces active sometimes (ath0, eth0, tun0, vmnet1, vmnet8, etc.)
The issue is that the primary interface does not have an IP address, which is what I was trying to help solve with the dhcp command I posted.

---

### Post by dmizer on 2006-10-02
it doesn't matter if you have more than one interface active at once if they are all configured properly.

and, in my experience with hunting down network difficulties, if you're having problems with one of your adapters (if you're using many or not) would be to eliminate potential conflicts with like hardware by disabling secondary devices.

yes, obviously the problem is that there is no ip.  but a card will not pick up an ip if there is conflicting hardware, or if one of the devices is active but not configured correctly.

i was not; however, aware that sit0 was ipv6.  but this could still be interfering with the ability to obtain an ip lease though.

---

### Post by x64Jimbo on 2006-10-02
Ok, so try disabling sit0 first before you try to get an ip...

sudo ifconfig sit0 down
sudo ifconfig eth0 up
sudo dhclient eth0

Then see if it works.

---

### Post by soopafly on 2006-10-02
Thanks guys!  I'll try this once I get home today.

I'm really excited about all this and really glad that there are so many helpful people here

---

### Post by darth_vader_ca on 2006-10-02
worst comes to worst you can statically set your ip on eth0.

cheers

---

### Post by soopafly on 2006-10-02
Hi Jimbo,
I followed your directions, but no luck.  I even connected directly to the modem, bypassing my router.  Here is what I get with sudo dhclient eth0

```

byuen@byuen-desktop:~$ sudo dhclient eth0
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

Listening on LPF/eth0/00:e0:18:75:20:76
Sending on   LPF/eth0/00:e0:18:75:20:76
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 2
No DHCPOFFERS received.
No working leases in persistent database - sleeping.


```

Any ideas?

---

### Post by x64Jimbo on 2006-10-02
If you're on DSL you will need to use a PPPoE program. DSL is similar to dialup in that manner. Much faster, but it still requires a daemon. You might try also setting the PPPoE settings in your router as per your ISP's instructions, then connecting through that so that you get the hardware firewall security and you don't have to run the program on your PC. 
If you're not on DSL, I'm not sure what the problem might be.

---

### Post by soopafly on 2006-10-03
I'm actually running on a cable modem.  I've read several people having problems with the exact motherboard.

I might just go ahead and buy another network card.  Do you suggest any?

---

### Post by x64Jimbo on 2006-10-03
I suggest testing another card before you buy one. If I had to recommend a brand, I've been pretty satisfied with Linksys cards.

---

