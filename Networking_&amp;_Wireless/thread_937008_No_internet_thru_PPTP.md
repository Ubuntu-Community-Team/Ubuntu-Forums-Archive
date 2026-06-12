---
title: "No internet thru PPTP"
date: 2008-10-03
forum: Networking &amp; Wireless
---

### Post by KristofferAndreas on 2008-10-03
Hi!

I just installed PPTP VPN server on my ubuntu server... i can connect and everythin but when im connected i cant ping or use internet. 

can someone tell me how i activate this?

btw: if it mather, i,ve used webmin for configuration... but its no problem to use command line...

Kristoffer

---

### Post by superprash2003 on 2008-10-03
when connected .. go to the command prompt and type cat /etc/resolv.conf and post output.. are you able to ping the server.. try pinging this ip 72.14.207.99

---

### Post by KristofferAndreas on 2008-10-03
on my pc it says

> 
### BEGIN INFO
#
# Modified_by:  NetworkManager
# Process:      /usr/bin/NetworkManager
# Process_id:   5445
#
### END INFO

search lyse.net


nameserver 66.66.66.1



on the server:

> 
search lyse.net
nameserver 66.66.66.1


what can this help...?

---

### Post by superprash2003 on 2008-10-05
are you able to ping that ip i told you?? also try opening that ip on your browser

---

