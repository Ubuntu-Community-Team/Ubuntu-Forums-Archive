---
title: "Jaunty Rhythmbox is skipping"
date: 2009-11-29
forum: New to Ubuntu
---

### Post by Redmage913 on 2009-11-29
Greetings,

I use Rhythmbox to manage and listen to my media library.  My library is primarily made up of MP3 and Apple Lossless files.

My issue is that it regularly skips slightly every 15-60 seconds, even when it is the only program running.  I tend to use this netbook on car trips, and I've been getting complaints from others about this issue, so I'd like to fix it.

I've heard that PulseAudio has a LOT of problems with Ubuntu, and I'm wondering if this could also be my issue.  Being relatively new to Ubuntu, I am unsure as to how I should proceed on this matter.

I'm running a stock Dell Mini 9 with a gig of RAM and an Iomega 100GB removable hard drive plugged in.  My media library is there.

Any suggestions?

Thanks,
--Red

---

### Post by el Tedward on 2009-11-29
Not sure if this is related at all to your issue, but I've heard a lot about and have had issues using the scroll bar in firefox. When I would have the desktop effects turned up there would be serious scroll lag issues along with my music crapping out for a few seconds under heavy duty web page scrolling. 

When I installed Karmic with firefox 3.5, I didn't have this problem. I've heard that <a href='http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page' title=''>ubuntuzilla</a> is good for keeping mozilla products up to date since ubuntu doesn't always use the latest versions.

Hope this helps.

---

### Post by j2bv16 on 2009-11-29
> **Redmage913 said:**
> Greetings,

I use Rhythmbox to manage and listen to my media library.  My library is primarily made up of MP3 and Apple Lossless files.

My issue is that it regularly skips slightly every 15-60 seconds, even when it is the only program running.  I tend to use this netbook on car trips, and I've been getting complaints from others about this issue, so I'd like to fix it.

I've heard that PulseAudio has a LOT of problems with Ubuntu, and I'm wondering if this could also be my issue.  Being relatively new to Ubuntu, I am unsure as to how I should proceed on this matter.

I'm running a stock Dell Mini 9 with a gig of RAM and an Iomega 100GB removable hard drive plugged in.  My media library is there.

Any suggestions?

Thanks,
--Red

Try reinstalling, if that doenst work you have a pulseaudio probleam and need to unistall and use alsamixer

---

### Post by werecatomega on 2009-11-29
it might not be rhythmbox that is causing the problem. try some other music players for ubuntu and if the music is still skipping, i'd say the music files are having the issues

---

### Post by Redmage913 on 2009-11-29
When I go to my volume settings, it says I'm using HDA Intel (Alsa Mixer).  Does this mean I'm already using alsa, or am I actually using Pulseaudio and I don't know it?

This problem has happened to me with all installs of Ubuntu (I've tried Jaunty Ubuntu, UNR, and Xubuntu with Rhythmbox installed, and I've tried Karmic Ubuntu and Xubuntu. I downgraded back to Jaunty Ubuntu for different reasons, which is why I'm using it now).

---

### Post by ajgreeny on 2009-11-29
As I understand things, pulse is just a sound server and still needs alsa underneath to actually produce the sound, so seeing alsa still in the system is to be expected.

I am afraid I can't actually help with your problem, so you will have to wait for others with greater knowledge than me.

---

### Post by Redmage913 on 2009-11-29
Thank you for your input.  All knowledge is appreciated, as it helps me have a fuller understanding of what the <beep> i'm trying to do....

---

### Post by Redmage913 on 2009-11-29
I'm still unsure as to how to proceed, however.

So....I Bump.

---

### Post by j2bv16 on 2009-11-29
it was happening to me, i unistall pulseaudio and it work for me only with alsa 
try it

---

### Post by jamesisin on 2009-11-30
I am having a similar (or perhaps the same) problem:

[http://ubuntuforums.org/showthread.php?t=1326861](http://ubuntuforums.org/showthread.php?t=1326861)

---

### Post by desperado665 on 2009-11-30
that sounds like a file transfer problem to me. Does it do the same thing if the files are copied to the local drive?

---

