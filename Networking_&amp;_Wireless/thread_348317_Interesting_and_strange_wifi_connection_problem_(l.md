---
title: "Interesting and strange wifi connection problem (long)"
date: 2007-01-28
forum: Networking &amp; Wireless
---

### Post by JediDuck on 2007-01-28
Hi all,

First thanks to all the people (you don't know who you are) that have replied to other threads; they've helped me with just about every problem I have.  But I've now got a problem that appears to be so unique I can't seem to find any help or reference to it.

Just to be clear, I have had my Ubuntu box connected wirelessly and surfing fine, so this isn't a "how do I install ndiswrapper" or anything like that cry for help.  This is far more interesting (and annoying).

I'm running 64-bit Edgy on an AMD64.  I'm using the BCM43xx drivers and wpa_supplicant.  My router is a Netgear DG834v3.  As I've said, I have connected to the router before, I've even restarted my computer and had it reconnect on startup.  I figured that all was fine, until I moved the router (which involved unplugging it) several feet away.  Now, my problems really begin..

The first problem is it's a mamoth effort to get the wireless card to get an IP address.  I usually have to plug the wired connection in, connect on that.  Then do "sudo dhclient eth1" to get an IP address for the wireless card.  Sometimes that receives a DHCP offer, other times it doesn't.  The regularity seems to be completely random, however successfully getting the address happens far less often than a failure.  

Second problem is, when eth1 has an IP address, I (more often than not) can't get at anything on the web or indeed the router itself.  ("ping -I eth1 <ip-of-router-or-address>" returns "Destination host unreachable" when "ping -I eth0 <ip-of-router-or-address>" is fine.)

Using the "route" command shows me that the routes are set up correctly for each interface, namely;

```

Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     *               255.255.255.0   U     0      0        0 eth0
192.168.0.0     *               255.255.255.0   U     0      0        0 eth1
default         192.168.0.1     0.0.0.0         UG    0      0        0 eth1
default         192.168.0.1     0.0.0.0         UG    0      0        0 eth0

```

Which I believe to be correct.  iwconfig shows the correct AP and settings (including Link Quality" (sometimes)) for eth1.  "iwlist eth1 scan" shows my network, again with all the details as expected.

As I mentioned, I'm sure it's not a security problem since I can connect, albeit very rarely.

Now it gets really interesting.  On the odd occassion where eth1 (the wireless card) gets an IP address.  I can go to the router admin pages and look at "attached devices".  It shows two entries, each entry has a different IP address, each has the "Device Name" as "unknown", (which is odd), but real puzzle is the MAC address.  For both IP addresses, the MAC address according to the router is the address for the WIRED card.  Does that make sense?

So, according to ifconfig, I have;

[LIST][*]eth0 --> 192.168.0.2 --> aa:bb:cc:dd:ee:ff[*]eth1 --> 192.168.0.3 --> zz:yy:xx:ww:vv:uu[/LIST]

But according to the routers Attach Devices list I have;

[LIST][*]192.168.0.2 --> UNKNOWN --> aa:bb:cc:dd:ee:ff[*]192.168.0.3 --> UNKNOWN --> aa:bb:cc:dd:ee:ff[/LIST]

I've upgraded the router to the latest firmware I could find on the Netgear site (V4.01.20) and I can't find any mention of why this might be happening.

Is this stranger than a box of frogs, or what?

I hope that someone can shed some light on this, I really hope that it's just me being daft and missing something out.  

Many thanks for any help.

---

### Post by hal10000 on 2007-01-28
> default         192.168.0.1     0.0.0.0         UG    0      0        0 eth1
default         192.168.0.1     0.0.0.0         UG    0      0        0 eth0

Why do you have two gateway adresses?
Ususally there MUST be only one, pointing to just ONE ethernet device.

---

### Post by JediDuck on 2007-01-29
Thanks for the response, Hal.

I shall remove the wired route later and see if that fixes the problem.  (I'm currently at work.)

So if you're only supposed to have one route pointing to one network device, does that mean I should only ever have one device up at a time?  Sounds like that might be part of my problem...

---

### Post by JediDuck on 2007-01-29
I'm posting this reply wirelessly.  Yay!

I removed the additional route and destination details for the wired interface and then restarted the networking.  Lo and behold I'm now connected wirelessly and the router is only showing my wireless card as being connected (rather than the oddness it was displaying before.)

Do I risk moving the router to its final destination - hence unplugging it again.  Do I risk rebooting my computer?  Wow, life on the edge is so full of risk...

Thanks again to Hal for the suggestion (I just hope that was the answer and it's not just decided to randomly work, again)

---

