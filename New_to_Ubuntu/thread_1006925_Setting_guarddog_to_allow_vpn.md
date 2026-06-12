---
title: "Setting guarddog to allow vpn"
date: 2008-12-09
forum: New to Ubuntu
---

### Post by gsub on 2008-12-09
Hi, all.

I finally got vpn working (almost) - It's installed, and running, but I need to take down my firewall (guarddog) in order to get it to work.

I'm quite obviously blocking some protocol that VPN needs to use, and was wondering if someone could tell me which ones I should enable.

Many thanks.

---

### Post by gsub on 2008-12-10
<bump>

anyone?

---

### Post by Benic on 2008-12-11
I use Cisco VPN with Guarddog and it works fine once you find out the good settings.

Here's mine, maybe that will help you:
UDP port 500 and 10000 (may be different, check documentation)
TCP port 10000 (may be different)
Tick the TCP clock option
Don't forget to allow those in the internet and local zone protocoles
In protocoles:
http, https, and DNS (to use internet)
ftp (if needed)
NTP time synchro 
Ping
PPTP
IMAP or POP and SMTP (to use mail if needed)
NFS 

I did the same for both internet and local zone, because I think you need both to use the internet with the vpn. Maybe I allow too many things. I don't know, I'm far from being an expert. But at least it works for me.

---

