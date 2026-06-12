---
title: "Fiesty Fawn Wireless Issue - Need Delayed Startup?"
date: 2007-04-17
forum: Networking &amp; Wireless
---

### Post by RDAC on 2007-04-17
Hi, got two boxes running Fawn right now, and both are experiencing a weird issue.

When I start them up, they don't want to connect back to their networks. In fact, the wireless just acts stupid for a while and says it can't find any other networks.

As soon as I turn off wireless networking (around 2-5 minutes after the computer has booted) and turn it back on, it finds it like a champ.

What's going on, and can someone suggest a workaround? I thought something that would disable the adapter on shutdown and enable it after startup, maybe with a 15-30 second delay or something.

Any help is appreciated, and thanks in advance!

PS: Other than this minor issue, I've had a blast with this release. It's been the easiest to set up so far (former SUSE & Fedora user), and the suggestions I've got off the forum have allowed me to completely move off of my windows system for disc printing and duplication. Thanks again to the community!

BTW, one card is an AirLink+, and the other is a bad, bad broadcom chipset.

---

### Post by samopal on 2007-04-18
exactly same problem on my notebook, xubuntu 7.04 feisty, 64bit 
from the beginning I was disabling/enabling wireless card in settings, but later I wrote this script> 

#!/bin/bash 
echo "Resetting network..."
sudo cp /etc/network/interfaces /etc/network/interfaces.bak
sudo cp /etc/network/interfacesMSI /etc/network/interfaces
sudo /etc/init.d/networking restart 
echo "[ OK ]"

if you are using only one wireless network, delete two rows with ¨cp¨, i´m using them only because i´m using 3 different wireless networks often.

---

### Post by RDAC on 2007-04-18
Awesome! Worked like a charm. Thanks for all the help.

:guitar:

---

### Post by samopal on 2007-04-18
> **RDAC said:**
> Awesome! Worked like a charm. Thanks for all the help.

:guitar:


yop, but that's only workaround... :(  
if someone has REAL solution please post it. 
or should this be reported as bug ? :confused:

---

