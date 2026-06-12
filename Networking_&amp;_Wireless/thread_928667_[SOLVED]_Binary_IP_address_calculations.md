---
title: "[SOLVED] Binary IP address calculations"
date: 2008-09-24
forum: Networking &amp; Wireless
---

### Post by Rytron on 2008-09-24
Hi,
If someone was given two ip addresses in binary format, how can they confirm that the two ip addresses are on the same network. 

Note that custom subnets are used (i.e. not /8 or /16 or /24 at the end of the IP address.

Also is there an online/offline tool that allows you to input two binary IP addresses and find out if they are on the same network?

Thanks.

---

### Post by pedro_orange on 2008-09-24
The only difference between binary IP and decimal IP is their base. Just tokenize the binary string into 8 characters and convert to decimal. Then you'll have a decimal IP address. 

1111 1111 . 1111 1111 . 1111 1111 . 0000 0000
255       . 255       . 255       . 0 

With regards to finding out if they're on the same network, this is done with subnets. Thats what subnets are; a subdivision of a larger network that enforces a hierarchical design.

So if they're in the same subnet they're definatley in the same network.

---

