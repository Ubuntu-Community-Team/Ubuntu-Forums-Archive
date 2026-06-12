---
title: "Persistent remote X sessions on ubuntu server edition?"
date: 2008-02-17
forum: Networking &amp; Wireless
---

### Post by sammydee on 2008-02-17
Hi all

I have an old pc (600mhz p3, 512mb ram, 750GB hard disk) that I use as a sort of general server.

Now I'd like to keep it away from graphical apps of any kind as much as possible because it is old, slow and without any kind of gui a linux server is much much more reliable.

Unfortunately a couple of apps I need require a gui. Amarok for one, I like to use it over ssh displayed on my laptop, running on the server. It's quite slow and annoying if I restart X on my laptop, but it's the only music player that really fits my needs. Yes I know about mpd, and it's perfect, but I am yet to find a frontend that offers anywhere near the functionality of amarok - namely, the fine tuned playlist control. If there was one that would be absolutely perfect, but for now, amarok is really the only option I have.

The main problem is azureus and linuxdc++. I know there is rtorrent instead of azureus, but I don't know of any good replacements for linuxdc++. Also, I really need some of the functionality of azureus that rtorrent simply doesn't have. Both of these applications need to run for long periods while my laptop is turned off on the server. I want to access these remotely but also have them running while my laptop is switched off, then resume where I left off when I next connect.

I suppose what I am really asking for is resumable X sessions using an extremely lightweight window manager. XFCE is far too heavyweight for this, I really want something as simple as an xsession, a window manager and an x terminal that is accessable remotely and resumable.

Anybody got any good ideas?

sam

---

### Post by sammydee on 2008-02-17
WOOO!

Halfway there - I didn't know that azureues had a headless option - [http://www.azureuswiki.com/index.php/ConsoleUI](http://www.azureuswiki.com/index.php/ConsoleUI).

Just gotta figure out dc++ now...

Sam

---

