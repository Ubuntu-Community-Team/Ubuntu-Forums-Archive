---
title: "Ports not opening"
date: 2007-04-08
forum: Networking &amp; Wireless
---

### Post by bifodus on 2007-04-08
I have a Linksys WRT54G router with version 1.52 firmware.  When using Deluge (although the actual bittorrent client seems irrelevant, as I've tried every client in the repositories), and setting the port range from 6881-7000, it shows the port as being open when I do a 'nmap -p 6881 localhost', and I have the same exact port range forwarded on my router.  However, when I go to the Shields UP!! site, it shows that port as being closed, and in my bittorrent client I always get stuck at the "Connecting to peers" step, and I never get anywhere.  Nothing changes when I put my computer on DMZ.

Any thoughts on why this isn't working as intended would be much appreciated.

Thank you.

---

### Post by heimo on 2007-04-08
Torrent should work even without opening those ports (even though it may work slower as you won't be able to connect to all peers). Could you try if this one works? (it's a very well seeded torrent at the moment)
[ubuntu 7.04 beta desktop i386 (torrent)]("http://torrent.ubuntu.com:6969/file?info_hash=%A5e%14%07M%86%AB-%E5uA%F4E%83%1CMc%28T%80")

---

### Post by bifodus on 2007-04-08
Still not working, but I appreciate the response.  I read in some other post that I needed to actually use Firestarter or directly configure Iptables in order to open the relevant ports, so I installed Firestarter and added the ports 6881-7000, but still no luck.

---

### Post by heimo on 2007-04-08
Also check that the port range is same as configured in torrent client. Some clients may use different port ranges, or random ports. You may want to choose some other port range (ISPs may block or shape some traffic).

---

### Post by r00tintheb0x on 2007-04-08
The best way to find out what is open on your machine is to have a trusted friend do a nmap port scan on your IP. That'll tell you if your torrent ports are open or not.

---

