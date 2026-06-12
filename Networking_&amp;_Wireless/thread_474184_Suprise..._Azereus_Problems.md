---
title: "Suprise... Azereus Problems"
date: 2007-06-14
forum: Networking &amp; Wireless
---

### Post by shepppard on 2007-06-14
Al right so here is my issue. 
Port forwarding on my router... set
Static IP on my Linux Box... set
Green faces across the board in Azereus... set
Downloading... OOOOH wammy.

so why is this not downloading? Everything is configed. Yes my static IP is set up for the right address. My down speed started at like 4 Kb/s and then... died to 0... and my upload isnt going either. What is wrong with this?

Any ideas?

Cheers

---

### Post by shepppard on 2007-06-14
Screw this... I'm going back to Windows...

---

### Post by PilotJLR on 2007-06-14
I can't tell if you're really asking for help or just trolling... but here are a couple questions that I can think of:

I see you already did the port forward, but did you also run the NAT Configuration test in Azureus? To make sure the correct port and protocol is forwarded...

Also, is there any error of any kind, or just a stopped download?

Lastly, how do you know the torrent is even healthy?

---

### Post by shepppard on 2007-06-14
Had the torrent downloading when windows was running on my system and it ran fast. Gave the Same IP adress to the new linux install. Did the Nat test in Azureus and it said ok. Starts downloading and then it goes to 0 pretty quickly...
I'm completely frustrated this is the only reason I have this computer.

---

### Post by fdrake on 2007-06-14
try another program. i used azureus and i wasn't really that happy. now i am using freeloader, very simple but much faster than azureus for me and less ram consuming. 
sudo aptitude install freeloader

---

### Post by shepppard on 2007-06-14
Did not work

Yay... this is ridiculous

---

### Post by fdrake on 2007-06-14
this is kind of confusing. would you be so kind to attach the torrent file in your next post ??

---

### Post by shepppard on 2007-06-14
Alright guys thanks for your help and all but this really isnt working and it REALLY makes no sense.
I'm not a retard when it comes to computers but this just does not add up. 
The Torrent is healthy... I sent it to a friend and he downloaded it no prob.
I had no Nat Error in the beggining when it dint work but now after screwing around with everything all I am getting is a NAT error. 
My static IP is rather screwed up too or this Distro just does not like me or something.
The ports are forwarded... I went to Portforwarding.com just to make sure again. Reset my router and redid the port forward and it still does not work
I've tried just about every single Linux Bittorrent manager... none of them work.
I DO NOT HAVE A FIREWALL just to make sure that that was not in the way

I had a green Nat when this all started... I dont know why its screwed up now

EVERYTHING should be working. IF any one has any Ideas on how to fix this... then go ahead and try to figuere it out....

In the meantime I'm going to be installing windows.
Thanks for the help

---

### Post by irishstu on 2007-06-14
> **fdrake said:**
> try another program. i used azureus and i wasn't really that happy. now i am using freeloader, very simple but much faster than azureus for me and less ram consuming. 
sudo aptitude install freeloader

I agree with fdrake. I had several problems with Azureus, first in Fedora Core, then when I switched to Ubuntu. Maybe Azureus (running on Linux) and my router just don't like each other (oh and btw, Azureus works fine on my Windows partition).

Anyway, I tried a lot of things and I just couldn't get it to work right, then I switched to ktorrent and had tremendous speeds within a few minutes. Even faster that I have with Azureus on Windows.

---

