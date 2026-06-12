---
title: "Auto switching between static and automatic IPs"
date: 2008-07-30
forum: Networking &amp; Wireless
---

### Post by robtotheb on 2008-07-30
I have a static IP address on my laptop when using my home network and it works fine under Ubuntu.  When I connect to a network, for example at work I have to turn off these IP settings to connect.  Is there a way to save my home settings so I don't have to manually type them in each time?

---

### Post by Iowan on 2008-07-30
Easier way might be to get a DHCP address at home, too.  If you have no DHCP server, it might be possible to use **avahi** to "fail" into your desired settings.  I glanced only briefly at **avahi-daemon.conf** and it's **man** page.  I didn't see anywhere to set up IP addresses there, but the **avahi-autoipd.action** file did have some interesting data.

---

