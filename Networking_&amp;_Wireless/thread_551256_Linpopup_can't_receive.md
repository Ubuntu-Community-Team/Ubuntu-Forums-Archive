---
title: "Linpopup can't receive"
date: 2007-09-14
forum: Networking &amp; Wireless
---

### Post by FyberOptic on 2007-09-14
So I decided to put Linux back on my primary machine the other day to mess around with some Tivo partitions, and thought I might as well get the whole thing fixed up nice and usable while I was at it.  One important thing I need is winpopup-compatible messaging.  I've never gotten this to work as flawlessly as just using RealPopup in Windows, which is just one of the reasons I don't use Linux more often on anything but servers.  Samba can just be kind of a pain at times in general.

Anyhoo, I seem to be able to send messages via Linpopup, but can't receive any.  At first I thought it was a client problem, so I even downloaded Linpopup2 and compiled/installed, in case the one from apt-get was the problem.  But same problem.

So I started messing around in samba's configuration.  I found that the messages were being saved into temporary files in /tmp, which linpopup was reading and then supposedly popping up for me to read.  So I changed the messenger line to just 'cat' the files to the 'wall' command.  I found that samba was apparently configured fine for receiving at least, because I was then seeing them in the console window.

I imagine that means there's a problem with Linpopup talking to the X server.  I mean, the default install is just supposed to work as-is as far as I know.  So why it doesn't in my case is beyond me.  I've looked on Google and other places and have just had no luck finding solutions.  I even tried RealPopup under WINE, but I guess netbios isn't implemented or isn't enabled, I dunno.  I never really looked into it yet, but it looked a bit glitchy, so getting Linpopup to just work properly is my best bet.

It's just kind of disappointing for such an almost trivial thing to be such a troublesome problem, considering the trickery I went to in the first place to get Linux to boot off a USB hard drive on my Windows PC that can't boot them!  I thought that was actually going to be the hard part, but nope.  GRUB4DOS is great.

---

