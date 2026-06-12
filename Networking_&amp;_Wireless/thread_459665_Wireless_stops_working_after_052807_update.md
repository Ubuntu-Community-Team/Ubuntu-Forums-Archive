---
title: "Wireless stops working after 05/28/07 update"
date: 2007-05-30
forum: Networking &amp; Wireless
---

### Post by kiyoshilionz on 2007-05-30
Sorry I can't give you more info in this post, but I can't access the internet from my laptop which is having trouble.

It was a 6.10 -> 7.04 install and wireless has been working like a champ. I have an Intel 2915ABG and it uses ipw2200 drivers.  On 05/29/07, the wireless has stopped working.  Both in Network Manager and with iwconfig I cannot connect to any networks.  I checked DMESG and the system logs and I'm getting the "link is not ready" error message on my wireless interface.

I remember doing a big update that required restarting the computer on 05/28 or 05/29 and I am guessing that that is the cause of all of this, because it was magically working before, and somehow stopped.

I'm using 64-bit WEP encryption with an open key, "iwlist scan" shows all the wireless networks in range properly, and I'm not sure what else I can tell you from here.

It's just not associating with the wireless network i.e. iwconfig says the wireless is "not associated' to any network

---

### Post by kiyoshilionz on 2007-05-30
Also I've been using Linux/command line Unix stuff for a while so don't hesitate to get deep into the system.

---

### Post by stoian on 2007-05-30
Same thing here, after the last update in Feisty Fawn (I think it included a newer kernel) my wireless card stopped working...

I am NOT using ndiswrapper, as my D-Link AirPlus DWL-650+ has been supported at least since Dapper Drake. It worked after upgrading to Feisty, but a day or two ago I suspect some upgrade broke it.

Now I am connected through hard wire to the router :(

Here's the dump from ifconfig -a :

ds@dell:/$ sudo ifconfig -a

eth0      Link encap:Ethernet  HWaddr 00:0D:56:AC:23:4D  
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20d:56ff:feac:234d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:8353 errors:1 dropped:1 overruns:0 frame:0
          TX packets:8393 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:7925203 (7.5 MiB)  TX bytes:1456098 (1.3 MiB)
          Interrupt:7 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:598 errors:0 dropped:0 overruns:0 frame:0
          TX packets:598 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:55054 (53.7 KiB)  TX bytes:55054 (53.7 KiB)

wlan0     Link encap:Ethernet  HWaddr 00:80:C8:07:00:FC  
          inet6 addr: fe80::280:c8ff:fe07:fc/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:53 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:14242 (13.9 KiB)
          Interrupt:11 Base address:0xd000 

wlan0:ava Link encap:Ethernet  HWaddr 00:80:C8:07:00:FC  
          inet addr:169.254.7.18  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:11 Base address:0xd000 

Also, I tried ifdown / ifup commands, but to no result:

ds@dell:/$ sudo ifdown wlan0
RTNETLINK answers: No such process
There is already a pid file /var/run/dhclient.wlan0.pid with pid 14154
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan0/00:80:c8:07:00:fc
Sending on   LPF/wlan0/00:80:c8:07:00:fc
Sending on   Socket/fallback
DHCPRELEASE on wlan0 to 192.168.1.1 port 67

ds@dell:/$ sudo ifup wlan0
There is already a pid file /var/run/dhclient.wlan0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan0/00:80:c8:07:00:fc
Sending on   LPF/wlan0/00:80:c8:07:00:fc
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
No DHCPOFFERS received.
No working leases in persistent database - sleeping.



Please, help!

---

### Post by seppo on 2007-05-31
I can confirm this too. Using ipw2200 with a HP nx8220 laptop. The Wifi card is detected with ipw2200, I can scan networks, but I'm unable to connect to any AP (interface remains unassociated).

This used to work perfectly.

---

### Post by kiyoshilionz on 2007-05-31
Bump

---

### Post by n00bWillingToLearn on 2007-05-31
There was a kernel update recently, have you tried booting from the previous kernel from the GRUB menu?

EDIT: Also, have you filed a bug report?

---

### Post by neptune229 on 2007-05-31
A bug report has been filed in relation to the D-Link DWL-650+. It seems to no longer work with 7.04

I have had the exact same problem, although 7.04 is my first taste of Ubuntu so I am not sure if in my situation it would have worked with 6.10.

---

### Post by kiyoshilionz on 2007-06-01
I restarted the wireless router (DI-524) and now it works.  Weird...

---

### Post by tekdata on 2007-06-01
For me, the 5/28 update got WAP working, whereas it wasn't previously. However, after the round of updates last night, it again, is not. I wish I would have read what the heck those were. :(

bcm4311, both with native bcm43xx and ndiswrapper.

---

### Post by stoian on 2007-06-01
a bug has been logged and confirmed here:
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/117580](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/117580)

i suppose it's work in progress...

---

### Post by cornsnap on 2007-06-02
I had a similar problem so I provided the hex number instead of the ascii key and it worked.  Just a thought. :)

---

### Post by 4ebees on 2007-06-02
> **neptune229 said:**
> A bug report has been filed in relation to the D-Link DWL-650+. It seems to no longer work with 7.04

I have had the exact same problem, although 7.04 is my first taste of Ubuntu so I am not sure if in my situation it would have worked with 6.10.

I have a HP DV14A1p (pretty sure that's the model; I don't have it in front of me) with 6.06 installed.

It uses the ipw2200 also and I have a D-Link DWL650+...

and am having the same problems.

One solution I've found (though I'm using the hex key) is to start Kwifimanager, hit the 'apply' button for whatever settings I need, even though they are already there, then open the network manager and stop the wireless card. Then I restart it and it works... but will not do so all the time if I want to stop and restart it.

This used to work perfectly... in fact it used to connect at start up most of the time.

I hope the bugfix is quick coming. It's very frustrating.

---

### Post by tim.ybarra on 2007-06-05
I am on an HP dv1000 series with a Broadcom 1390.  I too had wireless working, using ndiswrapper, until last update.  As suggested earlier in the post, load old kernel works like a charm.  Hope this gets fixed soon...

---

