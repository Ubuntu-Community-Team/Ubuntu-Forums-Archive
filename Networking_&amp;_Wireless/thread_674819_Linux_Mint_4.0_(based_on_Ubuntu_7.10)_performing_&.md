---
title: "Linux Mint 4.0 (based on Ubuntu 7.10) performing &quot;portscans&quot; on Windows network"
date: 2008-01-22
forum: Networking &amp; Wireless
---

### Post by devilears on 2008-01-22
I installed Mint 4.0 (Ubuntu 7.10 based) on my company laptop during the holidays in December, and it's working great! One issue though, upon returning to the office, I had hardly plugged the machine into the company LAN, when our IT security guys stormed in claiming (and proving to me), that my laptop was scanning the whole of the company LAN for open ports every 20 minutes! What can this be? It must be some service that is switched ON by default in Mint because I never had this issue whilst running UBUNTU 7.04 or 7.10. PLEASE ASSIST URGENTLY!

Sorry for asking help over here, but the Mint Forum is kinda quiet....

---

### Post by Thanoulis on 2008-01-22
I do not have installed Mint ever, but if it is your laptop that portscans the entire LAN, there must be a process somewhere that do that...
Try to type in a terminal:
```
ps -aux
```
and search for anything suspicious...

---

### Post by Monkey77 on 2008-01-22
Hi,

What port ranges is it scanning?  

There are services that will do network discovery to find services out there, I think Apple used to call in Bonjour or Zeroconf.  

You might have an avahi service running that is doing this.

[http://avahi.org/](http://avahi.org/)

Regards
Phil Hannent

---

