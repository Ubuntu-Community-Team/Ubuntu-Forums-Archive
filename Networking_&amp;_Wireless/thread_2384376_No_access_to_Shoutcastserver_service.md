---
title: "No access to Shoutcastserver service"
date: 2018-02-06
forum: Networking &amp; Wireless
---

### Post by tadiwe on 2018-02-06
Hi all,
I installed Shoutcastserver on my Lubuntu x86 running in an older HP Laptop.
The Server comming up right. The Server hast a Webpage responding in http on Port 8000. So I can access the Page using [http://localhost:8000/](http://localhost:8000/)
using Firefox Browser. The Laptop is connected by WiFi to the Internet. Also all Webpages in the Internet are working fine. But my other computer in the LAN is not able to access the Shoutcastserver using the Address [http://192.168.2.106:8000/](http://192.168.2.106:8000/)
I tried several things like modify the hosts.allow, adding iptable stuff, disable ufw, etc. I then saw it working one time, but again gone after reboot. I then uninstalled ufw and iptable, also no luck. I think there must be somewhere something which I Miss. thanks in advanced.

---

### Post by tadiwe on 2018-02-07
Very weired behavior:
I just setup telnetd, because I want to check if this is not working, too. After setup, telnetd and Shoutcast are working both. No Idea why.
I guess that the setup of telnetd changed something which wasn't done before.
So currently it seems to be solved.

---

### Post by tadiwe on 2018-02-07
Still working, does no one has an idea what happened?

---

