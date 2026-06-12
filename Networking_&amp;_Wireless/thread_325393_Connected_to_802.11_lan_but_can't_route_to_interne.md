---
title: "Connected to 802.11 lan but can't route to internet"
date: 2006-12-25
forum: Networking &amp; Wireless
---

### Post by armbarcrashdummy on 2006-12-25
G'day all,

I've got a weird one, I can connect and associate with my 802.11LAN, but can't connect to the internet.  It's looks like my machine can't find a default router (even though it's set)?

I've got my AP as the default router (netstat -nr) and the AP is also in /etc/resolv.conf along with the IP of my ISP's primary DNS. I can ping my AP and other clients on the LAN.  If I try to ping an external site, I can see the DNS resolution in the ping (ie, I see the IP along with the hostname).

I've got IPv6 disabled in Aliases as well.

It's got me confused.

Any ideas?

p.s Ubuntu 6.06 on a Tecra A3X (ipw2200).

---

### Post by armbarcrashdummy on 2006-12-25
Ok,

Now I'm really confused. I can access external sites via Firefox, but not ping or apt-get etc.

WTF?

---

### Post by dgalant1 on 2006-12-25
I have a similar issue when I restart the computer and boot into linux from windows, but doing a cold boot with wireless enabled works every time.  I wasted about 2 hours of my life compiling the latest ipw2200 driver which seem to be already included in 2.6.17 kernel.

sometimes I can resolve this by running dhclient...

---

### Post by dbott67 on 2006-12-25
Have you seen this thread (post #3 and #5):

[http://www.ubuntuforums.org/showthread.php?t=323747](http://www.ubuntuforums.org/showthread.php?t=323747)

-Dave

---

