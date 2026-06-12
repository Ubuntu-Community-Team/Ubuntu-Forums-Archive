---
title: "Problem conneting to network"
date: 2007-07-09
forum: Networking &amp; Wireless
---

### Post by mustaq on 2007-07-09
Hi All:

I am a new user of Ubuntu. I recently moved from FC3 to Ubunto 7.04. The migration was plain and easy for my home PC, but I am having trouble with my office PC: I can't connect to the wired netowrk here. I have a static IP, and I put my IP, gateway, netmask and DNS  in System>Administration>Networking---these are the only info I needed to setup my old FC3 two years ago. But after enteing these info, the system fails to connect, and becomes sluggish in GUI response. If I disable the network connection, GUI becomes ok again after relogin. When enabled, I could ping only the gateway and nothing else, not even the DNS servers.

Can anyone suggest a solution? I am not an expert in networking issues. Thanks in advance.

Hardware: Intel P4 1.8GHz, 512MB RAM, and 80GB HDD with around 32GB in '/'. The network card is "Intel PRO/100 VE", as per Windows XP.

---

### Post by scrooge_74 on 2007-07-09
try putting that same info in /etc/network/interfases

---

### Post by mustaq on 2007-07-09
> **scrooge_74 said:**
> try putting that same info in /etc/network/interfases

The /etc/network/interfaces seems to have all the correct addresses. I have tried by modifying the file (commenting out eth1, wlan0 etc), but no luck.

---

### Post by mustaq on 2007-07-10
Ooops! The problem resulted from my own fault: I got wrong info about my DNS. Because of GUI sluggishness, I suspected hardware and network and missed my mistake. Sorry for that.

Now everything is OK.

---

