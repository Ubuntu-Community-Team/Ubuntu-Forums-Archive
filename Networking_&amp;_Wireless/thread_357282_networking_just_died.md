---
title: "networking just died"
date: 2007-02-09
forum: Networking &amp; Wireless
---

### Post by joesnow on 2007-02-09
I'm not familiar w/ debian-based systems, I've been using RH, but since I got a new system I put Ubuntu on my old Opteron.  All was going well, I installed the desktop iso of 6.10, installed some QEMU, put windows on it, and right at the end of the windows install I rebooted cuz I also did   apt-get update; apt-get upgrade.  When the system came back up "network-admin"'s icon in the system menu in gnome was gone, along with a few others that I can't think of cuz I'm more concerned w/ the networking.

Before, the networking worked fine, i was able to browse the web, copy files around, etc.  Now I can't even ping my router.  As far as I can tell, networking is setup ok.  I looked @ /etc/resolv.conf and /etc/network/interfaces and all seems well.  ifconfig returns normal info for my static ethernet, and the DHCP one doesnt get an ipv4 IP but it gets an ipv6 one somehow.  I don't know what happened, and in an hour of messing w/ it I can't seem to fix it.  I've rebooted twice since.  One particular thing that may be a little different is i disabled the gdm service (although I wouldn't expect that to make a difference).

what should I do? I'm not sure how to proceed considering things are in slightly different places than I expect them to be.

---

### Post by alan_nunn on 2007-02-20
I have also just realised that my Networking option has vanished. I can't for the life of me work out why. I am guessing it was to do with a recent update. I can still edit the options via /etc/network/interfaces but i want my networking back in the administration menu. I'm running Edgy 6.10 Ubuntu, on a ThinkPad R50e. 

Alan

P.S Starting to get annoyed now

---

### Post by alan_nunn on 2007-02-20
Right I have worked out how to get the Networking back. You need a Internet connection to do this.

Simply go into Synaptic and search for Gnome-System-Tools, tick it and install it and bingo. It worked for me. I don't how I managed to fix this myself. I still don't know why it disappeared in the first place.


Hope this helps somebody.

Alan

---

### Post by batholith on 2007-02-20
deleted...sorry wrong post!

---

### Post by alan_nunn on 2007-02-24
Has anyone else had this problem?

---

