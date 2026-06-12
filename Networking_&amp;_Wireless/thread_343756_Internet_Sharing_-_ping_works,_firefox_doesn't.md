---
title: "Internet Sharing - ping works, firefox doesn't"
date: 2007-01-21
forum: Networking &amp; Wireless
---

### Post by crzdude on 2007-01-21
Hi,

I have an iBook running Mac OS X connected to the Internet and I am using Airport to share this internet connection with my Ubuntu 6.06 (a fresh new install) laptop. My ubuntu laptop is able to connect to the iBook and it receives an ip address from it (i.e., 10.0.2.2). After that is done, I am able to ping [www.yahoo.com](www.yahoo.com) indicating that I can lookup addresses. Therefore, everything seems to be working fine. However, when I launch firefox and try to access [www.yahoo.com](www.yahoo.com), the browser just keeps trying to connect to it for a long time. At the bottom of the browser window, I can see a message saying: Connecting to [www.yahoo.com](www.yahoo.com)...  It stays like this for a long time until it finally gives up and displays a screen indicating that "The connection has timed out". Why I can ping [www.yahoo.com](www.yahoo.com) but not access it via the browser? Any help would be appreciated.

Thanks

---

### Post by Iowan on 2007-01-22
IPv6 *can* cause problems .  You might disable it on  Firefox.

---

### Post by crzdude on 2007-01-22
Thanks for the hint. It did not solve the problem though. I get the feeling that this is more related to the way the network packets are handled. It looks like UDP works fine but not TCP. Ethereal shows that when I try to access a web site, my ubuntu laptop sends three or four SYN packets directly to the ip address of the web server but never gets an answer. Where could the problem be? I tried 'iptables -L' and I do not see any rules defined.

---

### Post by crzdude on 2007-01-22
Hey you all,

You may disregard this post. The problem went away as soon as I turned off the firewall in the Mac. The problem was caused by the Mac Firewall. Now, I have to figure out how to configure it properly.

Cheers

---

