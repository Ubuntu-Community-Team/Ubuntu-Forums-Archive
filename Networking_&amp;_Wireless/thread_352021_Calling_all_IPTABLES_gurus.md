---
title: "Calling all IPTABLES gurus"
date: 2007-02-02
forum: Networking &amp; Wireless
---

### Post by andytof47 on 2007-02-02
Hi, Ihave been trying to turn my install of edgy into a gateway

anyway I messed up iptables and couldn't get anynetwork connectins happenig so I tried

sudo iptables -F

sudo /etc/init.d/netoworking restart 


Still no luck what can i do?????????

---

### Post by handy on 2007-02-02
The following 2 links may be of help:

[http://doc.gwos.org/index.php/IptablesFirewall](http://doc.gwos.org/index.php/IptablesFirewall)

[http://ubuntuforums.org/showthread.php?t=159661&highlight=iptables](http://ubuntuforums.org/showthread.php?t=159661&highlight=iptables)

---

### Post by andytof47 on 2007-02-02
Cheers for the links

I flushed and played but still not working.....................


Where can i check what is happening  e.g which log file

also I noticed that I can ping external site like google and i get a normal response

I can also ftp with my service provider and i get an error for ftp with google(just testing connectivity)


I have restrted and it still is down


This comes as a result of touching iptables
Squid and Dansguardian

Netstat reveals that port 3128 still has something  listening on it(squids default port) but I thought even if this running since my iptables is reset and using a basic allow all input output form the links it should be ok


Oh yes I have gnump3 server running on the system and can access that from the web interface, just no external http :confused: :( 


Please help

---

### Post by andytof47 on 2007-02-02
Bump Please:ks

---

### Post by andytof47 on 2007-02-03
Ok

Got it sorted now


An external ipcops firewall issue and port forwarding issue


cheers for the links N E Way

---

