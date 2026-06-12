---
title: "Constant Network Usage, Help!"
date: 2007-07-19
forum: Networking &amp; Wireless
---

### Post by kodoku on 2007-07-19
Hello all,

This issue first started when noticed my network monitor on a fresh Linux Mint, and I notice that my network is constantly being utilized (190 KB/s in, 8 KB/s out), right after booting up.  I did not have any kind of P2P application running, nor was I browsing the net or downloading anything.  Then I notice Moblock was blocking one particular connection constantly (169.254.255.255, labeled as Bogon), up to 860 times by the time of this post.  I freaked out and thought I was getting hacked and installed Firestarter, which then tells me that Samba is constantly using the network.  I check with my other computers, which are all on the same network, and they were not transferring any files or using the network.  Then I shut off those computers, and then network calmed down.  So is it normal for Samba to be using that much bandwidth just idling?? And what do all these blocked "Bogon" ip's mean in moblock??

EDIT: Ok, so these blocks are just DHCP Packets that my system is trying to send out.. should I just allow them?

---

