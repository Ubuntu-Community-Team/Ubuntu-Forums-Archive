---
title: "Hoo boy, DvD issues."
date: 2009-01-12
forum: New to Ubuntu
---

### Post by The_Proffessor on 2009-01-12
So to start with I'll say I switched to ubuntu after banging my head against Vista for about a year.  The frustration was almost, but not quite, enough to make me buy a mac *shudder*.  I believe ubuntu is the ideal solution though.

Right now, my main problem is that my computer now won't play dvds.  It detects the disc but only picks up on a subtitle track and no video and thus doesn't play. This may be, so I theorize, that the drivers for my CD/DVD-RW drive were removed in the switch.  So I tried to use the disc that came with my laptop (Toshiba Satellite if it matters) to try and install said drivers.  As I feared, the disc would not run as I'm pretty sure it's a windows only type deal.  Trying to run the cd under Wine met with similar frustration.

Am I barking up the wrong tree?  Or is it that I must haul my butt to the living room to watch movies again (god forbid)? And if Wine was the right idea, anyone know where I can find a good guide to using it (preferably without having to dicker with a command line)?  

I'm sure this issue has been addressed on another thread, but I'm too tired to properly look for it.

---

### Post by ken22 on 2009-01-12
Try this

[http://ubuntuguide.org/wiki/Ubuntu:Intrepid#DVD_Playback_Capability]("http://ubuntuguide.org/wiki/Ubuntu:Intrepid#DVD_Playback_Capability")

---

### Post by The_Proffessor on 2009-01-12
well we've moved from nothing to a complete scrambled mess.  I guess that's a step forward.

---

### Post by ken22 on 2009-01-12
just follow those instructions

---

### Post by Bakon Jarser on 2009-01-12
Try running this.

sudo apt-get install ubuntu-restricted-extras

Also vlc media player seems to be the best option for playing dvd's in ubuntu.

sudo apt-get install vlc

It will install under applications > sound and video.

---

### Post by 3rdalbum on 2009-01-12
If you are using VLC as suggested, to watch your DVDs, then you may need to change the video output settings in VLC as a work-around to Nvidia's buggy graphics card drivers. This may be why your video looks scrambled.

If you go to VLC and Tools > Preferences and click on the Video button, you'll see a popup menu for "Output". Change that to "X11 video output". Quit VLC and start it up again, and see if that helps your problem.

Nvidia has known of this bug for at least a year and still hasn't fixed it... typical proprietary software vendor.

---

### Post by 3rdalbum on 2009-01-12
If you are using VLC as suggested, to watch your DVDs, then you may need to change the video output settings in VLC as a work-around to Nvidia's buggy graphics card drivers. This may be why your video looks scrambled.

If you go to VLC and Tools > Preferences and click on the Video button, you'll see a popup menu for "Output". Change that to "X11 video output". Quit VLC and start it up again, and see if that helps your problem.

Nvidia has known of this bug for at least a year and still hasn't fixed it... typical proprietary software vendor.

---

### Post by binbash on 2009-01-12
for playing dvds , i strongly suggest using vlc.Also you can play menus etc with smplayer svn version.

---

### Post by Zerqent on 2009-01-12
Afaik, VLC in ubuntu does not have DVD support by default ? (For encrypted DVDs that is) - This is something I am not sure of though...


Anyways, what I always do is the following:

sudo aptitude install libdvdread3 && sudo /usr/share/doc/libdvdread3/install-css.sh


This will install the package libdvdcss2 which will make it possible to watch encrypted DVDs. You should not though that this is not legal in all countries - which is probably why this package is not installed by default.

---

### Post by The_Proffessor on 2009-01-19
Finally got it working.  Thanks to the many peoples who helped.  That last post, the not-entirely legal thing, was what finally got it all unscrambled. Though I'm sure all the other bits contributed.  Anyways, thanks guys.

---

