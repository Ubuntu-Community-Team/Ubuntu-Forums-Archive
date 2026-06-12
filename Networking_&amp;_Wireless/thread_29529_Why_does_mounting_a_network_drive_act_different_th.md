---
title: "Why does mounting a network drive act different than browsing?"
date: 2005-04-24
forum: Networking &amp; Wireless
---

### Post by MetalMusicAddict on 2005-04-24
I noticed that "mounting" a network drive makes apps act differently from "browsing" it.

ie: With Xine if I try to watch a video when I use the network browser it gives me a error. "There is no MRL" but If I mount the drive and go to the same folder through "Computer" everythings fine.

This changed from Warty to Hoary for me.

Does this have anything to do with SMB? And why doesnt Samba come installed by default?

---

### Post by crazybill on 2005-04-24
Check out [http://www.ubuntuguide.org/#sambaserver](http://www.ubuntuguide.org/#sambaserver) 

The ubuntu guide was recently updated concerning SMB setup.

---

### Post by MetalMusicAddict on 2005-04-24
[QUOTE=crazybill]Check out [http://www.ubuntuguide.org/#sambaserver](http://www.ubuntuguide.org/#sambaserver) 

The ubuntu guide was recently updated concerning SMB setup.[/QUOTE]
I dont need to know how its setup (got that down) I'm wondering about its behavior.  ;-)

---

### Post by king20878 on 2005-04-25
When you mount the drive through fstab, it is seen by the entire OS as an attached filesystem, so any program can access it.  If you are browsing it with Nautilus, it's not really mounted so only those programs that are 'Gnome aware' i.e. those that are integrated with Gnome can see it, e.g. Totem can, but not Xine or XMMS.

---

### Post by moopere on 2005-04-25
[QUOTE=king20878]When you mount the drive through fstab, it is seen by the entire OS as an attached filesystem, so any program can access it.  If you are browsing it with Nautilus, it's not really mounted so only those programs that are 'Gnome aware' i.e. those that are integrated with Gnome can see it, e.g. Totem can, but not Xine or XMMS.[/QUOTE]

Even worse is that you can't really tell which apparently gnome programs are -really- gnome integrated in this way.  gpdf isn't for instance, gedit is.  Openoffice (1.x or 1.9x), which doesn't pretend to be a gnome app admittedly, certainly doesn't work.  

Anyone aware of any gnome centric way to mount  a samba share from a gui?  I sniffed around for most of today trying to find a way - the only thing that comes close is smb4k (for KDE) which is a pretty heavy hit if you don't already use kde apps (you'll need a bunch of kde libs to run it).

For those with a KDE desktop, get smb4k right now, its fantastic for situations where you have multiple samba shares and regularly like to surf them (ie, you are not fond of a heap of static mounts).

Cheers,
Craig

---

### Post by MetalMusicAddict on 2005-04-25
[QUOTE=king20878]When you mount the drive through fstab, it is seen by the entire OS as an attached filesystem, so any program can access it.  If you are browsing it with Nautilus, it's not really mounted so only those programs that are 'Gnome aware' i.e. those that are integrated with Gnome can see it, e.g. Totem can, but not Xine or XMMS.[/QUOTE]
Ahh... Makes sence.

What about that new option in Hoary? In the places menu "Connect To Server...". Is that "Mounted"?

---

### Post by doclivingston on 2005-04-26
Nope, "Connect to Server" will still only affect Gnome programs. Sorry, I can't think of any easier way to do it for Gnome than mounting it.

---

