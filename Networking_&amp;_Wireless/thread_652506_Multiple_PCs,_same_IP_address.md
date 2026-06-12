---
title: "Multiple PCs, same IP address"
date: 2007-12-28
forum: Networking &amp; Wireless
---

### Post by Rhemat on 2007-12-28
Hi,

  Hopefully this has not been posted before, but I searched and could not find any topics about such.  Anyway, I have a couple of PCs hooked up to a couple of routers, and they both share the same IP address.  I first noticed this when they were on an Actiontec GT704 WG model DSL modem/wireless router.  I tried getting help from TDS (my service provider) but when I happened to mention that I use Linux, the operator told me that their policy says the problem is on my end.

  I later purchased a Belkin F5D7230-4 wireless router, and have one machine hooked up to it, and my main one hooked into the Actiontec, but they still share the same IP address.  I'll later try plugging in both into the Belkin, see how that turns out, but I was hoping that someone may have some suggestions.

  Would setting one (or both) up for static IP address help?  Is there some other configuration method?  Is there a cheap wireless DSL modem/router that I could use to replace them?

Thanks in advance for your help.

---

### Post by mightyteegar on 2007-12-28
Can both machines access the Internet?

---

### Post by Rhemat on 2007-12-28
Yes, I was able to use the internet on both machines.

---

### Post by mightyteegar on 2007-12-28
1.  Do your machines have IP addresses that start with 192.168 or 172.xx or 10. ?  

2.  How are the routers connected?  Is it something like this?

```
[R1]------[R2]------[PC2]
 -
 -
 -
[PC1]
```

---

### Post by Rhemat on 2007-12-28
My main machine IP starts with 69.130, and the other's I'm uncertain of.  I go to the Belkin's setup page, and it gives me the fake IP of the Belkin, and when I go to the Actiontec, it's the same as the main machines.

As for how're they're hooked up, yes that's about it.  My main machine is hooked up to the Actiontec, the Actiontec feeds a line into the Belkin, and the other machine is hooked up to the Belkin.

---

### Post by jamescondron on 2007-12-28
Do I have this right? All your machines are showing the same *external* ip address, that is to say from the internet, they all just appear to be one machine?

If so, thats what happens on a router, basically the router is the only computer online in this sense, it merely 'routes' the packets for each box (connected to the router) to where they were requested from.

---

### Post by jflaker on 2007-12-28
Since you are using Network Address Translation, it is possible that two systems on two different routers could be given the same IP address.  

Consider each router as a box.  Any machine inside each box must have a unique IP address.  They must also be on the same subnet to be able to communicate with each other.

Two or more boxes can be connected to each other and each machine in each box should be able to  reach machines in the other box, even with the "same" IP address.......they are independent networks.

My machine has a 192.168.1.x address too.......


So, recap......
each box is an independent network
each IP inside a box must be a unique address 
IP's in different boxes can be the same.
The router handles proxying the communications to the internal IP's through Network Address Translation (NAT)

---

### Post by Rhemat on 2007-12-28
Actually the only way I'm able to check this is from my routers setup pages.  I know that the IP address that the Actiontec spits out is right because I use that number to play Quake 3 matches ages ago with a friend.

I'm trying to learn how to network and share information between several computers by starting out small, but it appears that I still lack necessary information for such.

I do appreciate all the help that you all have offered, and hopefully I'll sort this mess out.

---

