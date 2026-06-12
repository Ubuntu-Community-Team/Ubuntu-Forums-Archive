---
title: "3c905 quits on download"
date: 2008-05-06
forum: Networking &amp; Wireless
---

### Post by ajm8127 on 2008-05-06
Hi.

I have a 3com 3c905 wired NIC in my computer. I have tried to transfer data from my NAS via FTP and NFS, and when I upload data from my computer, everything is fine and I can upload as much as I want. The problem comes in when I try to download. It only does half a gig or so before it quits, and is completely useless. I cannot access the net or anything with it after that. I have to switch to the wireless to carry on. To get the wired NIC operational again takes a restart. The problem also occurs when I download torrents.

I know this card is ancient. If support is bad, I don't care. My question is, when my computer is running, how can I reset this card. A system restart cures the problem, but that takes time, and I'm sure there is a way to do it without a restart. I'm running 7.10. Thanks in advance.

Tony

---

### Post by ajm8127 on 2008-05-07
I've tried

   #ifconfig eth0 down
and
   #ifconfig eth0 up

and I still can't get a valid LAN ip address. I get a 169.254.x.x instead of a 192.168.x.x

I also tried disabling all NICs, reseting the router, and enabling the wired NIC. Same problem. Short of restarting I can't fix it. I should NEVER have to restart a linux machine. There has got to be a way.

---

