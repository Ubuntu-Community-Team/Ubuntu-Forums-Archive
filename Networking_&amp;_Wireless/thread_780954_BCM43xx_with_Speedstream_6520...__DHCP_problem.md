---
title: "BCM43xx with Speedstream 6520...  DHCP problem ?"
date: 2008-05-03
forum: Networking &amp; Wireless
---

### Post by joellord on 2008-05-03
Hi everybody,
  I'm having a hard time with my network.  I'm using Ubuntu 8.04.  It used to work with 7.10 but it stopped working when I installed 8.04 Beta a few weeks ago.  For some reason, my other computer is using Mythbuntu 8.04 Beta and the wireless was working on it....  until this morning.

Now my laptop has a BCM 43xx card and I use the restricted drivers for it.  The light is on, I see all the networks of my neighbors but I can't connect to my network.

It seems like I simply can't get an address from my DHCP so I thought it could be my router (Speedstream 6520).  The weird thing is, my girlfriend is running Windows on her laptop and when she came in this morning, she connected to my network, as usual.

Any help would be greatly appreciated,
Thanks !

Joel Lord

EDIT:
Ok, for some reason, my Mythbuntu machine is now working again...  But my laptop still isn't working.  I just noticed that a box saying "Passphrase Required by Wireless Network" keeps popping up.  I enter the passphrase (I'm sure it's the right one) and click on Connect...  and it pops up again.

EDIT:
Another update, when I try to manually start my card using 
sudo ifup wlan0 
here is what I get:
```

joel@joel-laptop:~$ sudo ifup wlan0
There is already a pid file /var/run/dhclient.wlan0.pid with pid 134519072
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:14:a4:43:45:9a
Sending on   LPF/wlan0/00:14:a4:43:45:9a
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 21
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 2
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
joel@joel-laptop:~$ 


```

---

### Post by joellord on 2008-05-03
Ok, it now works !  Not sure how I did but it works ! 

Here is something to try if you have the same kind of problem.  I change the wired network to "Roaming Mode" so that might be it...

Thanks for reading everyone ! ;)

---

### Post by koma77 on 2008-05-04
Did you really change the wired network to roaming? Or the wireless?

---

