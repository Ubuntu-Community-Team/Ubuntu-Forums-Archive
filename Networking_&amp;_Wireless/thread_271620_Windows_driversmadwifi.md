---
title: "Windows drivers/madwifi?"
date: 2006-10-04
forum: Networking &amp; Wireless
---

### Post by zombie_st on 2006-10-04
Okay, after troubleshooting for the wrong things few times and misreading my own handwriting, I think I know what I need to get my wireless up. I just can't find it.

Can anyone direct me to where I can find the Windows driver BLKWGN.inf for my Atheros AR5211 card, as I'm listed as needing it here: [https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

I've no driver cds and no clue where to find it. Google isn't finding it for me, and the Atheros and Belkin sites are giving me no love.

Alternately, I'm guessing the answer is "no" but is there any possibility madwifi would help with this? I thought it was already part of Ubuntu...

Open to any help, comments or suggestions, of course, even if it's just "give it up and find a new card". Thanks a bunch!

---

### Post by x64Jimbo on 2006-10-05
You guessed right with the madwifi question. Madwifi support is one of the best wireless solutions in the Linux world. I highly recommend using madwifi.
As for how, check this out:
[http://madwifi.org/wiki/UserDocs/Distro/Ubuntu](http://madwifi.org/wiki/UserDocs/Distro/Ubuntu)

---

### Post by zombie_st on 2006-10-06
> **x64Jimbo said:**
> You guessed right with the madwifi question. Madwifi support is one of the best wireless solutions in the Linux world. I highly recommend using madwifi.
As for how, check this out:
[http://madwifi.org/wiki/UserDocs/Distro/Ubuntu](http://madwifi.org/wiki/UserDocs/Distro/Ubuntu)

Thanks for the reply and the link! Being an utter newbie at this, though, I /do/ have a few follow-up questions. Hope you (or whoever else is passing by) can have a bit of patience with me!

I've been running a fresh default install of Breezy Badger, and looking at the top of the page you linked me to, it seems that if my card could work with just madwifi, then it would Just Work out of the box? I also got the impression looking again at the page I linked to earlier that the ndiswrapper + Windows driver fix was supplied because madwifi /isn't/ enough to get my particular card working. It is entirely possible that I'm reading this wrong. Are there additional madwifi components I can download and install that aren't already built in to Breezy Badger? And if so, is there a handy tutorial somewhere on how to put it on my laptop without already having any sort of net connection? I'm currently writing all this from a net cafe's comp, and will have to have someone else download and burn my necessary packages to do /anything/, so the wget and apt-get install instructions are not an option for me.

Looking forward to any thoughts anyone has on this. Thanks for your time!

---

### Post by x64Jimbo on 2006-10-06
You don't have ethernet connectivity either?
In regards to the madwifi issue, everything should be set to go - let's see if you just don't have the module loaded yet...
sudo modprobe ath_pci

---

