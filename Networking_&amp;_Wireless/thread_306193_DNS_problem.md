---
title: "DNS problem"
date: 2006-11-24
forum: Networking &amp; Wireless
---

### Post by snl on 2006-11-24
I am using my laptop both at home and at school. I don't have any problem connecting to the internet at school, but to connect to the internet at home, I have to manually enter my DNS Servers and then lock the resolv.conf so that it won't reset. Is there any other way so that I don't have to enter my home DNS Servers and lock/unlock resolv.conf everyday.

Thank you.

---

### Post by Tilex on 2006-11-24
Your router connects automatically to your DNS server, right?  If you include the "router" of your router (eg. 192.168.1.1), won't it translate your DNS server for you?

Or maybe you could save a school and home profile under WifiManager Assistant...

---

### Post by cilynx on 2006-11-24
You've probably got network-admin hijacking your configuration.  If you want to use network-admin, it isn't too bad as it has profiling support.  If you don't want to use it, delete all settings therein and leave all of your interfaces as "unconfigured".  Just in case you're a command line junky like me and don't know where to find the "easy ways to do things":

Click System->Administration->Networking

Let me know if that works for you...

---

### Post by snl on 2006-11-24
The problem is at home, it picks up 10.0.0.138 instead of my ISP DNS Servers that why I have to enter them manually.

I am using speedtouch 585 router (using wired connection).

Thank you.

---

### Post by cilynx on 2006-11-24
Gotcha.  Configure the DHCP server on your router at home to tell the clients the IP of your ISP DNS as opposed to 10.0.0.138.  It's got nothing to do with your laptop.  Either that or setup 10.0.0.138 as a DNS forwarder =)

---

### Post by stream303 on 2006-11-25
I'd probably just write those isp dns nameservers into your router's setup page.

Perhaps the following might help:
[http://www.ubuntuforums.org/showthread.php?t=305275](http://www.ubuntuforums.org/showthread.php?t=305275)

---

