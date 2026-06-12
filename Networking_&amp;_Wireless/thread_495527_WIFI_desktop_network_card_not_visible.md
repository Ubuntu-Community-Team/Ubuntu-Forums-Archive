---
title: "WIFI desktop network card not visible"
date: 2007-07-08
forum: Networking &amp; Wireless
---

### Post by moaxey on 2007-07-08
its one that should work out of the box in feisty 
Netgear WPN311 <http://ubuntuforums.org/showthread.php?t=377148>

restricted modules are installed
there's no lights on, 
nothing about it in ifconfig or iwconfig
no mention of it in dmesg
nor lspci 

which doesnt leave ne a lot to go on?

---

### Post by waster on 2007-07-08
have you tried the card in another computer?
Is it a PCI card?
Have you tried different PCI cards in the same slot in that computer?

---

### Post by Lowell Boggs on 2008-01-15
I just bought a referb hp pavilion s3200N and put the 64 bit version of gutsy on it.

However, when I installed the os, I did not have the wired lan cable connected.  The network manager correctly set up the wireless network -- which has some sort of s/w bug that was recently patched.

However, I can't see my eth0 card.  Network manager acts like the builtin NIC just isn't there.

Is it possible that my failure to attach the ether net cable to the computer when I installed gutys caused it to think that there was no card?

Any other ideas?

Thanks,
  Lowell

---

### Post by Lowell Boggs on 2008-01-16
This turned out to be a stupid-Lowell trick:

I had two problems:  1.  I forgot to plug my wired network cable in when installing linux
                              2. When I did install it, I plugged in either a normal phone cable or
                                   a bad ethernet cable. I can't tell which since the cable I used
                                   came with the computer -- its in the trash now.

Sadly, the only way I could diagnose this problem was to install windows and let it diagnose the problem, then re-install ubuntu.

If someone would tell me what commands I could use to check the physical h/w, I'd be h appy to write a script and post it.  That is, a script to diagnose the existence of h/w which is disabled and why.

The system logs didn't say why I had a problem only that I didn't have a signal -- this could have meant anything -- like the card was configured wrong...

---

