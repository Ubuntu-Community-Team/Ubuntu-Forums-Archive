---
title: "Transmission BitTorrent won't let me add or remove torrents"
date: 2009-11-02
forum: New to Ubuntu
---

### Post by Inquisitorthemad on 2009-11-02
I can't get Transmission to remove torrents, or add them. If I try to add a new torrent, it acts like I've added a pre-existing torrent and therefore doesn't give it to me. If I try to remove torrents, it works fine, but they're all back by the time I'm done. The problem started when I tried to torrent "Lulz; A Corruption of LOL", and I suspect the problem is to do with the ";" in there but that doesn't tell me how to _fix_ the problem.

How am I meant to fix this? I've tried completely removing and reinstalling everything, and it did *nothing*.

---

### Post by NickJones on 2009-11-02
Download Wine and uTorrent.
Nick

---

### Post by wojox on 2009-11-02
Go into your home folder, view hidden files, go to .config and delete the transmission folder. It will get recreated when you open transmission again.

---

### Post by chris282 on 2009-12-17
Thanks for that, wojox.

Same problem - fixed!

- Chris

---

