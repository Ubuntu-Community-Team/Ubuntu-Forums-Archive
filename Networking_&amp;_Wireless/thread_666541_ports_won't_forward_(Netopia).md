---
title: "ports won't forward (Netopia)"
date: 2008-01-13
forum: Networking &amp; Wireless
---

### Post by Mateo on 2008-01-13
i hate routers.  they are difficult as heck to set up.  i have many problems every time i get a new one.  this time i'm having trouble forwarding ports.  I am using a Netopia 3347NWG.  I go to the "Pinhole" section on the router and insert port 7111 to 7120 and select TCP.  I type in my LAN ip address as shown in the terminal command ifconfig (192.168.1.104).  I use 7111 as the "Internal Port" (not sure what the heck that means, i've never seen this option in other routers i've owned).  I then restart the router and go to [http://www.canyouseeme.org/](http://www.canyouseeme.org/) and test port 7111.  **Failure**.  7112, **failure**.  So I try several different ranges of ports thinking maybe I picked one that happens to be blocked by my ISP.  Unless my ISP is blocking ever port known to man, it's something that I'm doing wrong on my end.  but I have no idea what.  What do I do next!?

---

### Post by Mateo on 2008-01-13
bump

---

### Post by Mateo on 2008-01-13
again

---

### Post by Mateo on 2008-01-14
bump

---

### Post by Mateo on 2008-01-16
bump

---

### Post by Mateo on 2008-01-17
bump[

---

### Post by Mateo on 2008-01-18
bump

---

### Post by NullHead on 2008-01-19
Sorry you're having problems. I would install firestarter and see if that is whats causing the problems. I'm also currently having the same problems with my laptop. Make sure to use firestarter and see if it's blocking the ping through you're open port.

---

### Post by Mateo on 2008-01-19
thanks for your attempt at help. I don't have firestarter installed, so i know it's not blocking any ports.

---

### Post by disneyfriedhistory on 2008-01-19
No guarantees, but try this:
In your terminal, type: ```
sudo iptables -L
``` 
See if there are any rules running.  Chances are, there won't be, if you haven't installed Firestarter and you have a fairly fresh install of Ubuntu.  In which case, it's probably either your router or your ISP.

Did you try connecting directly to your Cable/DSL modem, without going through the router?  If it doesn't work, then it's could very well be your ISP.  My ISP (through a student dorm in Berlin) has all ports blocked except 80.  It sucks!

If you could find the ports by going around your router, then i would guess it's a router problem.  You might try assigning your LAN IPs statically, especially if it is a wireless network.  This may seem redundant, but I had a laptop that would constantly time out on port 80 requests.  I'm sure it was an MTU problem, but the only thing that every really fixed it was assigning a static LAN IP to the MAC on the laptop's wireless card!  Routers are strange beasts.

---

### Post by Mateo on 2008-01-19
here's the output of that command:

```
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination    
```

not sure what it means.

it's definitely not my ISP, unless my ISP decided to start blocking ports during the hour it took me to change routers.

the new router is both router and modem.  i did this to make things more simple.  hasn't worked out that way yet.

---

### Post by Mateo on 2008-01-19
I went to "http://www.canyouseeme.org/" and tested all of their common ports, for things like ftp, ssh, web, pop3, etc. and **none** of those worked either.  what the heck.

---

### Post by NullHead on 2008-01-19
The odd thing is that I have the same problem that you have, but let me describe to you my situation. The cable line comes into my cable modem and then it goes directly into my wireless/wired router - witch then goes to an 8 port witch with then goes to three wired computers .... there is also three wireless computers that connect wirelessly. Now two of the wireless computers are my desktop and my laptop. The ips that I use for my two wireless computers are 192.168.2.9(desktop) and 192.168.2.11(laptop) Now ports forward and function perfectly on my desktop but not on my laptop :confused: I also dual boot into windows and ubuntu gutsy. 

I'm stuck at the same problem that you're running into and I'm beginning to think that the ISP is blocking the number of ports open through the router as a security measure.

---

### Post by Mateo on 2008-01-20
bump

---

### Post by Mateo on 2008-01-25
bump

---

### Post by Mateo on 2008-01-26
bump.

---

### Post by Mateo on 2008-01-28
bump

---

### Post by Mateo on 2008-01-31
bump

---

### Post by NullHead on 2008-02-01
Please stop bumping it's going to make me get all upset. 

Anyways, search[ Portforward.com]("http://www.portforward.com/cports.htm") for you're application and forward the correct ports and see if that doesn't fix it :D

---

### Post by Mateo on 2008-02-01
Like I said before, this happens with any port I attempt to use.  Literally every last port I have tried has said blocked.  So I know it's not an ISP issue.  It's something about my particular router, something that I'm not familiar with.

---

### Post by NullHead on 2008-02-01
There should be a guide on that site for you're router and how to properly forward ports for you're exact router.

---

