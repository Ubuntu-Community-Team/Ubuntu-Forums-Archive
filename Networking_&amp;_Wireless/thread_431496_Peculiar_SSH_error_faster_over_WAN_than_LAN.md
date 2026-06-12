---
title: "Peculiar SSH error: faster over WAN than LAN"
date: 2007-05-03
forum: Networking &amp; Wireless
---

### Post by MoxJet on 2007-05-03
Hello. I have a server computer in my room, that is both connected to WAN and LAN.

When I try to connect via SSH from the terminal from my desktop computer, it takes very long time to reach it thorugh 192.168.0.120, the servers static LAN IP, but it succeeds. If I access it through my DynDNS-address, the connection is established almost instantly.

If I mount the server using the »Connect to a server...»-program on the Ubuntu meny, it times out if I try to access it via LAN, but runs nice over WAN.

This is a bit annoying since I move a lot of files back and forth, and the data transferering speed is of course a lot slower if it has to go through WAN. When I use scp from a terminal ssh, the file transfer goes at maximum speed over LAN, the only problem is the connection time to the server, as stated above.

Please give me any pointers how I could solve this problem and connect via LAN instead!
Thanks in advance,
Dan

---

### Post by MoxJet on 2007-05-04
I tried adding them to /etc/hosts, and it goes quick now via terminal ssh, but mounting the folders times out. :(

---

