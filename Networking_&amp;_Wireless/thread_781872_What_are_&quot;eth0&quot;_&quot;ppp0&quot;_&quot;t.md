---
title: "What are &quot;eth0&quot; &quot;ppp0&quot; &quot;tap0&quot; &quot;lo&quot;?"
date: 2008-05-04
forum: Networking &amp; Wireless
---

### Post by Xanderfoxx on 2008-05-04
I have wondered what exactly these "interfaces" are called, and what their nature is.

I need to know, because I need to know if IPsec can be labeled "tap23" or such, or if that is only for SSL/TLS tunnels.

I want to know more about the operating system I'm running. Anyone up for a quick tutorial on what I know aren't actually drivers, or the hardware itself? :)

Thanks in advance.

---

### Post by ddrichardson on 2008-05-05
eth0 is the first ethernet device
ppp0 is the first point ot point protocol device, usually associated with a modem
lo is the loopback interface, 127.0.0.1
tap0 is the first virtual ethernet device, explained quite nicely [here]("http://vtun.sourceforge.net/tun/faq.html").

---

