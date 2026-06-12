---
title: "How may I transfer files from my PC to my hard drive on a network?"
date: 2014-01-29
forum: Networking &amp; Wireless
---

### Post by 9k0aefbmMtuJ on 2014-01-29
I have a Desktop in my upstairs study running Ubuntu and connected via wifi to my downstairs Router fixed in my music room. 

I've attached my Seagate FreeAgent GoFlex Desk 2TB hard-drive to the router though an Ethernet cable.

Please will the team lead me through in simple terms how I may transfer my music files from my Desktop to my 2TB hard drive via a network?

---

### Post by TheFu on 2014-01-29
In theory, any of the file managers should be able to access storage "on the network" by just browsing. pcmanfm can and I'd assume nautilus will too.  It would probably connect using CIFS via gvfs.

I don't have a GoFlex, so I don't know which storage daemons those devices run, which file systems they support, or any other limitations.
Plus using wifi means it really needs to be an ad-hoc connection, not something "mounted" - IMHO.

Does "browsing" not work?

---

