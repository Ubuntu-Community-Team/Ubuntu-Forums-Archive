---
title: "Network-manager broke after KDE"
date: 2006-12-03
forum: Networking &amp; Wireless
---

### Post by sparX CG on 2006-12-03
Hi everyone!  I'm having problems setting up my wireless network connection.  Seems like many do too!  Linux, unfortunately, doesn't have any straightforward out-of-the-box and working-for-everyone wireless tool yet.  The closest we can get it Network-manager, but then again, that doesn't always work either.

So here's my story.  I've been a happy GNOME user for a long time, but then I found that GNOME and Gtk lacked good tools for some things, such as CD burning.  So I decided to try out KDE.  It was pretty ugly at first, but after getting QtCurve and configuring it properly, it looked pretty good, almost comparable to Murrine.  Anyways, that's the unimportant part.

While my laptop here was GNOME-only, I had no problems whatsoever with Network-manager to set up my wireless connection.  Install, start, connect, type WPA key, Internet.  Ever since I installed kubuntu-desktop along with my ubuntu-desktop, Network-manager stopped working.  Whenever I try to connect, it just tries, then stops and nothing works.  I figured it was a GNOME and KDE conflict, so I installed a fresh Kubuntu, and used knetworkmanager to configure and use Network-manager.  But I got the same problem.  It just doesn't work, whether it's WPA protected, like at my home, or unprotected, like at my school.

Does anyone else have this problem?

---

### Post by Ethos on 2006-12-03
Thats the problem I am dealing with right now...I have another post going to try and answer this problem since im using wpa2 tkip+aes encryption on my router, and dont want to unsecure it at all. I could suggest using wifi radar for unsecured networks, that works for me, but I cant get it to work with wpa...

---

### Post by sparX CG on 2006-12-03
Does anyone know a solution to this?  It's very annoying, I believe it's KDE invading the wireless settings, but I don't know how to disable that.

---

### Post by sparX CG on 2006-12-04
Bump, I know many people have this problem, is there a fix somewhere?  I can't find it, even after hours of googling.

---

### Post by vayu on 2006-12-04
> **sparX CG said:**
> Bump, I know many people have this problem, is there a fix somewhere?  I can't find it, even after hours of googling.

I don't know anything about the GUI wireless setups but there is a KDE kwifimanager.  Maybe you need to go to it and either use it and forget about knetworkmanager, or disable kwifimanager and use knetworkmanager.  Or maybe you need to go to kcontrol and see what settings it has for networking in general.

If you're really desperate I could describe how I got it to work with config files.  But it's a long shot, because I worked hard to get my setup working and I don't know much beyond that, plus I'm on Dapper not Edgy. If your situation is as mine it might work.  I use my laptop in three different situations, wired static, wireless wpa static, and wireless dhcp unsecured.

I'm usually on the wired static and that's set up to be automatic.  When I use the wireless static wpa secured I type two lines in a command window, same when I'm at a coffee shop using wireless dhcp unsecured.  Not too bad actually.

I've seen a howto that even automated it more than that, but that script was beyond me.

(I've been meaning to try network manager, but I'm attached to it actually working more than ease of use, plus I've learned a bit about what goes on under the hood, now I'm skeptical about the gui because I don't know what it's doing)

---

