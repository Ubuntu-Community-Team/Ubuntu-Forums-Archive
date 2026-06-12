---
title: "[SOLVED] Connected to network, but almost no internet."
date: 2008-07-19
forum: Networking &amp; Wireless
---

### Post by letubenaiah on 2008-07-19
Hey Guys!

I am running Hardy and have an interesting problem.  I can connect wirelessly to a WEP network and Skype will connect to the internet but nothing else will.  I am using a RaLink EW-7128G wireless card.  I am using DHCP to get my local IP address, I have tried using different DNS servers (openDNS) but it didn't work. 

Thanks Everyone!
Benaiah

---

### Post by letubenaiah on 2008-07-24
UPDATE:  I think I've narrowed in down to a DNS problem.  If I type in the IP address of a website directly into the address bar the browser will get there.  But it still doesn't work if I just type in the name.  I've tried using different DNS servers by adding the line "supersede domain-name-servers IP, IP;" to /etc/dhcp3/dhclient.conf but it didn't make any difference.  Any ideas?

Thanks,
Benaiah

---

### Post by bab1 on 2008-07-24
Where are you setting your dns server address?  Is it /etc/resolv.conf?  Is it handed out by the dhcp server?  I would configure the NIC to get the dns address from your spec rather than dhcpd to start with.  In other words the /etc/resolv.conf file.

---

### Post by letubenaiah on 2008-07-24
> **bab1 said:**
> Where are you setting your dns server address?  Is it /etc/resolv.conf?  Is it handed out by the dhcp server?  I would configure the NIC to get the dns address from your spec rather than dhcpd to start with.  In other words the /etc/resolv.conf file.

I first tried the one given by the dhcp server, when that did not work I tried a different dns server by changing the nameserver in /etc/resolv.conf that did not work either and was over written with the old dns every time I restarted.  That is when I changed it in /etc/dhcp3/dhclient.conf.  After changing it there it added those dns servers to /etc/resolv.conf and kept those settings even after reboot.

---

### Post by bab1 on 2008-07-24
Take a look at [[COLOR="Red"]THIS[/COLOR]]("https://www.opendns.com/start?device=ubuntu")

---

### Post by letubenaiah on 2008-07-24
> **bab1 said:**
> Take a look at [[COLOR="Red"]THIS[/COLOR]]("https://www.opendns.com/start?device=ubuntu")

I'd tried that a few days ago, but I tried it again with the same results.  Only skype connects, but I can get to webpages by IP address. I really appreciate the help though!

Benaiah

---

### Post by bab1 on 2008-07-24
This is a dns problem.  One last thought, cam you ping and of the sites by name? and have you disabled IPv6?  i have heard that it cam make dns time out before resolving your request.See [[COLOR="Red"]here[/COLOR]]("http://ubuntuforums.org/showthread.php?t=866561")

---

### Post by letubenaiah on 2008-07-24
> **bab1 said:**
> This is a dns problem.  One last thought, cam you ping and of the sites by name? and have you disabled IPv6?  i have heard that it cam make dns time out before resolving your request.

I have tried disableing IPv6.  I tried it once from within FireFox and also using /etc/modprobe.d/blacklist.  That didn't work either...

---

### Post by bab1 on 2008-07-24
Hrummmmpfffff!  Re-install!

---

