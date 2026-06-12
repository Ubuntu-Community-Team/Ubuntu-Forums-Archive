---
title: "Connecting two computers."
date: 2006-09-24
forum: Networking &amp; Wireless
---

### Post by jcrnan on 2006-09-24
I know that back before we had a router at home I connected my pc to the internet by a cable from my moms pc to my pc (hers was plugged to the net), We used windows back then and there was this easy setup for doing such in the networking wizard.

Now Im using two ubuntu machines I need to get this working again :) Any help on how to connect a desktop pc (trough network cabel) to my laptop so the desktop recives internet from the laptop (wich gets it wirelessly trough built in network card)?

I really need help on this :)

---

### Post by JohnW on 2006-09-24
Hardware: You need a 2nd network interface on your laptop and the same crossover rj45 cable I imagine you used before will connect the two computers.

Software: your laptop needs to act as a router.  Lots of ways to do that with Linux, one I've used is Firestarter.  Has a nice gui interface.  Use Synaptic to get it (not sure which repository, I normally enable all of them in Settings|Repository and press Reload).  Or apt-get install firestarter.

---

### Post by JohnW on 2006-09-24
Sorry, I just realised I didn't read carefully enough -- you need the routing software in hers, not yours, if you want it that way round.  But you'll also need a wireless access point if you don't want to run a cable between the two computers.

Wouldn't it be simpler just to have a wireless router connected to the internet, serving both pc's?  Prices of them have got so much cheaper over the past couple of years.

---

### Post by jcrnan on 2006-09-24
you misunderstood a little :)

I need it connected like this:


cable modem---router+++++++++laptop------desktop

--- = network cable
+++ = wireless

Now, I already have the laptop connected. I just need the desktop connected to the laptop so it also can get acsess to net. I dont have any wireless connection availible for the desktop as of now. 


But yeah, if I just connect them with a cable and install firestarter on the desktop it should work?

---

### Post by jcrnan on 2006-09-25
noone here that knows?

---

### Post by mips on 2006-09-25
I would connect the Desktop directly to the router if I was you.

With your scenario the desktop would only have internet connectivity when your laptop is home and switched on.

Anyway, to answer your question install Firestarter, it's in the repos. Next enable Internet Connection Sharing (ICS).

[http://www.fs-security.com/](http://www.fs-security.com/)
[http://ubuntuforums.org/showthread.php?t=89278](http://ubuntuforums.org/showthread.php?t=89278)

---

### Post by jcrnan on 2006-09-25
I would have already done that if it was possible ;) But the router is on a different floor, etc. But yeah, Im gonna try the firestarter thing then, even tough it just looked like a firewall at first glance.

---

### Post by Iowan on 2006-09-25
> **jcrnan said:**
> 
But yeah, if I just connect them with a cable and install firestarter on the desktop it should work?
I could be mistaken, but Firestarter would be installed on the laptop (to make it a router), not on the desktop.  It would seem cleaner to connect from the desktop to the router - but looks like that't either mean getting a wireless card, or hardwiring from desktop to router.

---

### Post by mips on 2006-09-25
Yes, in this scenario firestarter must be installed on the laptop.

---

### Post by JohnW on 2006-09-26
> **jcrnan said:**
> I would have already done that if it was possible ;) But the router is on a different floor, etc. But yeah, Im gonna try the firestarter thing then, even tough it just looked like a firewall at first glance.

It's a firewall, but can also act as a router for other PCs connected to it.

However, if I had the same problem I'd just spend a tenner (UKP) (about $18 US ).  E.g. [http://www.aria.co.uk/ProductInfoComm.asp?ID=22699](http://www.aria.co.uk/ProductInfoComm.asp?ID=22699)
is a USB2 wifi dongle.  Plug it in the PC and you have internet whether or not the laptop is around.

---

### Post by jcrnan on 2006-09-26
Its three times that price here and its not meant as serious going to work with computer :P Its an old piece of crap that I tought I would have around for testing cutting edge stuff and such and not caring wether or not I broke anything.

I think I know how to get it working now tough, I just need to get the right cable first.

---

