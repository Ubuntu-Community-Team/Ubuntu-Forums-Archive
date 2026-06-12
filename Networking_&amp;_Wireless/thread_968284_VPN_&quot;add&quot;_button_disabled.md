---
title: "VPN &quot;add&quot; button disabled"
date: 2008-11-02
forum: Networking &amp; Wireless
---

### Post by Lord_Dicranius on 2008-11-02
I'm trying to configure a VPN to see if I just might be able to use Ubuntu on my work laptop.  I opened up the Network Connections window, selected the VPN tab, and the "add" button is grayed out.  Anybody know why this is?

I'm using Ubuntu 8.10 AMD64, desktop version, just installed this morning :)

---

### Post by Lord_Dicranius on 2008-11-02
Found my answer [here](http://ubuntuforums.org/showthread.php?t=96521) :)

---

### Post by Neofree on 2008-11-03
Some reason the linked thread the author was embarrassed?  I have no shame! what was it???  I need to get to work..

Thanks,

Neofree

---

### Post by Lord_Dicranius on 2008-11-03
Sorry about that Neofree.  I'm not booted into Ubuntu right now, so I'm trying to remember this off the top of my head.  But I think it was the "network-manager-pptp" package that I installed (pptp because that's what type of VPN I'm connecting to).  Found [another thread](http://ubuntuforums.org/showthread.php?t=965213) with pretty much the same answer.  Although that enabled my "add" button, I'm still having issues with connecting.  Much of the issues I'm having seem to have been issues with the Ibex testers too, all the way up until release - [see here](http://ubuntuforums.org/showthread.php?t=922362).

I gotta go find the launchpad page for this...

---

### Post by Lord_Dicranius on 2008-11-03
Weird... I pressed submit once and I got a forum error saying I gotta wait 20 seconds before posting.  It gave it to me a couple times within a 5 minute period.  When I finally got it to go through, it had already posted *shrug*

---

### Post by aggiemarine07 on 2008-11-07
you need to do this command:

sudo apt-get install network-manager-vpnc vpnc


and it should then allow you to add a vpn profile to ubuntu

---

