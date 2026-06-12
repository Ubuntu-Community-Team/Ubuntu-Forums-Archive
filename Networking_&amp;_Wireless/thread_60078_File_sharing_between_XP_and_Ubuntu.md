---
title: "File sharing between XP and Ubuntu?"
date: 2005-08-26
forum: Networking &amp; Wireless
---

### Post by Unix_Wizard on 2005-08-26
Noob here. I have a laptop with XP. I would like to know if there is a way to create shared folders between the 2 comps. Currently all I can do is ping one from the other I have some shared folders on the XP (Which are set to be accessible). I can't see any shared folders of the other pc with any of them! Basicly I have samba (Atleast I think I do) but can't find a way to enter the ip and see the shared folders.

---

### Post by andlinux21 on 2005-08-26
I think in order to share files on the windoze box you would need at least a Fat32 partition somewhere I maybe wrong but someone I am sure has the answer to this for ya  :)

---

### Post by izmaelis on 2005-08-26
You can share any directory from your Linux box using samba server. Great how-to is located right [here](http://ubuntuguide.org/#sambaserver) on the Ubuntu Guide.
If both of your computers are in the same LAN, you can acces your Windows shares by browsing **Network Places** in your upper Gnome panel.
More details about how to access your Windows shares you will find [here](http://ubuntuguide.org/#accessnetworkfolderswihoutmount).

P.S. Try reading Ubuntu Guide more. You will find lots of useful stuff there.

---

### Post by Unix_Wizard on 2005-08-26
[QUOTE=izmaelis]You can share any directory from your Linux box using samba server. Great how-to is located right [here](http://ubuntuguide.org/#sambaserver) on the Ubuntu Guide.
If both of your computers are in the same LAN, you can acces your Windows shares by browsing **Network Places** in your upper Gnome panel.
More details about how to access your Windows shares you will find [here](http://ubuntuguide.org/#accessnetworkfolderswihoutmount).

P.S. Try reading Ubuntu Guide more. You will find lots of useful stuff there.[/QUOTE]
 Right thanks. By the way I manged to access shared files of the XP machine from ubuntu but I can't do the opposite!! I am quite sure this is related to ubuntu but it's from the xp machine. I input the ubuntu pcs network name (Or ip address it doesn't matter). When I'm prompted for a user/pass I enter my ubuntu account info and it fails! What am I supposed to do to let the xp machine into my ubuntu? 
btw: thanks for the links I think I messed up something to do with my locale when I tried to install some converted rpm is that relevant?

---

