---
title: "Wireless Setup"
date: 2006-08-03
forum: Networking &amp; Wireless
---

### Post by KDayz on 2006-08-03
Hello All. I'm a complete noob. Just dual-booted linux about 1 hour ago and I'm trying to setup my wireless internet on my laptop. The wireless card came with the laptop so I dont know how to find the name of it. Can someone please help me out on how to find the name and then setting this bad boy up. So far I love linux.

---

### Post by Fass on 2006-08-03
```
sudo lspci
```

In a terminal. Somewhere in the list will be your wireless card. Do a forum search on its name to see if there is a guide (there probably is) on how to make it work.

---

### Post by KDayz on 2006-08-03
hmm. i typed that in the terminal. One of the results was:

Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

Would this be it?

---

### Post by Fass on 2006-08-03
Yup, [and here is just one guide on how to make it work.](http://www.ubuntuforums.org/showthread.php?t=185174&highlight=broadcom)

There are many others in the fora - just do a search for broadcom if you don't like the one I linked to.

---

### Post by KDayz on 2006-08-03
Thanks alot for the help mate! You helped me alot and unlike other places didnt bitch about how I should search first and stuff. I like the community here and people like you make it better. :)

---

### Post by Cure777 on 2006-08-03
> **Fass said:**
> Yup, [and here is just one guide on how to make it work.](http://www.ubuntuforums.org/showthread.php?t=185174&highlight=broadcom)

There are many others in the fora - just do a search for broadcom if you don't like the one I linked to.

When I did the 'lspci', i got the same thing, but this guide didn't help for one reason: How am I supposed to get stuff of synaptic package manager..etc, when I don't even have a connection ?!?!?

---

### Post by Fass on 2006-08-03
> **KDayz said:**
> Thanks alot for the help mate! You helped me alot and unlike other places didnt bitch about how I should search first and stuff. I like the community here and people like you make it better. :)

On second perusal, it seems that guide doesn't work well for 4318 cards... sorry, should have read more closely myself. No biggie, as there are others if you search for "broadcom 4318".

---

### Post by Fass on 2006-08-03
> **Cure777 said:**
> When I did the 'lspci', i got the same thing, but this guide didn't help for one reason: How am I supposed to get stuff of synaptic package manager..etc, when I don't even have a connection ?!?!?

There are guides out there to make the broadcom cards work with ndiswrapper, which is available on the Ubuntu CDs.

That may be a route. That, or using a wired connection while setting up the wireless. Or downloading the required packages from [http://packages.ubuntu.com/](http://packages.ubuntu.com/) in an OS that the card works in and then access the partition from ubuntu and use them. Or burn them to CD from a comp that has a connection.... and so on...

---

