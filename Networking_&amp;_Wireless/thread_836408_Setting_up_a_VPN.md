---
title: "Setting up a VPN"
date: 2008-06-21
forum: Networking &amp; Wireless
---

### Post by solwic on 2008-06-21
I'm wanting to set up a VPN server.  I've read lots of tantalizing hints that it can be done with Hardy Heron (and Ubuntu in general) but I've not found any real instructions.  Lots of archived posts here on the forums where the OP didn't get any help, or the thread just stops, like the OP found what he/she was looking for and didn't post again to let anyone know about it.  

I imagine there's a lot to do with setting up a VPN, so what I'm really looking for are good, easy to follow instructions.  I don't mind reading and troubleshooting...I just don't know where to go to find the information I need.

I've seen a lot of these threads go dead on the forums here, but I'm banking on hope.  ANY help would be absolutely wonderful.  

Thanks!

---

### Post by inportb on 2008-06-21
You might want to check out [OpenVPN]("http://openvpn.net/"); it runs on many platforms, has many options, and has good documentation.
[OpenSSH]("https://help.ubuntu.com/community/SSH_VPN") has potential, but its VPN applications are currently quite limited.

---

### Post by SpaceTeddy on 2008-06-21
i agree with inportb 100%. as for a tut, check this [[COLOR="Blue"]thread[/COLOR]]("http://ubuntuforums.org/showthread.php?t=812065") out. I've written quite lots there, including a simple post on howto get openvpn up and running (i think it's the third post).

hope it helps (a little) :)

PS: if any questions are left after this, just ask here and i will try my best to answer them :)

---

### Post by solwic on 2008-06-21
Ok I think I might have gotten my terminology confused.  What I need done is a simple way to establish a private, secure connection between two or more computers over the internet that allows for sharing and/or editing files.    

Any help with that?  Sorry for the confusion, if there is any.  :)

Thanks!

---

### Post by inportb on 2008-06-22
If all your files are to be contained on one server, then a regular SSH session should be good enough for your purposes.

---

