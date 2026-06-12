---
title: "Bittorrent in Feisty"
date: 2007-06-18
forum: Networking &amp; Wireless
---

### Post by phillipgi on 2007-06-18
I know this is old to most people (including me), but I can't work this out.

I've got a dual-boot system with Windows and Feisty. I use Azureus in Windows, and get pretty good download speeds (100-400kbps). However, in Ubuntu, I get nothing.

I've got all my ports forwarded (and I've checked them with Azureus's port checker), and, as far as I can tell, my firewall's off (I installed firestarter and opened the ports I'm using).

I've used Azureus and kTorrent, both to no avail (and I've copied my settings from Windows' Azureus). Some connections are made (although not as many as in Windows), and none of them actually download; after 2 hours I've managed 200k.

This has got to be something to do with Ubuntu, as the same torrent that works in Windows doesn't work in Ubuntu approx. 2 minutes later!

If anyone can shed any light on this, I'd really appreciate it.

---

### Post by Kabal on 2007-06-18
I use wine icw Utorrent (win exe) and that works great!

---

### Post by Crafty Kisses on 2007-06-18
> **phillipgi said:**
> I know this is old to most people (including me), but I can't work this out.

I've got a dual-boot system with Windows and Feisty. I use Azureus in Windows, and get pretty good download speeds (100-400kbps). However, in Ubuntu, I get nothing.

I've got all my ports forwarded (and I've checked them with Azureus's port checker), and, as far as I can tell, my firewall's off (I installed firestarter and opened the ports I'm using).

I've used Azureus and kTorrent, both to no avail (and I've copied my settings from Windows' Azureus). Some connections are made (although not as many as in Windows), and none of them actually download; after 2 hours I've managed 200k.

This has got to be something to do with Ubuntu, as the same torrent that works in Windows doesn't work in Ubuntu approx. 2 minutes later!

If anyone can shed any light on this, I'd really appreciate it.

Possibly try "Bittornado".

---

### Post by dreadlord_chris on 2007-06-18
> **phillipgi said:**
> I know this is old to most people (including me), but I can't work this out.

I've got a dual-boot system with Windows and Feisty. I use Azureus in Windows, and get pretty good download speeds (100-400kbps). However, in Ubuntu, I get nothing.

I've got all my ports forwarded (and I've checked them with Azureus's port checker), and, as far as I can tell, my firewall's off (I installed firestarter and opened the ports I'm using).

I've used Azureus and kTorrent, both to no avail (and I've copied my settings from Windows' Azureus). Some connections are made (although not as many as in Windows), and none of them actually download; after 2 hours I've managed 200k.

This has got to be something to do with Ubuntu, as the same torrent that works in Windows doesn't work in Ubuntu approx. 2 minutes later!

If anyone can shed any light on this, I'd really appreciate it.

first off - and this, of course, is only my opinion - but Azureus sux rox in Ubuntu.
That being said - I use kTorrent all the time and have no problems.

And about the firewall - unless you specifically turn it off, it's on by default.

---

### Post by phillipgi on 2007-06-19
OK, I've fixed it, and it was easier than I thought. Apparently, if you use a router with a built-in firewall (most new ones do), you need to turn it off. With Windows it's  not a problem (don't know why), but with Ubuntu it is.

Also, Azureus does suck (huge memory footprint), and I now use kTorrent, which is simple and works really well. As for using a Win32 client - doesn't that kind of void the point of switching to Linux?

---

### Post by dreadlord_chris on 2007-06-19
> **phillipgi said:**
> OK, I've fixed it, and it was easier than I thought. Apparently, if you use a router with a built-in firewall (most new ones do), you need to turn it off. With Windows it's  not a problem (don't know why), but with Ubuntu it is.



That's probably the UPNP service that "automagically" configured your router in XP - wasn't that nice, you didn't even ask it too (Azureus did, though). Personally, for things like this, I would rather know/be doing the configuring myself.

---

### Post by phillipgi on 2007-06-22
Yeah. Didn't even know my router accepted UPNP requests (it was really cheap when I bought it, quite some years ago).

---

### Post by fusionisthefuture on 2007-08-08
im also having problems like this, and im pretty sure ive got my firewalls configured right.  

in my linksys router running dd-wrt, ive got a static ip set for my computer, and, ive got two ports, 48000, and 6969 forwarded to that address.  

in firestarter, ive got outbound traffic set to restrictive, with the trackers address allowed, as well as service for port 6969 and 48000.  in the inbound traffic side, ive got service for port 6969 and 48000.  

in ktorrent, ive got port : set to 48000 and udp tracker port : set to 6969.  

can anyone see why i shouldnt be getting full dl speed, on a weekly release torrent that gets 300,000 downloaders?  oh btw, im seeding at my full capability, 22kB/s, which stays steady at that rate during the whole download, while my download rates waver between 10, and 60 kB/s on a VERY healthy torrent, 60 being the maximum for my connection (i know its saaaad :().  

thanks alot. 
-arne

---

### Post by Jamshedk on 2007-08-12
witht he DDWRT firmware you must change your timeout and connection settings here is a good read...

[http://www.dd-wrt.com/wiki/index.php/Router_Slowdown](http://www.dd-wrt.com/wiki/index.php/Router_Slowdown)

---

### Post by fusionisthefuture on 2007-08-12
thank you for the reply, and i did change that, although the way that you check to see if its working doesnt seem to work for me cuz i get really different values, and i also dont see that this is the problem becuase like i said bittorrent works fine on my windows machine.  i also uninstalled firestarter, and im going with webmin now.  id just really like to know if theres anything obviously wrong with the settings that i posted above?  thanks,
-arne

---

### Post by phillipgi on 2008-04-26
Thanks, all sorted now

---

