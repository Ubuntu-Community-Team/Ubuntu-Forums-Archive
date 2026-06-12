---
title: "VPN ... access point?"
date: 2008-11-18
forum: Networking &amp; Wireless
---

### Post by DGortze380 on 2008-11-18
Ok, sorry here's my plan. Don't know if it will work, hoping it will. Any advice is greatly appreciated.

The idea is to gain access to Playstation Network ports without violating my schools Usage Guidelines.

1) openVPN Server on Ubuntu at my house, accessed via DynDNS
2) VPN Client on my MacBook at school 
3) Point-to-Point VPN for data transfers/network maintenance

Those are simple enough (I think). Need Help with this last one.

3) Ubuntu Box at school with the VPN client installed. Should have internet access over the VPN from my home router. Connect a PS3 to the Ubuntu Box and have the PS3 have internet access through the Ubuntu Box, Over the VPN, Through the router at my house.

Need to do this obviously because I can not install a VPN Client on the PS3.

---

### Post by SpaceTeddy on 2008-11-19
this is a classic roadwarrior configuration you want. Just ignore the fact that you want to access the PS3 - what you really want is access something that is behind the vpn server you are connecting to. 

fist of, before i start explaining anything or throwing our references - what have you actually managed so far of these steps (i am asking to know where to start explaining). Or is this (so far) only an idea that you have and don't know how to do ?

In general, this seems easy enough to do, given that you can connect your vpn from school and do not get blocked by any firewall - but then, there are ways to evade that, too...

---

### Post by DGortze380 on 2008-11-19
> **SpaceTeddy said:**
> this is a classic roadwarrior configuration you want. Just ignore the fact that you want to access the PS3 - what you really want is access something that is behind the vpn server you are connecting to. 

fist of, before i start explaining anything or throwing our references - what have you actually managed so far of these steps (i am asking to know where to start explaining). Or is this (so far) only an idea that you have and don't know how to do ?

In general, this seems easy enough to do, given that you can connect your vpn from school and do not get blocked by any firewall - but then, there are ways to evade that, too...

Well, been at school since September, so nothing is done yet as the VPN Server will have to be set up at home.

So any explanation you have time for would be a big help. 

I guess my first big question is, does the VPN operate over all ports. Meaning if a packet is sent over the VPN on port 6432 (arbitrary), will it be blocked at a physical router that is blocking 6432? Or is there a way to pipe the VPN traffic through say port 80 until it gets to the VPN Server, then back to 6432 (again, arbitrary port number, that can and will be a variety of ports at any given time). Let me know if that's not clear.

---

### Post by SpaceTeddy on 2008-11-19
openvpn allows you to run on any port with tcp or udp - and since it only uses one port, you can acctually make it look some other traffic - but you will have to use wrong ports for the vpn. this is not a big problem - but it is not standard. 

I for myself always have an openvpn server somewhere running on tcp port 443 (https) since an openvpn connection cannot be distinguished from a secure website... really. It it could, it would really defy the purpose of security... 

for setting up the server, i suppose you might want to look at this
[[COLOR="Blue"]http://ubuntuforums.org/showpost.php?p=5076501&postcount=4[/COLOR]]("http://ubuntuforums.org/showpost.php?p=5076501&postcount=4")
once you got the server working, read the thread further down to figure out how to make the forwarding work (i just explained it there)... that is really all you need... 

cheers :)

---

### Post by DGortze380 on 2008-11-19
> **SpaceTeddy said:**
> openvpn allows you to run on any port with tcp or udp - and since it only uses one port, you can acctually make it look some other traffic - but you will have to use wrong ports for the vpn. this is not a big problem - but it is not standard. 

I for myself always have an openvpn server somewhere running on tcp port 443 (https) since an openvpn connection cannot be distinguished from a secure website... really. It it could, it would really defy the purpose of security... 

for setting up the server, i suppose you might want to look at this
[[COLOR="Blue"]http://ubuntuforums.org/showpost.php?p=5076501&postcount=4[/COLOR]]("http://ubuntuforums.org/showpost.php?p=5076501&postcount=4")
once you got the server working, read the thread further down to figure out how to make the forwarding work (i just explained it there)... that is really all you need... 

cheers :)

Thanks a bunch. I'll read through that. I was considering 443 because I know it's open with very few restrictions. Just wasn't sure if it ran over 1 port or all.  

Going to leave this thread open for a bit, in case I have any trouble with the set-up. Thanks again.

---

