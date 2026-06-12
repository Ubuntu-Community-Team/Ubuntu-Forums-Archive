---
title: "the end of my powers ..."
date: 2008-03-13
forum: Networking &amp; Wireless
---

### Post by spinctz on 2008-03-13
is anyone here that has succesfully installed the sis190(191) ethernet card drivers without ndiswrapper ... 

if not ... and you've installed it with ndiswrapper how do you got internet conection using a router ... i can ping external ip's (209.85.129.99) but not http address ([www.google.com](www.google.com))...

please answer

---

### Post by Paris Heng on 2008-03-13
To ping domain name, you need a** iptables/Netfilter **in the box.

> Netfilter is a framework that provides a set of hooks within the Linux kernel for intercepting and manipulating network packets. The best-known component on top of netfilter is the firewall which filters packets, but the hooks are also used by other components which perform network address translation, stateful tracking and packet enqueueing to user space.

Regards

---

### Post by spinctz on 2008-03-13
ok ...lets say i understand that ... if i can ping in  the terminal why don't I have any internet in firefox ...
new in ubuntu .. so don't take me hard ...

---

### Post by Paris Heng on 2008-03-13
On the other hand, you also need to on your IP forwarding, in this case IPv4,

> echo 1 > /proc/sys/net/ipv4/ip_forward


Check your routing table as well,

> #route -n

Hope this can help.

---

### Post by kevdog on 2008-03-13
Sounds like a DNS resolution problem to me.  Here is a guide how to use OpenDNS -- try it -- its fairly easy to setup:

[http://ubuntuforums.org/showthread.php?t=543659](http://ubuntuforums.org/showthread.php?t=543659)

---

### Post by spinctz on 2008-03-13
nope ...that is not the problem ... i have those settings ...
here is what i "think" maybe someone sees something ( i'm a newbie so don't laugh) ... 
i think is because my wired card appears like a wireless card ... and every time i "force" the wired connection i get wlan0: no IPv6 routers present... maybe my router is not IPv6 ... if what i said is not stupid can anyone think of a sollution ...

---

