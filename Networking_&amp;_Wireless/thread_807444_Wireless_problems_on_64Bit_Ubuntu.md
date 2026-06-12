---
title: "Wireless problems on 64Bit Ubuntu"
date: 2008-05-25
forum: Networking &amp; Wireless
---

### Post by yamagami on 2008-05-25
Hi all
I've done a lot of research on the following problem and although I found somewhat similar issues, none of the solutions worked for me so far.
I've received my new Thinkpad T61p with the built in Atheros wifi. I promptly installed the latest Amd-64 version of Hardy. All works great, EXCEPT that network manager can't connect to my home wireless network. 
I can see the network, it asks me for my WPA key, and then it just spins there for a while and eventually times out. 

* Syslog shows all is ok, until the end where it complains it took too long. ("Association took too long (>120s), failing activation")
* I've tried this on Gutsy live cd (64bit version) and had the same problem. 
* The same card works great in XP. 
* Wired network works without a problem. I simply plug in the cable and I'm online.
* I've disabled IPV6 (blacklisted module and disable=true in aliases).
* I've tried manual configuration as well. 

Please, if anyone has any insight on this one, I'll be forever grateful. I've been battling with this for a few days now.

Thanks, 
Harel

---

### Post by trucker33377 on 2008-05-25
have you tried to connect without a password? open the router and remove it at least it may let you know where your problem is. Good Luck Ive been trying amost a month now with this gateway. so far i did get kubuntu on line wireless but i dont like it all that well

---

### Post by yamagami on 2008-05-26
I connected an Atheros based PCMCIA card to the laptop, and wireless worked!
Its the same chipset, but the internal thinkpad one does not work (times out) and the external one does. This driving me nuts. I got a state of the art thinkpad based on its good reputation with linux, and now this. 
I've also recompiled latest madwifi and wpa_supplicant drivers. 
Tried to boot a live cd of hardy for intel x86 (no 64bit).
Tried a gutsy amd64 live cd, 
No cigar.... ;o( I'm lost here.
H

---

### Post by yamagami on 2008-05-28
Resolved!!!!!
I took the latest madwifi from SVN, recompiled it, and then recompiled the latest wpa_supplicant against that source. 
Works a treat!

---

### Post by Alex J. on 2008-05-28
Looks like I may have the same problem. I'm pretty new at this, possible that I could get some terminal commands or more explanation?

---

