---
title: "VPN gaming?"
date: 2007-07-12
forum: Networking &amp; Wireless
---

### Post by Negyxo on 2007-07-12
I have a few questions that i hope i can get some help for.

I play windows games with friends from all over the world and the best way we've found the get connected and rolling is to use hamachi and create our own little VPN. The only problem is that we are reaching the threshold of hamchi's usability when we add more players. We need more bandwidth and hamachi's up/down limitations are really starting to hurt. So the idea is to create our own VPN using a dedicated Ubuntu box on a nice internet line. 

I use ubuntu a bit offhandly on some of my computers but have no experience really getting into networking and such. What i'm really asking is if anyone could point me in the right direction as to what would be the right solution. I've researched OpenVPN and it's capabilities but i'm not exactly sure on how to implement such a solution for windows gaming.  I essentially need a way to use my ubuntu box to create a UDP "lan" connection between a bunch of windows machines running lan based multiplayer games. 

Any help is much appreciated!

also, popcorn ? :popcorn: huh?

---

### Post by Negyxo on 2007-07-12
Anyone?

---

### Post by KiloEleven on 2007-07-12
VPN is going to add unnecessary overhead for gaming. It would probably be better to just use the "Connect to IP" that most games have.  This would improve game performance (lower latency). Whoever is running the server would have to forward ports on their firewall to the game server.

---

### Post by EXCiD3 on 2007-07-12
I agree with KiloEleven, VPN's really kill online gaming, my friends and I have tried it but its helaciously laggy. Just get a server and make it a private server if you dont want random noobs coming around. ;)

---

### Post by Negyxo on 2007-07-13
We are trying to play primarily RTS games, RTS games that we don't necessarily *cough* own :roll:. So we are limited to using the LAN options of whatever game we trying to use (c&c3, supreme commander and the likes...) I have a really solid fiber optics internet connection (15 mb down / 5 up) and i think i can handle 5-7 clients connected playing an RTS. I *think* using a VPN is my best bet... i could really use any advice or link to a tutorial(s) on how to setup such a network. Or any other ideas would be much appreciated.

---

### Post by mips on 2007-07-13
[http://ubuntuforums.org/showthread.php?t=239219](http://ubuntuforums.org/showthread.php?t=239219)
[http://www.thebakershome.net/?q=node/56](http://www.thebakershome.net/?q=node/56)
[http://openvpn.net/howto.html](http://openvpn.net/howto.html)

I suspect you might require a bridged lan setup from your above description.

---

