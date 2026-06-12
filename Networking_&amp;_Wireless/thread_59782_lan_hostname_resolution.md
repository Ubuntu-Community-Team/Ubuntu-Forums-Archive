---
title: "lan hostname resolution"
date: 2005-08-25
forum: Networking &amp; Wireless
---

### Post by soonindallas on 2005-08-25
hi all,

I thought initially this was a samba problem, but it seem to be a network (mis)configuration...  I have an XP box and a Ubuntu laptop.

I can actually browse the shares on my XP box over the network but only if I use the IP address of the XP host.  Resolution of the name of that host into its IP is not performed.  Samba complains of not being able to connect.

Each host can ping the other by IP.  The XP box can ping the Ubuntu laptop by name, but the reverse is not true.  Using Ethereal I notice the gateway resolves the XP host name to 82.101.8.43 which is a useless IP adress on my home network.

How should I start to troubleshoot this one ?

---

### Post by s_p_a_r_k_y on 2005-08-25
Check your host file for any entries in there. No reason that the gateway should have to resolve any netbios names. Gateway should only be doing DNS for external resources.

---

### Post by soonindallas on 2005-08-25
[QUOTE=s_p_a_r_k_y]Check your host file for any entries in there. No reason that the gateway should have to resolve any netbios names. Gateway should only be doing DNS for external resources.[/QUOTE]

in that case i guess the netbios resolution is not occurring, because ubuntu appends the search domain from resolv.conf and sends a DNS query to the nameserver from resolv.conf (the gateway) and asks for the resolution of a meaningless resource: isabelle.myisp.com.  The gateway responds... well if you'd care to look at the screenshot...

---

### Post by s_p_a_r_k_y on 2005-08-25
just from the screenshot what is that theMatrix then the percent? What applet is that and what does it do?

---

### Post by soonindallas on 2005-08-25
[QUOTE=s_p_a_r_k_y]just from the screenshot what is that theMatrix then the percent? What applet is that and what does it do?[/QUOTE]
 theMatrix is the name of my WLAN node.  the applet is gtkwifi, check it out here: [http://sourceforge.net/projects/gtkwifi](http://sourceforge.net/projects/gtkwifi)

a cool little applet for WLAN network detection, selection, key storage...

---

