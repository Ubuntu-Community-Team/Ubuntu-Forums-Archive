---
title: "[SOLVED] Certain DVDs not Playing"
date: 2008-12-23
forum: New to Ubuntu
---

### Post by Raynman37 on 2008-12-23
Alright, I'm having problems with DVD playback that I can't seem to figure out.  I wish I could change the thread title because now it includes all of my DVDs.  This is what I get:

[IMG]http://i555.photobucket.com/albums/jj443/Raynman37/totem_error.png[/IMG]

I am not sure why I get this error because I have ubuntu-restricted-extras from Synaptic, which should include libdvdcss2.  I also did:

```
sudo aptitude remove --purge totem totem-gstreamer
```
and
```
sudo aptitude install totem-xine
```

These are all legitimate copies of DVDs.  What am I missing?

---

### Post by mc4man on 2008-12-23
> I have ubuntu-restricted-extras from Synaptic, which should include libdvdcss2.

That's no guarantee it's installed, you should double ck. either in synaptic or just run ```
sudo apt-get install libdvdcss2
```

If it's not installed then either go here and add the repo and the key and run above again,

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)
 
or go here and do a direct install. (just click on i386 version. (unless your 64 bit install of ubuntu.

[http://packages.medibuntu.org/intrepid/libdvdcss2.html](http://packages.medibuntu.org/intrepid/libdvdcss2.html)

If that's not it do you know if region's been set on the drive?

---

### Post by Raynman37 on 2008-12-23
Ah man, thanks a ton.  Something happened to my Medibuntu repo when I was cleaning my computer up (aka hosing s*** up).  Just had to add the repo and install libdvdcss2 again.

Thanks much!

---

### Post by mc4man on 2008-12-23
Cool, you can always go directly to the medibuntu package list for intrepid. Things get added every once and awhile.

[http://packages.medibuntu.org/intrepid/index.html](http://packages.medibuntu.org/intrepid/index.html)

---

