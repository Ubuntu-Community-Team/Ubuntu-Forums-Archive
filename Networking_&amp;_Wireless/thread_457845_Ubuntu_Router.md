---
title: "Ubuntu Router"
date: 2007-05-29
forum: Networking &amp; Wireless
---

### Post by hedgefighter on 2007-05-29
Hey guys,
I'm trying to make a router with Ubuntu 7.04 Server. I've been following this howto: [http://ubuntulinuxhowto.blogspot.com/2006/06/setup-your-computer-to-be-router.html](http://ubuntulinuxhowto.blogspot.com/2006/06/setup-your-computer-to-be-router.html)

The DHCP seems to work fine. I get an IP from the router, but I can't seem to get a connection to the outside world. I can't figure out what the issue is. My guess is that it's the iptables. If anyone can help or knows what's wrong or a more up to date tutorial, I'd really appreciate it.

---

### Post by beatbros on 2007-05-29
> **hedgefighter said:**
> Hey guys,
I'm trying to make a router with Ubuntu 7.04 Server. I've been following this howto: [http://ubuntulinuxhowto.blogspot.com/2006/06/setup-your-computer-to-be-router.html](http://ubuntulinuxhowto.blogspot.com/2006/06/setup-your-computer-to-be-router.html)

The DHCP seems to work fine. I get an IP from the router, but I can't seem to get a connection to the outside world. I can't figure out what the issue is. My guess is that it's the iptables. If anyone can help or knows what's wrong or a more up to date tutorial, I'd really appreciate it.

Hi,
have you enabled ip forward?

```

sudo echo 1 > /proc/sys/net/ipv4/ip_forward

```

---

### Post by hedgefighter on 2007-05-29
That did it. Thanks a lot. Turns out I turned on ip_forward in /etc/sysctl.conf instead. :o

---

