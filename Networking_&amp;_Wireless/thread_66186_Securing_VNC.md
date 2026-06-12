---
title: "Securing VNC"
date: 2005-09-16
forum: Networking &amp; Wireless
---

### Post by Kyral on 2005-09-16
Hey. I use VNC to connect to my desktop in my dorm when I'm in the computer labs at school. Now I'm kinda paranoid (with good reason) that the VNC connection isn't secure, even though it doesn't leave the school net at all (I tracerouted it). I plan on doing an Ethereal trace on it later after class.

Anyway if I find that it is transmitting in the clear, how can I secure it? Thanks :D

---

### Post by KingBahamut on 2005-09-16
VNC is pass authed, or it should be. Just use secure passwords. I suppose if your really really insecure, you could forward the port to a non standard VNC port. Standard I think is 5900 to 5910 for the hard client, and 5800 to 5810 for the Java client if enabled.

---

### Post by Kyral on 2005-09-16
Its pass authed, (and they would have to get past my screenlockout as well), but the VNC pass isn't very secure (its not dictionary words, but it isn't an insane amount of randomness). But what I'm worried about is the actual bitstream between the client and my desktop. I wanna know if THAT is in the clear, 'cause if someone has a packet sniffer aimed at me, it won't matter if the password is there or not. I eventually plan to put an IpTables rule into effect that would block all VNC connections from off campus.

I'm also using the default server client on GNOME, and vncviewer in the labs.

I've been thinking about talking to the guy incharge of the lab build of Gentoo about installing a FreeNX client, 'cause I heard it was faster than VNC. Is it also more secure?

---

### Post by jimcooncat on 2005-09-16
[QUOTE=Kyral]But what I'm worried about is the actual bitstream between the client and my desktop. [/QUOTE]

There are lots of tutorials on the net about tunnelling VNC through SSH. Here's one:
[http://pigtail.net/LRP/vnc/](http://pigtail.net/LRP/vnc/)

[QUOTE=Kyral]I've been thinking about talking to the guy incharge of the lab build of Gentoo about installing a FreeNX client, 'cause I heard it was faster than VNC. Is it also more secure?[/QUOTE]

This also tunnels a session through SSH. So yes, it's more secure because it encrypts the data stream. It's faster because it uses a more efficient protocol than VNC when doing a Linux to Linux connection. The client can also be used to connect to a VNC server if you want to (like on a Windows computer, or if you want to forward the :0 display).

---

### Post by KingBahamut on 2005-09-16
FreeNX might be more secure, but I dont have much experience with it. 

Id use tcpdump to an output over ethereal, I find it easier to deal with than ethereals interface , if yoru concerned about sniffing out the traffic.

---

### Post by bugmenot on 2005-09-16
[QUOTE=Kyral]I've been thinking about talking to the guy incharge of the lab build of Gentoo about installing a FreeNX client, 'cause I heard it was faster than VNC. Is it also more secure?[/QUOTE]

Yes, it's significantly faster on either GNOME or KDE. The only WM I found VNC to be faster with was fluxbox with a flat theme on the local network. But even there scrolling webpages is kind of jerky, which it won't be with NX on the LAN.

NX is using a multi-tiered approach for security. It initiates the connection over SSH, where you can exchange the default public key with your own. Even without a custom key, all traffic is encrypted with SSL after password authentication.

See [here](http://www.nomachine.com/ar/view.php?ar_id=AR02C00150)

And by the way, VNC traffic isn't encrypted at all. You can tunnel it over SSH, but that is even more sluggish.

---

