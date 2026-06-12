---
title: "Networking 101"
date: 2006-08-25
forum: Networking &amp; Wireless
---

### Post by editrix on 2006-08-25
I asked about this in Absolute Beginners [http://www.ubuntuforums.org/showthread.php?t=241400](http://www.ubuntuforums.org/showthread.php?t=241400) but got no answers, so I'm trying here.

I simply want to use my Win98 box while still in Linux. I've got the 2 machines connected to a router. Using RealVNC, I can access the Win98 box, but the connection is so slow, it's unusable. I've been reading about vnc programs to the point I'm more confused than enlightened. If anyone has any suggestions, I'd appreciate it.

---

### Post by bernied on 2006-08-25
I use vnc, but only in the other direction (accessing linux desktop from Windows). 
This is maybe not available in Win98, but have you looked at the Remote Assistance options for windows? Maybe it's possible to install this. I don't know what protocol it uses, but it may also be vnc.

That thread that you referenced talks about CygWin, which enables  a linux environment inside windows, so you can run X through Windows. I also use this, but again only to get Linux X-sessions on the Windows machine, not the other way round. I don't think this would be useful to you, as you wouldn't be able to run your Windows programs inside cygwin (as far as I know). 

If it's just command line you want access to, you could install a ssh server on the windows machine - I think there are open/free releases.

Good luck

---

### Post by amo-ej1 on 2006-08-25
Perhaps it's better to check where your problem lies, is it vnc related or is it bandwidth related. I'd try to transfer a large file between the two machines and check if the bandwidth is what you expect it to be 10/100/1000 mbit. If this works you can be sure the problem is vnc otherways you should check your network settings (duplex, collisions, ...)
and can't it simply be the win98 that is slow ;-)

---

### Post by editrix on 2006-08-25
Oh, very strange. I already replied to this but it hasn't shown up. If there's a duplicate post, I apologize.

> **amo-ej1 said:**
> Perhaps it's better to check where your problem lies, is it vnc related or is it bandwidth related.

Yes, this is what I'd like to do, but have no idea how.

> **amo-ej1 said:**
> I'd try to transfer a large file between the two machines and check if the bandwidth is what you expect it to be 10/100/1000 mbit.

I'm a real beginner at this. I don't know how to transfer files. (It's not actually what I intend to do with the network, but I'm willing to try anything to diagnose the issues.)

And how would I know what the bandwidth is, or even what I expect it to be? If you mean bandwidth as in modem, I'm not using one. There's just the router and ethernet cables.

I'll ask about network settings (duplex, collisions, ...) once I get past step 1.

Thanks.

---

### Post by editrix on 2006-08-25
> **bernied said:**
> If it's just command line you want access to, you could install a ssh server on the windows machine - I think there are open/free releases.

Good luck

Thanks. I'm trying to actually use Windows, but on my Linux desktop--a couple programs for which there's no Linux equivalent. I'm trying to set up a system where I've got two computers, but only one monitor & keyboard. I've seen posts about this, but they all talk about very complex things like internet connection sharing, which I don't need.

---

