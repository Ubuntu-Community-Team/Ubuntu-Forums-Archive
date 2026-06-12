---
title: "Music Playback Over NFS Stops and Starts"
date: 2008-09-16
forum: Networking &amp; Wireless
---

### Post by russell-ault on 2008-09-16
I just set up a RAIDed NFS file server (OpenBSD) and moved all my music files to it from a USB mobile hard-drive (I needed the hard drive for other things). Music playback had been working without issue before the move, but now it seems that, regardless of what playback software I'm using (MPD and Amarok tested) and regardless of what encoding type I'm trying to play (FLAC, OGG, and MP3 tested), exactly the same problem occurs:

At first, the song will start to play normally. Then, after a period of as much as a minute but as short as fifteen seconds, playback will stop. After another short period of time, playback will resume from exactly where it had stopped previously.

It appears that there is something wrong with either my NFS implementation or my network itself, and I'm at a bit of a loss to determine which it is. I know NFS works for certain operations because it's how I transfered all the music to the server in the first place (which was apparently without error), and i know the network works for certain operations because I have Internet access right now. Is there a good way to determine what part of my NFS set-up music playback software doesn't like?

---

