---
title: "How do I save playlists in Banshee to the iPod?"
date: 2011-07-21
forum: New to Ubuntu
---

### Post by discodandy on 2011-07-21
I am new to Ubuntu and have an iPod Classic 160gb. I have been using Rhythmbox which syncs playlists as playlists to my iPod. I heard that Rhythmbox is being discontinued, so have started nosing around in Banshee.

It is very unclear in the Banshee documentation how to sync playlists to the iPod, so that the actual playlists themselves show up on said iPod.

I have already experimented with the Smart Playlists, but it only transfered the playlist title and not the actual songs with it.

How do I copy/sync playlists as playlists to the iPod?

---

### Post by MikaelHolber on 2011-08-05
I have partially solved this for static playlists (not smart) by using banshee and gtkpod. My issue is when syncing with banshee, all songs go to the Ipod with the correct cover-art (if it is correct in banshee). However, the playlists will only get partially populated (example, one static playlist with 88 tracks get 33 tracks on the ipod, this seems to be random and applies to the smart playlists as well). Also, the order of the playlist was not preserved but put in the artist name from 0-Z (bummer if you want to create a dj-set as in my case)

The solution was to:
[LIST]
[*]Export the playlist created in banshee to a m3u file. 
[*]Sync the ipod so that all songs are on it.
[*]Close banshee and open gtkpod, gtkpod now want to scan the ipod (as if its never been connected before).
[*]Add the playlist from the menu.
[*]Eject the ipod from gtkpod so that the itunes database gets written.
[/LIST]

Most of the times everything get written to the ipod correctly, when stuff gets mixed up is when banshee is not playing ball, that will give you duplicates as gtkpod also transfers the song (saddest case is if you change the metadata, for example add BPM or comment)

If all the metadata is the correct the playlist will have cover-art and order preserved.

---

### Post by brobry on 2013-03-04
YOU ARE A PEACH!! thank you! you made my week

---

