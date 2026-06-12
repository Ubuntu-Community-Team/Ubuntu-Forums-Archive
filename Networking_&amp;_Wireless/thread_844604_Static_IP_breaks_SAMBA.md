---
title: "Static IP breaks SAMBA"
date: 2008-06-29
forum: Networking &amp; Wireless
---

### Post by dardack on 2008-06-29
Ok if I use DHCP on the file server I just set up using Ubuntu Server, both my windows laptop and my ubuntu laptop can read the samba share I set up.  I want to set up a static IP for the server, as that makes sense to me.  So i edit /etc/network/interfaces:

iface eth0 inet static
       address 192.168.xx.99 #100 to 109 are used for DHCP from my router
       netmask 255.255.255.0
       broadcast 192.168.10.255
       gateway 192.168.10.10

If I set it for Static, I can SSH in, ping [www.google.com](www.google.com), access WEBmin from either laptop.  However when I try to mount the samba share says permissions denied or something.  In windows, when I explore the network places, it's not found.  As soon as i set inet back to dhcp, I can then mount and find it in windows no problem.  Does anyone know the cause of this?

---

### Post by Iowan on 2008-06-29
Another [thread/post]("http://ubuntuforums.org/showthread.php?p=4991871") mentioned that static addresses are treated somewhat differently - hostnames not recorded, etc... Like you, I prefer top have static addresses on servers.  Also like you, I'm having problems having my server visible.  Dunno if you could configure a static *lease* for your server (in your router).

---

### Post by dmizer on 2008-06-29
> **dardack said:**
> Does anyone know the cause of this?

netbios name resolution for samba doesn't work if you set a static ip on a dhcp network.

> **Iowan said:**
> Dunno if you could configure a static *lease* for your server (in your router).
this is the ideal solution, but not all routers support this configuration ... unfortunately.

---

### Post by dardack on 2008-06-30
> 
Quote:
Originally Posted by Iowan View Post
Dunno if you could configure a static lease for your server (in your router).

this is the ideal solution, but not all routers support this configuration ... unfortunately. 

Thanks so much.  I had originally tried to do this with my old router but it didn't support this.  Your answer made me check the new router (i figured it's brand new with wireless N gigabit routing, so it must) and it does.  It's real easy too, just let the computer get an address from DHCP, click the reservation button select what devices you want to have a reserved address, all done.  Works great.  Thanks again.

---

