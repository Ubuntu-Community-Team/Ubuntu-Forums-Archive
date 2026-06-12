---
title: "Disable my wireless adapter?"
date: 2009-03-23
forum: New to Ubuntu
---

### Post by aquascrotum on 2009-03-23
I have a wired ethernet connection to my router but also have my wireless configured to connect to the same router - I tend to use the wired connection.

In Windows I was able to simply enable/disable the wireless network adapter as and when required.

When I untick the "Enable Wireless" checkbox in Ubuntu 8.10, this setting re-sets every time I restart (ie the computer reconnects to the wireless again at startup).

How can I semi-permanently disable my wireless card/connection, whilst not making it a huge task to re-enable when the need arises?

---

### Post by nandemonai on 2009-03-23
> **aquascrotum said:**
> I have a wired ethernet connection to my router but also have my wireless configured to connect to the same router - I tend to use the wired connection.

In Windows I was able to simply enable/disable the wireless network adapter as and when required.

When I untick the "Enable Wireless" checkbox in Ubuntu 8.10, this setting re-sets every time I restart (ie the computer reconnects to the wireless again at startup).

How can I semi-permanently disable my wireless card/connection, whilst not making it a huge task to re-enable when the need arises?

Edit the connection configuration in Network Manager and un-check 'Connect Automatically'.

System -> Prefs -> Network configuration

---

### Post by sudo make sandwich on 2009-03-23
Are you only wanting to do this when you are plugged into the wired connection?

If so, it isn't really necessary. When Ubuntu detects multiple interfaces, it should select the wired connection over wireless. For example, on my laptop if I enable all three of my usual connections (3G, WiFi, wired), Ubuntu will select them in order of preference:

1. Wired
2. WiFi
3. 3G

My 3G card is at work, so I can't connect all three for you now, but here is wired and wireless in my routing table:

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.26.8.0       0.0.0.0         255.255.255.0   U     1      0        0 eth0
10.26.8.0       0.0.0.0         255.255.255.0   U     2      0        0 eth1
0.0.0.0         10.26.8.1       0.0.0.0         UG    0      0        0 eth0

eth0 is my wired connection, eth1 is my WiFi. As you can see, the "G" flag is on my eth0 connection. Ubuntu did that the instant I plugged the cat5 cable in.

The easiest way to check: Look at that little network icon in your tray. Is it the two little PCs? Or the signal meter? The signal meter means Ubuntu will use the WiFi connection.

As to the direct answer if you really want to actually deactivate your WiFi for another reason (and I figure you don't have an actual switch for this on laptop), then you may want to install [wicd]("http://wicd.sourceforge.net"). It is more configurable for manually controlling your network interfaces. There are Ubuntu instructions on their download page.

---

