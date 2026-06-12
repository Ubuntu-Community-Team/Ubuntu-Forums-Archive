---
title: "Connection sharing with multiple devices"
date: 2008-07-24
forum: Networking &amp; Wireless
---

### Post by Kev1729 on 2008-07-24
Hey there.

I already have one of my servers sharing the internet connection with my desktop, and I also need to be able to share it with my PS3.  I am trying to do it though my desktop, since that will be on most of the time I play my PS3 and the cable is quite short it wont reach the server. Would it be easier to have the server share all connections?

Anyway, I have enabled IP forwarding/masquerading etc like I did with my server and tried a sane setup on the desktop and PS3, I just have no idea why it is not working, here is a basic layout:

Router is connected to server on eth1 (192.168.0.4), which shares the connection with eth0 (192.168.1.1).  This works fine.

The desktop needs to share with the PS3, on eth1.  I have tried different addresses, 192.168.1.3, 192.168.2.1 etc. No joy.

I am using firestarter for routing, connections from all the addresses I have tried are enabled and there is nothing appearing in blocked connections.

The thing is, when I try the connection test on the PS3, the desktop drops the connection as the PS3 obtains an IP address.

Help me please!  :(

---

### Post by superprash2003 on 2008-07-24
is your setup like this server->desktop->ps3 or server->desktop ,server->ps3 ??

---

### Post by Kev1729 on 2008-07-24
Server -> Desktop -> PS3

---

### Post by Kev1729 on 2008-07-24
Never mind I got it working, I forgot to set the broadcast address.

:)

---

