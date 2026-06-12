---
title: "Home Media Server"
date: 2007-10-16
forum: Networking &amp; Wireless
---

### Post by schnabea on 2007-10-16
Hey everyone. I am interested in building a home media server that I can use to store all my music/videos and stream them wirelessly to other computers in my apartment. The caveat is that it has to work for both Linux and Windows clients. I am wondering if there is a software solution that works in a similar fashion to orb.com, where I can just have a media player program set up to browse the different collections. 

My fiance is a basic Windows user, and has no desire to try to learn Linux so I want a solution that will be very easy for her to use, without browsing through a standard file share. Basically I would love it if she could somehow see a library view of all the media on the server categorized by type, title, whatever, much like the amarok or iTunes library can be set up.

Does anyone know of anything that matches this description?

P.S. I wasn't sure if I should put this here or in multimedia or where, so admins please move it to wherever you think would be most appropriate.

---

### Post by Insightfill on 2007-10-16
There aren't many multimedia clients for both Linux and Windows that also have good library features (I hope I'm wrong).  VLC is the closest to multi-platform I can think of.

An alternative that may work, and close to what we have in my Mac/Windows/Ubuntu household was creating a Samba share on the Ubuntu machine and setting iTunes to use that as its library directory.  All newly imported files on the Windows side will copy to the Ubuntu machine.  Then, choose your favorite Ubuntu multimedia application and point it to the same directory.  Both applications will use the same file set, but the user can use the application library interface to find the files.

If you have multiple Windows computers, this won't work as well since iTunes doesn't have a "keep in sync" feature - it expects to own the directories.  Windows Media Player actually can do this however - pointed at a directory, it can keep a dynamic library going.

---

