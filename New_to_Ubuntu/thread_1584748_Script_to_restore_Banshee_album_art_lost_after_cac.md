---
title: "Script to restore Banshee album art lost after cache wiped?"
date: 2010-09-29
forum: New to Ubuntu
---

### Post by bornagainpenguin on 2010-09-29
Hi, I was wondering if someone who knows what they're doing can create a simple (?) script for me to run that would make Banshee play every song in the library (not podcasts) for about ten seconds to help me rebuild my album art?  I know that there is an option for banshee to download album art but it is not working right now due to the way Bleachbit wipes the cache.  If anyone is wondering how I ended up with this issue there is a great write up about it [here](http://bleachbit.sourceforge.net/forum/bleachbit-removes-downloaded-album-art-not-really-bug).

The only way to get the art back is by manually playing each song, so I was hoping someone could automate the process for me.  I'd hate to have to re add and redownload all my podcasts on my crappy connection, so I'm really hoping someone can help me out here.  Thanks in advance!

--bornagainpenguin

---

### Post by pborman on 2010-11-07
Start banshee playing with "all artists" playlist, then in a terminal type...

 while true; do sleep 10; banshee --next; done

I've used this to automate loading track lyrics, but it works for album art too,

Phil.

---

