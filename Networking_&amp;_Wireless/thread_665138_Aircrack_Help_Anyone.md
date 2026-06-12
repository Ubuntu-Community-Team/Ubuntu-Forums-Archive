---
title: "Aircrack Help Anyone??"
date: 2008-01-11
forum: Networking &amp; Wireless
---

### Post by kevdog on 2008-01-11
Ok - I finally broke down -- I just wanted to see if I could use aircrack-ng and aircrack-ptw to crack my networks WEP code. Call it the Geek in me. 

Im using an Atheros chipset with the patched madwifi sources for packet injection.

Ive run into two problems along the way

My network used a 64bit WEP shared key.  This is causing me problems with fake authentication. 

Also, using a known MAC on the network to authenticate, I proceed to starting aireplay-ng in a mode which listens for ARP requests then reinjects them back into the network.  To start receiving ARP requests, I initiate a PING request from another computer on the network, however the minute I do this (everytime in fact) I get a:

Got a deauth/disassoc packet. Is the source mac associated?

I just cant seem to get over this hump!

---

### Post by kevdog on 2008-01-12
Help??  

Maybe I should post on the aircrack-ng forum?

---

### Post by wieman01 on 2008-02-05
Kevdog, 

Have you ever tried my own WEP crack tutorial? We could continue the discussion from there if you like.

---

### Post by kevdog on 2008-02-05
Wieman

I kind of took a break from this topic for a while.  I managed to get my Atheros in monitor mode and set up the virtual interface using the patched madwifi drivers as reported on the aircrack-ng site.  My problem was with the attacks.  I went through the basic attack and it didnt work.  I want to do packet injection to speed up the process, however everytime I use this technique, my connection is immediately dropped.  Im sure Im doing something wrong b/c Im just learning about the whole process.  I didnt know if I could connect to the AP with my current MAC, or I needed to sniff the MAC address of another computer currently connected to the network and use that MAC address.  This is the point I became confused.

---

### Post by wieman01 on 2008-02-05
Hi Kev, 

Alright, got it. So if there are still questions, let me know, perhaps we can discussion them here. I went through the whole process at one stage, I have to refresh my memory a bit, but the guide should be very clear on these things. 

If MAC filtering is enabled, you have to clone a permitted client's MAC address and then establish a connection. Otherwise you don't have to worry about it. That's it.

---

