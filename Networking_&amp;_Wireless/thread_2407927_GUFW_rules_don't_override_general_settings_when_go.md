---
title: "GUFW rules don't override general settings when going with the whitelisting approach"
date: 2018-12-11
forum: Networking &amp; Wireless
---

### Post by thia11 on 2018-12-11
Hello, fiends!
 

 

 I am trying to barr my computer from the internet when I play my steam games so they don't phone back home, so I can make my little statement about consent. But I want my browser to have online access so I can listen to music.
 

 I have the GUFW Firewall. The default general settings are -Incoming: Deny, -Outgoing: Allow.
 

 When I click on the report after a fresh boot, I get exactly 30 entries - ports: 111, 123, 137, 138, 139, 3***** for rpc.statd, 445 simbd, 5***** for avahi-daemon and rpc statd, 631 for cups-browsed, 677 rpcbind, and 68 dhclient
 I imagine all these are normal things, though, reading about some, maybe I should also block them, but I'm afraid to brick something.
 

 Anyway, I booted up Steam, and two entries showed up as 27036 ports. Very nice. So I clicked on them and made a rule- Allow: out, just like the general rule for outgoing is allow, and incoming is deny.
 So I put the outgoing default setting to Deny, so both are deny, and I hoped my new rule for steam that says Allowut, would serve as a way of whitelisting specific programs, and overriding the general rule, like it is supposed to work for blacklisting, but it doesn't work!
 

 What should I do? I can't be chasing every gme around, and the whitelisting approach is the easiest way. I read on another forum that a guy managed to only allow ports for browsers and his thunderbird, and that everything works nice. I have to type a password every time I open GUFW, so I kow it's sudo, and I should theoretically be able to do everything he did with the graphical interface.
 

 What should I do? Am I doing something wrong? My theory was to make a profile filled with those 30 ports (or less if I can identify the useless ones) and steam, and have it on when I play games, so their proprietary software can't ring home to servers and share my data. I only allow steam to steal it and share it, but I won't be spied upon without express consent.
 

 Thanks!

---

### Post by TheFu on 2018-12-12
Play music on the system?
Use a web-proxy server that is only configured for the music player, not Steam?
There are some techniques for firewalls on a per-userid basis, but only iptables seems to have access to that level of control.  I've not used per-userid controls.   [https://www.cyberciti.biz/tips/block-outgoing-network-access-for-a-single-user-from-my-server-using-iptables.html](https://www.cyberciti.biz/tips/block-outgoing-network-access-for-a-single-user-from-my-server-using-iptables.html) was the first google result.

UFW doesn't support them to my knowledge.  UFW/GUFW is not intended to provide access to everything thing the Linux kernel firewall can do. It is a simple interface for simple needs.

[https://ubuntuforums.org/showthread.php?t=2380003](https://ubuntuforums.org/showthread.php?t=2380003) is another thread here that has some other options for your consideration.

---

