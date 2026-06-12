---
title: "Dialing upon unbuntu start"
date: 2007-12-20
forum: Networking &amp; Wireless
---

### Post by DonDodge on 2007-12-20
I've just installed gutsy gibbon which is the first linux distro I've used in years.

Funny thing is every time I start the computer in ubuntu, it dials up my isp and is connected to the internet before I even get past the logon to the system. 

I see it where it happens in the system log. When I just now logged into ubuntu, chat [4387]  did the ATDT thing to dial the modem, then pppd [4221] completed the connection.

 What's up with this? What causes this thing to autodial upon start-up? How do I stop this autoconnect thing?

---

### Post by DonDodge on 2007-12-21
Okay, here's the thing. I know this is a commonly addressed problem and I know why it happens and how to stop it.  What I don't know is why, if I stop it, my computer is all screwed up.

If I shut off this autodialed connection in System/Network/Modem Connection or anywhere in Modem Properties, it takes over four minutes for ubuntu to complete the boot and activate my panels. Even worse, it takes forever to load a program. If I start a terminal, text editor, File Browser, System Log, Control Center, etc., the program needs 42 seconds to load. The first load of a terminal after booting can take up to two minutes.

If I allow the boot sequence to dial the connection, the entire deal is finished in a little over a minute, the computer is ready to go to work and all these programs start in about a second instead of 42 seconds.

If I disallow the autodialed connection, my computer is screwed until I manually dial the connection. Once I do that, the problem is over. A terminal, text editor, file browser, etc. loads in about a second instead of 42 seconds.

Is there any way to deal with this? I really don't want to have to connect this thing to the internet every time I boot up ubuntu.

The system won't allow me to solve the problem by taking away the modem, phone number or anything else in Network Settings. This computer is useless unless and until it's allowed to connect to the 'net. This seems really goofy. Why would ubuntu cripple this thing until it's allowed to make this network connection, even if it's only connected for two seconds?

---

### Post by DonDodge on 2007-12-22
Well, this problem has progressively resolved itself, apparently though doing the ubuntu updates which I accomplished in about three different sessions. The autoconnct feature started becoming intermittent at boot up. Then the wait times were cut in half when it didn't do the dialer dance. The last few times I've booted it, there's no attempt at automatic connection and there is no excess waiting time for anything. Now I can't even make it do the autodial thing. Go figure. There's nothing like a self-healing operating system but this puppy sure is frustrating at times.

---

