---
title: "Cannot connect / ping anything behind router (IPNetRouter)"
date: 2006-12-17
forum: Networking &amp; Wireless
---

### Post by DungaDunga on 2006-12-17
Just installed 6.10 for the first time (never have used Linux before) on a X86 box.

I have a small network with static IPs, so entered 192.168.0.200 as IP, 255.255.255.0 as mask, 192.168.0.1 as router / DNS (I have DNS forwarding set up).

The result - can ping router and local machines, can't see anything behind the router.

All other computers work OK (Macs and PCs), Win XP connects without problem on the same machine.

Tried disabling DNS forwarding and entering actual DNS - no result. Changing IP - the same. Disabled IPv6 - the same.

The router is an old Mac running IPNetRouter v 1.6.8.

When I click on any address in Firefox, it just keeps "Looking up..." for a minute and then says can't connect. Can't ping anything outside network neither by domain name nor by IP.


Is there anything else to try or just forget about Ubuntu with such a rocky start?...

---

### Post by DungaDunga on 2006-12-18
Well, back to Windows then...

---

### Post by nijinsky on 2006-12-19
Okay as  a last resort then if you are going back to windows......

I will recommend another linux distro. Use Xandros and it should automatically setup. I use this on my laptop. I beleive there is a free version (V3) but the latest is commercial, however, I bought the home premium (only $79) or £40 at todays great exchange rate :-).

You could always download the 30 day trial, have a poke around in the config files and then go back to Ubunu and try it again for free.
 
I kept xandros because it worked first time with WPA on my IBM T30 laptop.

I like Ubuntu, free and as complete as any distro, however, for the ease of configuration (all automatic), and ease of transition from winxp I think xandros cannot be beaten.

regards
Bob

---

### Post by Iowan on 2006-12-19
You might try a **Search** for **DNS** - or check posts tagged **DNS**.
Post the contents of **/etc/network/interfaces**, **/etc/resolv.conf**, and the results of **route -n**.
(All this from a terminal - details on how to do this can be provided if you need them).

Do you have a **gateway** specified? (*Should* be your router address)

---

