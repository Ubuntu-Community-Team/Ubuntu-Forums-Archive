---
title: "intermittent network"
date: 2008-04-29
forum: Networking &amp; Wireless
---

### Post by RSnowman on 2008-04-29
Sometimes on the first boot into 8.04 I do not get a connection.

Now I can reboot several times and not get a connection. Right now I have no connection in Ubuntu. 

In Windows this doesn't happen. Every boot is good (the network is there, I mean)

Device Manager sees my network card as rtl8111/8168B. The driver it looks like is r8169.

I have tried DHCP and my static address. No difference.

I go /etc/init.d/networking restart many times.

What other information? Is there a way to make a deeper restart without reboot? 

Something is wrong. what do you think it is.

Thanks for your help

Richard

---

### Post by RSnowman on 2008-04-29
Oh excuse me. I find this:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/221499](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/221499)

But this is very bad. How can I update when it is fixed?

---

