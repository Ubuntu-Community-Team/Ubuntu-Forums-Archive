---
title: "Network problem - can ping google.com, but not http://www.google.com"
date: 2008-01-12
forum: Networking &amp; Wireless
---

### Post by leepr on 2008-01-12
Hi there,

I did a fresh install of Ubuntu 7.10 on a new machine without any problems until just this morning. Firefox can no longer connect to the web. I have a bunch of SSH/FTP mapped drives that I can still see and I can still successfully ping google.com from the terminal. However, when I try to ping _[http://www](http://www)._google.com, it says that the host is unknown. Take away the "http://www" and it works.

I'm connecting via DHCP to Qwest DSL. The network connection is up - I can still go places with FTP/SSH, but HTTP access seems to be disabled. Neiter Firefox, Lynx or ping let me see http content. There's no problem with the router, 'cos the wireless connection is working in the rest of the house. The machine I'm having problems with is connected directly to the router.

I didn't install/pach/delete anything prior to this issue. It was working last night, but not this morning.

Can anyone offer any advice?

Cheers,
  LeePR

---

### Post by ebutton on 2008-01-12
Sorry that I can't offer more, but I think that no one can ping "http://www.google.com".  http is a tcp protocol on port 80, whereas ping is an ICMP protocol (not a tcp protocol).  It won't help you discover what is blocking tcp port 80 outbound, but you SHOULD be able to ping just the DNS part of the URL = [www.google.com](www.google.com), which resolves to a unique IP address.

For example:
ping [www.google.com](www.google.com)
PING [www.l.google.com](www.l.google.com) (216.239.51.104) 56(84) bytes of data.
64 bytes from kc-in-f104.google.com (216.239.51.104): icmp_seq=1 ttl=243 time=20.9 ms

Regards,
EdB

---

### Post by desertphotog on 2008-01-12
I've been having a similar problem since installing gutsy on my Dell Jan 1.  I did get my WiFi working yesterday by disabling the IPv6 in the browser.  Go to Firefox browser and type in about:config and scroll down to  network.dns disable.IPv6   and make it "TRUE"  (BOLD).  See if it works for you- it's easy to undo too, if you need to use it.

---

