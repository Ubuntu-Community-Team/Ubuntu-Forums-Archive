---
title: "DVD wont Copy"
date: 2008-12-17
forum: New to Ubuntu
---

### Post by LowSky on 2008-12-17
I have been backing up my DVD library to my computer, so I can watch them from the network.

I have been using acidrip which is awesome, and works great. Every DVD but this one has been an issue (Dark Knight is the disc in question)

As you can see from the screen shot is that trying to load the disc eats up all my memory and swap. (I have 4GB of RAM and 8GB of Swap)

Anyone know what is going on? I'm backing it up as an ISO right now, that seems to be working, but I cant store it to my data drive, because its formated to Fat32 so my computer (linux) and my sister's windows computer can see it.

---

### Post by TransitMan on 2008-12-18
"***The Dark Knight***" is known to have a newer form of DRM on this release.
While I do not have my own copy as of yet, I've read that AnyDVD and possibly DVDFab will decode the DRM.
DVDFab is a Windows program, but runs well under "WINE'.
AnyDVD is also a Windows program, but I am unaware of it working in "WINE".
You might want to give **DVDFab** a shot.

---

### Post by umatchan on 2008-12-18
install wine+dvdfab , it works

---

### Post by LowSky on 2008-12-18
I installed DVDfab, it works, but not with this DVD.. Thanks for the program

---

### Post by LowSky on 2008-12-22
> **TransitMan said:**
> "***The Dark Knight***" is known to have a newer form of DRM on this release.
While I do not have my own copy as of yet, I've read that AnyDVD and possibly DVDFab will decode the DRM.
DVDFab is a Windows program, but runs well under "WINE'.
AnyDVD is also a Windows program, but I am unaware of it working in "WINE".
You might want to give **DVDFab** a shot.

how can they add new DRM and it will play in my old DVD players, and on my computer with VLC, xine, and mplayer. This makes no sense. I'm not saying its impossible but how do they add new encoding but yet my old stuff like a 5 year old DVD player still work fine???

---

### Post by mc4man on 2008-12-22
> how can they add new DRM and it will play in my old DVD players, and on my computer with VLC, xine, and mplayer

It's actually a 'structure protection' which in almost all cases has no effect on players on any sort. Players use the video_ts.ifo and playback from there, bypassing all the bad sectors, butchered .ifo's ect. (if you wanted to see how a title 'runs' use PgcEdit in trace mode.

In the case of TDK all the .ifo's from vts_05 on are intentionally 'borked' and prevent parsing the complete disk. In playback vts 5-9 are never called so it's not a factor for playback.

see here for a non manual solution (more appropriate place for these questions, ect.

[https://forum.doom9.org/showthread.php?t=143404](https://forum.doom9.org/showthread.php?t=143404)

---

### Post by jalirious on 2009-04-06
dvd fab with wine [DVDFab5232.exe] cracked the dark knight (disc 1 of two, didn't bother with two), then used k9copy to convert it from dvd9 to dvd5 (i.e. 4.3 gb).

---

### Post by LowSky on 2009-04-06
Wow my post was brought back from the near dead.

thanks for the tip

---

