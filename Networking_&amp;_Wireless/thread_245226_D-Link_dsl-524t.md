---
title: "D-Link dsl-524t"
date: 2006-08-27
forum: Networking &amp; Wireless
---

### Post by fire_storm on 2006-08-27
hi

i am new to linux and i have a D-Link dsl-524t router but it does not work on linux is there a way to fix this problem?

thank you

---

### Post by baron_samedi on 2006-09-05
Man, you need to give some specific information on your problem if you expect to get some useful help.

I don't have Ubuntu but old fashioned Debian Testing... It seems that I have just solved a problem with my D-ling DSL-524t router. The problem was:

* Firefox couldn't see the web even when Konqueror did.

* Sometimes the connection went down altogether for no clear reason: no pings.

It seemed that the computer was updating the DNS information from the router and that caused it going bonk.

So, what I did, after much trial and error:

1. Log into the router and set it no "NO DHCP SERVER". Allocate a fixed DNS address (192.168.1.3 in my case) to the computer.

2. Change the /etc/resolv.conf file to include the DNS addresses of my ISP.

3. Change the /etc/network/interfaces to give the computer a fixed configuration for the eth0, and stop it from reading the DHCP info. That means changing the line:

		iface eth0 inet dhcp

for something like this:

              iface eth0 inet static
              	address 192.168.1.3
              	netmask 255.255.255.0
		broadcast 192.168.1.255

and that is about it. Sorry if my description is technically messed-up, but I am quite new at this myself. Hope this helps.

---

### Post by Stone123 on 2006-09-05
2. Change the /etc/resolv.conf file to include the DNS addresses of my ISP.
that the only thing you needed to do.

---

### Post by baron_samedi on 2006-09-06
> **Stone123 said:**
> 2. Change the /etc/resolv.conf file to include the DNS addresses of my ISP.
that the only thing you needed to do.

Hmmm... That was my first bet, but for some reason it was not enough in my machine. The /etc/resolv.conf file kept being written back into the default form.

BTW, my next task now is to get both computers in my home network (my linux and a windoz box) to see each other, so that I can print thrhough a printer attached to the windoz box. Any suggestion to help me save time?

---

