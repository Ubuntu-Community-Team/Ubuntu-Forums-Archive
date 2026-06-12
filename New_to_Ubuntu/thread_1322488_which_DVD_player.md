---
title: "which DVD player?"
date: 2009-11-11
forum: New to Ubuntu
---

### Post by pcrussell50 on 2009-11-11
i'm not a big DVD watcher, and the last time i watched a DVD it was Hardy Heron using VLC.  since it's been so long, i was just wondering if anyone has any other/better tips, or is VLC still the hot DVD player.  this for protected DVDs like you the ones you rent.

FWIW, i did the enabling multimedia process, and movie player still does not play protected DVDs. i'm running a successful install of karmic on a 3,1 macbook. [the macbook comes with a DVD player, but i want to be able to do this in karmic].

-peter

---

### Post by RedSingularity on 2009-11-11
Yeah i still use VLC.  I wouldn't use anything else.  It will play your encrypted DVDs.  I am sure it is till "up there" on the list of popular video players.  Of course besides a whole media center package like XBMC.

---

### Post by 3rdalbum on 2009-11-11
VLC is still the best DVD player, although it has surprisingly fallen behind Mplayer in terms of Blu-ray support.

Gstreamer does not play DVDs anymore, so that's why Totem Movie Player can't play your DVDs (as it's based on Gstreamer - there's a version of Totem based on the Xine backend which can play DVDs though).

---

### Post by andrew.46 on 2009-11-11
Hi 3rdalbum,

> **3rdalbum said:**
> VLC is still the best DVD player, although it has surprisingly fallen behind Mplayer in terms of Blu-ray support.

Actually I believe that if MPlayer is used with a decent frontend such as SMPlayer it will give vlc a run for its money. A problem with MPlayer has often been the way packagers pull the source code apart, removing the built in libdvdread + libdvdcss and some of the codec support for example, but if built in *full* and allied with SMPlayer: vlc look out :).

Andrew

---

### Post by rburkartjo on 2009-11-11
3rd xbmc is also good

---

### Post by kio_http on 2009-11-11
Kaffeine

---

### Post by arcofire on 2009-11-11
If you get libdvdcss2 from [http://www.medibuntu.org](http://www.medibuntu.org) then you can play encrypted DVDs in any of the regular players.

---

### Post by fooman on 2009-11-11
> **andrew.46 said:**
> 
Actually I believe that if MPlayer is used with a decent frontend such as SMPlayer it will give vlc a run for its money. A problem with MPlayer has often been the way packagers pull the source code apart, removing the built in libdvdread + libdvdcss and some of the codec support for example, but if built in *full* and allied with SMPlayer: vlc look out :).


+1 for smplayer.  :)

---

