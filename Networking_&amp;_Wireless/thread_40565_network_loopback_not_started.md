---
title: "network loopback not started"
date: 2005-06-09
forum: Networking &amp; Wireless
---

### Post by pem725 on 2005-06-09
Greetings,

I am scracthing my head about the loopback device (lo).  Why isn't it started and configured to start on boot?  Is this a bug?  Since many services require lo to be started, I figured it would be configured out of the box.  I guess I am mistaken.  How might I configure this the ubuntu way to avoid future problems.  BTW, I suspect that many who have cups (error 99's) and apache2 startup problems have the lo problem as well.  So, any ubuntu guru out there to help with configuring lo correctly?

Here is my interfaces line that is relevant to lo

# The loopback network interface
auto lo
iface lo inet loopback

Thanks greatly in advance.

---

### Post by uidzer0org on 2005-06-22
ifconfig l0 up

---

### Post by pem725 on 2005-06-22
Understood but why doesn't it startup by default?  Where in the init script is the network startup either opting to start lo or not?  So my real question is not how to start it but rather why would I need to start it up if networking starts by default?  My default NIC is my wireless (eth1) and is specified to start on boot.  Unfortunately it does not but it does start when I either ask it to start or start it using the gnome network config point and click.

---

