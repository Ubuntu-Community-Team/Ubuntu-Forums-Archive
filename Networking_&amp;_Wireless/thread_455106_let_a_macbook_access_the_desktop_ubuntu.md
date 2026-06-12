---
title: "let a macbook access the desktop ubuntu"
date: 2007-05-26
forum: Networking &amp; Wireless
---

### Post by fabbaz on 2007-05-26
hey
i would like my macbook to have complete access on my personal files on my linux desktop when inside of the network.
i have a ubuntu 7.04 desktop machine, connected to the router via cable, and the macbook connected to the same router via w-lan.
i want to be able to use the desktop as "media server", and the mac to have access to its files whenever i am logged in/ the desktop is on.
it worked to connect via ssh, but that is just annoying. besides, i only was able to access the macbook from the ubuntu box, which i don't really care about at all. 
i already tried to use nfs file sharing on specific folders, with no success. i am starting to get really frustrated with this, so i am asking for help ...
i thought it could be able with avahi/zeroconf/bonjour, but after installing the components via synaptic i got stuck because i wouldn't know what to do with them. netatalk didn't work either. besides: all of this is not what i want.
is there a way to just have ubuntu constantly share folders to who ever is in the network, without any further clicks?
it works fine with windows and mac, but windows i do neither have nor want to install ever again.

thanks!

---

### Post by fabbaz on 2007-05-26
yeay!
what i now did, which worked, was connecting to the ubuntubox via <apple-K> in finder. so i connected to the ip-adress of my desktop, and then, after logging in with my ubuntu-account, could simply drag'n'drop from the desktop to the laptop.
this is not 100%ly what i was looking for, but i am for now totally satisfied though :)

---

