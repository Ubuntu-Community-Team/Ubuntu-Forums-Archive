---
title: "How do I make a routing table fix permanent?"
date: 2006-09-08
forum: Networking &amp; Wireless
---

### Post by xp_newbie on 2006-09-08
I installed Ubuntu on an old 350MHz PII system and while it seems to work (slowly but works), the routing table on boot is such that it does not let the system connect to any computer on the LAN, not to mention the Internet:
> Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 eth0I managed to fix it with a few commands in succession:
> sudo route del -net 0.0.0.0
sudo route add default gw 192.168.0.1Which yields the following routing table:> Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     *               255.255.255.0   U     0      0        0 eth0
default         192.168.0.1     0.0.0.0         UG    0      0        0 eth0And allows me to post this message via this same PC. :)

However, on reboot, this entire change disappears. Obviously, I would like to avoid retyping those commands every time I boot. How do I make these changes permanent?

Thanks!
Alex

---

### Post by tbonius on 2006-09-08
Is your default gateway not automatically assigned?  Is this a static IP address?

You sould simply be able to edit the /etc/network/interfaces file and put in a default gateway for whatever interface you wish.  If your IP address is dynamically assigned .. this should be the responsibility of the DHCP server to hand you out the correct default gateway.

T

---

### Post by xp_newbie on 2006-09-08
Yes, this is a static IP address. I used the GUI to configure it and definitely specified 192.168.0.1 in the "Gateway address" field.

In fact, here is the output of cat /etc/network/interfaces:
> auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.0.9
netmask 255.255.255.0
gateway 192.168.0.1

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

Any idea what's happening?

Thanks!
Alex

---

### Post by tbonius on 2006-09-08
Interesting.  Make sure there are no hidden characters in the text file.  Use vi to edit the file if you have to.  Remove any unecessary entries (like eth1 and wlan0.. etc).

I remember having a similar issue a while back with using another editor.

Also.. from the Ubuntu machine.. ifdown eth0 && ifup eth0

Does netstat -rn timeout trying to find the gateway?

T

---

### Post by xp_newbie on 2006-09-12
I was about to try what you said but then got busy with other things, forgot the system (off) for several days and then... when I turned it again today the problem seemed to have disappeared. Strange.

Now I don't have to type anything to get access to the Internet.

---

