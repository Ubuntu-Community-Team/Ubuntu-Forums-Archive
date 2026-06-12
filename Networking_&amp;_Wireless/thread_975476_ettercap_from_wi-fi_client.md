---
title: "ettercap from wi-fi client"
date: 2008-11-08
forum: Networking &amp; Wireless
---

### Post by bruno386 on 2008-11-08
Is it possible to ARP poison clients on my lan from one of my wi-fi clients? I get good results when sat at one of the wired clients, but my wi-fi client never seems to poison successfully. I'm using ettercap, I get no errors, all my clients show when i scan the subnet, unified sniffing starts, but i dont catch any data.


using the ubuntu based mint linux distro with a netgear wn511T card.

Any ideas?



**update**

I have tried the poison whilst running wireshark on the wireless machine, and sure enough it is poisoning because i can see the data form the wired client pouring in. So I guess my question is redundent. But still, why does it not decipher them and drop them into ettercap like it usually would? Is this a bug or is it something to do with the way the ARP tables being setup differently between wired and wireless clients?

THanks in advance.

---

