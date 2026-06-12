---
title: "Access shared folder on laptop from Smart TV"
date: 2014-04-21
forum: Networking &amp; Wireless
---

### Post by ohremd on 2014-04-21
Dear forum users,

this might be a stupid question. Here's the scenario: In Windows I used to watch video files stored on my laptop from my LG Smart TV via WLAN. I had the laptop and TV in a home network and a shared folder on my laptop where I put the video files I wanted to access. Now I'd like to do the same thing in Ubuntu (atm I always connect laptop and TV via HDMI cable, but I'd prefer the network solution). I'm not a bloody beginner, but don't know very much about networking in Ubuntu.

What I have done so far (maybe wrong/unnecessary): installed gnome system tools and created a shared folder with guest access. But I suppose I need to do some more basic stuff such as getting both laptop and TV in a home network before I can find the laptop/shared folder in my TV's interface? 

Thanks a lot,
Dom

---

### Post by TheFu on 2014-04-21
Without a GUI, use samba.
With a GUI, use nautilus to "share folders".

This assumes that smart TV actually supports CIFS file sharing ... which I've never seen.  Are you sure that under Windows, it isn't actually using the DLNA server? The easiest, most capable DLNA server for Linux is Plex. No need to signup for any accounts. It isn't F/LOSS, so if that is important to you, don't bother with Plex. It is free.

---

### Post by ohremd on 2014-04-21
I will try Plex then. Thanks!

---

