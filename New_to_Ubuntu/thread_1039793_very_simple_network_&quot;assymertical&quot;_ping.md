---
title: "very simple network: &quot;assymertical&quot; ping?"
date: 2009-01-14
forum: New to Ubuntu
---

### Post by minsf on 2009-01-14
I connected my ubuntu 8.10 laptop to an XP laptop with CAT 5 cable. 
simple, ha? well, dont forget i'm a newbie :)
Anyways, I defined the eth0 IP on my side with "ifconfig" and on the other side by changing the TCP/IP properties inside the "local area connection" properties inside "network connection".
ping works from the XP to ubuntu (I can even see the packets on ubuntu side with "tcpdump").
[COLOR="Red"]why doesn't ping work from my ubuntu to the XP?[/COLOR]
(100% loss, no echo)

More details: IP addresses 192.168.1.2 for ubuntu and 192.168.1.3 for xp. network mask 255.255.255.0 i guess the routing tables in the xp are fine (because it successfully pings the ubuntu). if you want i can post the "route -n" of the ubuntu, though it looks fine for me. i removed the firewalls on both sides (and obviously disconnected them from the internet while the firewalls were off). i will gladly post more details, just let me know what you need. 

goal: at this point i only want to be able to ping from both sides. (later, i may want to share files between the two computers only. Actually the XP is already able to get files from my ubuntu, via the apache server installed on the ubuntu. that is, i put a file in /var/www and i point xp's firefox to [http://192.168.1.2/filename](http://192.168.1.2/filename) but i'll be glad to know of a better method)

---

### Post by handydan918 on 2009-01-14
To connect as you describe requires a cross-over cable, rather than a standard ethernet cable. Or, you can go thru a router or a switch or a hub.

---

### Post by minsf on 2009-01-14
hmmm... are you sure it's about the cable? shouldn't ethernet cable allow packets to go in both directions? in fact, i think i see packets going in two ways (with tcpdump).
it seems to me that if everything work fine in one way, it should work in the other way too (if it's configured correctly), shouldn't it? i dont see where the assymetry comes from. so if if the xp can ping and grab files, why wouldn't the ubuntu?
anyways, thanks handydan (where did all the thank system disappear?)

---

### Post by wirelessmonkey on 2009-01-14
Handydan is absolutely right, though I'll add that it sounds like one of the NICs, probably the desktop NIC, has autosense capabilities, and is thus able to reply to the XP machine, and not vice versa.

---

### Post by handydan918 on 2009-01-14
cat5 cables are not, in fact symmetrical. If you consider the matter for a moment, you'll see that they can't be.

[Here is a tutorial on making cat5 cables]("http://www.lanshack.com/make-cat5E.aspx") that explains the basics pretty well...

---

### Post by DGortze380 on 2009-01-15
Need a cross-over cable. Definitely.


Simple explanation:

Straight-Through (Regular Cat V) Cable:
(Comp 1 Talks Here)   Tx --------- Tx (Comp 2 Talks Here)
(Comp 1 Listens Here) Rx --------- Rx (Comp 2 Listens Here)

Cross-Over Cable:
(Comp 1 Talks Here)   Tx --------- Rx (Comp 2 Listens Here)
(Comp 1 Listens Here) Rx --------- Tx (Comp 2 Talks Here)

---

### Post by minsf on 2009-01-15
Thank you guys for your help and for your patience to explain it to me.
you guys are the best! 
i will definitely get a crossover cable.
i know i am a newbie, but i still [COLOR="Red"]do not think that it is a cable problem[/COLOR]. to prove that it is not, i did as handydan suggested and connected the two computers via the [COLOR="Green"]wireless[/COLOR] router. the situation is the same: the xp can ping the ubuntu (and grab files via the apache server that installed on the ubuntu), but the ubuntu cannot ping the xp.

---

### Post by Tony Flury on 2009-01-15
is your XP box running a firewall that might be blocking/ignoring pings ?

---

### Post by minsf on 2009-01-15
solved
(where did the "solved" tool and the thanks disappeared?)

---

### Post by Tony Flury on 2009-01-15
As a matter of interest - what was the solution ?

I think that they removed (temporarily) the SOLVED and Thanks functions to try to improve stability of the forums.

---

### Post by minsf on 2009-01-15
when i tried with the cable, i removed all firewalls completely. (it still seems to me that one of the NICs was able to do the crossover automatically, or else i wouldn't be able to send files over tcp. but maybe i am a stubborn newbie... LOL)
then when i tried the wireless, i put the firewalls back, and allowed ICMP. 
After your post about the firewall, i decided to check it again. and, indeed, the ICMP was not configured correctly on the XP end. so I removed the firewall for a second, and pinging worked both directions. 
So now i know the network is configured correctly, and I just need to play with the firewall on the xp.
Anyways, thanks Tony for your post that reminded me to check the firewalls.

any recommended link about file sharing for beginners?

---

