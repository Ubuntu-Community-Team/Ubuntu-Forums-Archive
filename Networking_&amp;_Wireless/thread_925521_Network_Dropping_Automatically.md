---
title: "Network Dropping Automatically"
date: 2008-09-20
forum: Networking &amp; Wireless
---

### Post by Mr.Macdonald on 2008-09-20
I just installed Ubuntu 7.04 on my Via Artigo system and ran into a (big) problem.

My internet doesn't work unless i run this
```
sudo /etc/init.d/networking restart
```

and after i run that i only can connect to the internet until the network manager says (after finding a network)
> Connection Established
in a pop-up window


I ran update manager, updating in chunks of packages (the net drops). and reinstalled everything involving the network (I'm desperate).

It almost seems that my problem in the Network Manager. Should i uninstall it (net manager)?? Should I use Fedora or Debian instead, because the Hardy CD didn't kept stalling my system (I have a gig of RAM)??


PS. if anyone has used a Artigo and knows how to configure the BIOS, I would appreciate it, because I can't boot a live CD. Meaning I am stuck and screwed with 7.04

---

### Post by Crafty Kisses on 2008-09-20
Is this wireless or through ethernet?

---

### Post by Mr.Macdonald on 2008-09-20
Wired connects with above problem
Wireless claims it has connected but didn't

A temporary solution was to uninstall network-manager and is functioning very nicely

---

