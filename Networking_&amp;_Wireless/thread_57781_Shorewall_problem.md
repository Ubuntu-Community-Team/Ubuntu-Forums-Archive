---
title: "Shorewall problem"
date: 2005-08-17
forum: Networking &amp; Wireless
---

### Post by henrrrik on 2005-08-17
My Ubuntu-box has two NICs and acts as a router/firewall for my lan. I installed Shorewall the other day and it works fine until I reboot the system. Something doesn't start properly, because the lan clients cannot access the Ubuntu-server (via SSH) or the internet anymore. dhcpd hands out IP-adresses to the clients OK though. Seems like some weird NAT issue. /etc/init.d/shorewall starts at bootup without any problems. 

Manually running "shorewall clear" followed by "shorewall start" fixes the problem. 

I've compared the output from "iptables -L -v" before and after clearing and restarting and I can't spot any differences.

Any ideas?  ](*,)

---

### Post by az on 2005-08-18
Can the lan clients ping external ip addresses?

 ping  64.233.167.99

---

### Post by henrrrik on 2005-08-18
Pinging the server (192.168.1.1) from a client works, pinging external addresses doesn't work. 
Accessing Samba and netatalk shares on the server from a client works. Accessing the server using ssh works but it takes about two minutes for the password prompt to appear after running "ssh 192.168.1.1". Accessing "http:/192.168.1.1" is also extremely sluggish. Netatalk and Samba are very responsive however.

---

### Post by LB6688 on 2006-05-18
[QUOTE=henrrrik]
Manually running "shorewall clear" followed by "shorewall start" fixes the problem. 

I've compared the output from "iptables -L -v" before and after clearing and restarting and I can't spot any differences.

Any ideas?  ](*,)[/QUOTE]

I have Exact same problem right now, Did you ever find the "fix"/"work around"?


Thanks

---

### Post by LB6688 on 2006-05-19
Anyone? I have de-install/re-install shorewall with no luck.

Thanks

LB

---

### Post by henrrrik on 2006-05-26
Make sure IP_FORWARDING=On in /etc/shorewall/shorewall.conf
That solved it for me.

---

### Post by Dany on 2006-06-03
p

---

