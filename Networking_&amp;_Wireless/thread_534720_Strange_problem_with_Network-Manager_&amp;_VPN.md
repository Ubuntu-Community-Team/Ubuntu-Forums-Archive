---
title: "Strange problem with Network-Manager &amp; VPN"
date: 2007-08-25
forum: Networking &amp; Wireless
---

### Post by magnav0x on 2007-08-25
Ok, I've got VPN working with the network-manager pptp add-on, but I have a silly problem.  When I first tried setting up my VPN I forgot to set the 'Connection Type'.  When I view my 'VPN Connections' it shows up on the list, but when I goto 'Configure VPN', it does not show up on the list.  I want to get rid of it, but I can not find out where this information is stored.  I also have this problem on my laptop.  My buddy was trying to VPN to his work and ended up trying to set it up 5 or 6 times.  All the ones that didn't work I can not delete or edit.

Does anyone know where the VPN connection information is stored?  I want to get rid of these non -working connections.  I've searched all over and no one seems to know where this info is stored.  BTW, I'm running Ubuntu 7.04.

---

### Post by magnav0x on 2007-08-26
So no one knows where this info is stored?  Would I just be better off uninstalling it and reinstalling it to get rid of it?

---

### Post by callan79 on 2007-08-26
> **magnav0x said:**
> So no one knows where this info is stored?  Would I just be better off uninstalling it and reinstalling it to get rid of it?

Hello there,

I have a couple of PPTP VPN profiles set up too, and I ran this command to find the files :

```

cd /home
find -name "Test" -print

```

Note that "Test" is the name of my VPN connection, and it's case sensitive. The result that I got back was :

```

./callan/.gconf/system/networking/vpn_connections/Test

```

I guess yours should be stored somewhere similar :)

Cheers
Callan

---

### Post by magnav0x on 2007-08-26
Thank you so much!  That's where it was!  I need to learn to harness to powers of **find** sometime :)  For some damn reason I always resort to using **locate** and never think of **find**.  Oh well I'll get there eventually.  Thanks a lot for the pointer!

---

