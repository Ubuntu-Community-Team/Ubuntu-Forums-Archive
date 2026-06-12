---
title: "How to select 3G network (operator/type) on Intrepid?"
date: 2008-11-03
forum: Networking &amp; Wireless
---

### Post by MarioFrick on 2008-11-03
Hello,
I looked for this kind of information but I couldn't find anything googling around.

The issue is the following: I've a Vodafone Huawei connect card which I use with different Italian operators (Vodafone, Wind, 3). It works out of the box on Intrepid, but I cannot see which type of network it's actually using (GSM, UMTS/HSDPA), I cannot force it to use the 3G network instead of 2G and I cannot select the network (3 has national roaming on TIM network, it's important to be sure it uses the 3 network otherwise you pay a lot of money).

I think I solved the network selection by putting the network code, such as 22299 for 3, but still I cannot see which type of network it uses and cannot force it to use 3G.

Any idea? 
Thanks in advance

---

### Post by Plumtreed on 2008-11-03
I'm in the UK using the 3 network and always got connected to their GSM network. In Vista I connected to their 3GM network so I copied the APN from Vista to NetworkManager and used 'three' as the password. I don't think the password matters but switching to the other APN made the difference.

After changing the APN it took a few tries before it actually connected and initially it was very, very slow,so be patient. Now it is ok and works well and, at times, quite fast.

---

### Post by MarioFrick on 2008-11-03
It's not a matter of APN, of course I put the correct APN, but here 3 has only 3G network but can roam on another national network (TIM), but at a high cost (and slow speed). So it's important to know which of the 2 networks you are connected to.

---

### Post by Plumtreed on 2008-11-03
I also thought I had the correct APN, in fact, the NetworkManager Wiki was very specific about which APN to use! It wasn't till I changed the APN that I got onto the specific network I wanted. I can now choose either ,which is, in fact, forcing it to select the one I want. ,

---

### Post by MarioFrick on 2008-11-04
Ok, I solved using [UMTSmon]("http://umtsmon.sourceforge.net/"), it does all the things I needed! :)

---

