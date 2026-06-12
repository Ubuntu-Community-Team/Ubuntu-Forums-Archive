---
title: "No ftp,ssh or html from outside router, not a port forwarding problem"
date: 2007-09-14
forum: Networking &amp; Wireless
---

### Post by pombe on 2007-09-14
Hi all.

I'm a bit of newbie so bear with me, but this is a bit more of an advanced problem I think...

At one point I had my ubuntu edgy media server hosting a page and I was able to ssh and ftp to it from the outside (set all my port forwarding through my DI-624 router to make that happen)  A few months ago I broke mysql and reinstalled ubuntu, but Feisty this time.   I've finally gotten around to trying to get ftp and ssh working from outside the netwrok and serve up html, but I find that I now can't connect.  If I point firefox, ftp, or ssh at the external IP I get nothing.  

This doesnt seem to be a port forwarding problem...  (I know thats ussually the culprit)   I've got the server IP and ports set exactly the same as before.   The port forwarding works if I setup a filezilla server on one computer and ftp to it using my external IP from another machine (different windows computers, not the ubuntu box obviously).

I've got no idea where to start looking for the problem...  All the google searches I've done have turned up the port forwarding thing.

Any advice on how to solve this problem would be very very much appreciated!

Cheers

Corey

---

### Post by psusi on 2007-09-14
Can you connect to it from another machine on the local network?

---

### Post by pombe on 2007-09-15
Sorry, should have mentioned that.  Everything works fine if I connect within the network

---

### Post by kevdog on 2007-09-15
Doesnt seem to be a firewall problem, however have you opened up the respective ports on the server to outside traffic??

---

### Post by pombe on 2007-09-15
Thanks for the responces guys, but it turns out it was a router problem, but not port forwarding per se.   

I had the server giving itself the IP 192.168.0.111 through /etc/network/interfaces which the router didnt like.   I set the server to DHCP and told the router to assign the server 192.168.0.111 based on its MAC address and now all the port forwarding works.

Argh.   So frustrating.   This problem didnt come up in edgy.  no idea why the router doesnt play nice with Feisty...   

I guess that I managed to figure this out is an indication that I'm maybe not a "newbie" anymore.   (still dont know what DHCP or MAC stand for though...):)

---

### Post by psusi on 2007-09-15
As long as you told the router to forward to .111 it should be fine.  DHCP stands for Dynamic Host Configuration Protocol.  Among other things, it allows computers to ask the router what address it should use instead of requiring you to configure it manually.  MAC stands for Media Access Control, which is the system for multiple computers to share access to the same physical network.  It is often used as a short for the MAC Address, which is the physical ethernet network address of the machine, at the layer under IP.

---

### Post by pombe on 2007-09-15
Well, it  *should* be fine.   

I was working under the impression that assigning the server a static IP with the router amounted to the same thing as having the server give itself the same IP through /etc/network/interfaces.  But clearly this isnt the case.   Not a clue why.  At first blush I would blame this in the router, if it werent for the fact that I never had this problem with my previous edgy install.

---

### Post by psusi on 2007-09-15
Did you also configure the dns and gateway address on the server to point to the router?

---

### Post by pombe on 2007-09-15
Is that what "gateway" is for? hrm...  maybe that was it.   I don't know what I had that set to.   I removed that section from my interfaces file after I realized I could fix this by telling the router to give it a static IP.

Oh well, it was probably just a dumb noob problem like that.

---

### Post by psusi on 2007-09-15
Yea, the gateway is the machine that you forward packets to that you otherwise can not reach directly or have an explicit route defined for, so basically without that, your computer had no idea it needed to send packets to the router to reach the outside world.

---

