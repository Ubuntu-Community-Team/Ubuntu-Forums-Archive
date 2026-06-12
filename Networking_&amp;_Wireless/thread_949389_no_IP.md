---
title: "no IP?"
date: 2008-10-16
forum: Networking &amp; Wireless
---

### Post by jesuisbenjamin on 2008-10-16
Hello Forum,

So far i have never had a problem with network connections and Ubuntu. Lately however something is occurring quite often:

When starting up the connection with the router/internet (i am sharing a connection) doesn't seem to be fully established.

The NM indicates "requesting an ip address" and then nothing, under connection information my IP's etc show only 0's.

My wired network connection's settings are showing "roaming mode", which i tried to change in DHCP, thinking it would be better, but doing so and re-booting, there is no wired connection showing up in the NM... 

When putting the settings back on roaming, it seems that getting an IP address and connect to the net is a matter of luck only...

The last thing seems strange to me. Is this a matter of settings? Or is this some issue with the router?

I am not so literate in connections and networks, not even sure what an IP address really is :D - if you know of any documentation for dummies, one can learn more with - that would be great :)

Thanks

---

### Post by itsjareds on 2008-10-16
Are you sure your computer is actually connecting to your router?

PS: Nice greasy avatar :D

---

### Post by Iowan on 2008-10-16
Check **/etc/network/interfaces** file to see if there's an "auto" line for the interface (eth0?).  If not, you can add these lines to the file: (I like **sudo nano /etc/network/interfaces**) ```

auto eth0
iface eth0 inet dhcp

```Restart networking with **sudo /etc/init.d/networking restart**.

---

### Post by jesuisbenjamin on 2008-10-17
yes i do,
as a matter of fact i do not change anything to the physical connection, start up again and then it works...

---

### Post by jerome1232 on 2008-10-17
Since it's so intermittent, I might take a look at the Ethernet cable, are the ends not making good contact with the wire's inside? Any cuts or missing insulation? Also what happens if you enter this command a few times. Can you post the output?

```
sudo dhclient eth0
```

---

### Post by jesuisbenjamin on 2008-10-17
Iowan, thanks.

currently i read:
 > #auto eth0
#iface eth0 inet dhcp
auto lo
iface lo inet loopback

Could you please confirm i should change it into:
> #auto eth0
#iface eth0 inet dhcp
auto lo
iface lo inet loopback

?

thanks

---

### Post by jesuisbenjamin on 2008-10-17
Hey Jerome,

thanks and here is what i got:

> Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:21:70:a2:04:94
Sending on   LPF/eth0/00:21:70:a2:04:94
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
DHCPOFFER of 192.168.1.39 from 192.168.1.254
DHCPREQUEST of 192.168.1.39 on eth0 to 255.255.255.255 port 67
DHCPACK of 192.168.1.39 from 192.168.1.254
bound to 192.168.1.39 -- renewal in 12126 seconds.


> Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:21:70:a2:04:94
Sending on   LPF/eth0/00:21:70:a2:04:94
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
DHCPOFFER of 192.168.1.39 from 192.168.1.254
DHCPREQUEST of 192.168.1.39 on eth0 to 255.255.255.255 port 67
DHCPACK of 192.168.1.39 from 192.168.1.254
bound to 192.168.1.39 -- renewal in 12126 seconds.


> Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:21:70:a2:04:94
Sending on   LPF/eth0/00:21:70:a2:04:94
Sending on   Socket/fallback
DHCPREQUEST of 192.168.1.39 on eth0 to 255.255.255.255 port 67
DHCPACK of 192.168.1.39 from 192.168.1.254
bound to 192.168.1.39 -- renewal in 12822 seconds.


---

### Post by jerome1232 on 2008-10-17
Meh, of those three times you got a response every time from your router I was hoping one would fail and give us a clue as to why it failed.

Think you could duplicate a failed dhcp request? (maybe you'd have to reboot to get it)

---

### Post by jesuisbenjamin on 2008-10-17
Unfortunately i cannot provoke any issue of this kind, i will keep a note of the command and run it when the issue will occur again. Thanks.

Besides when it happens i see the NM first connecting to the router and then requesting an IP address, this would mean it **is** connected right?

---

### Post by jerome1232 on 2008-10-17
Yes that means the nic senses that a cable is attached and then issued out a dhcp request.  (The waiting for ip address makes it sound like the router isn't responding to the dhcp request)

---

