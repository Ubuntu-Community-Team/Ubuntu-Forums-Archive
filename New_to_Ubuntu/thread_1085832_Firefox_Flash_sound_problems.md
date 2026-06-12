---
title: "Firefox Flash sound problems"
date: 2009-03-03
forum: New to Ubuntu
---

### Post by Bearly Able on 2009-03-03
I can't get audio to work for Flash in Firefox: either there's complete silence, or very loud, distorted crackling.  As far as I know, audio works just fine elsewhere in the system.

I'm running Firefox 3.06 under Ubuntu 8.04, with Flash 9 (I think - it's the one in the repositories).  I've searched the forums and followed the instructions [here]("http://ubuntuforums.org/showthread.php?t=997506"), but nothing's worked - or I've screwed up somewhere.  I've also installed libflashsupport, but still no joy.

Can anyone suggest where I'm going wrong and what to do next?  Thanks in advance for any help you can offer.

---

### Post by cwsnyder on 2009-03-03
Just a note: the instructions which you followed are for 8.10 Intrepid Ibex.  You indicate you installed 8.04 Hardy Heron.  Unfortunately, sound is one of the things which changed.

Try the instructions [here]("http://ubuntuforums.org/showthread.php?t=205449"), and see if they work better.  These instructions are what I used to get my sound back when I was having problems.

---

### Post by Bearly Able on 2009-03-04
Thanks for the reply.  The post I followed states it also applies to Hardy.  I've looked at the thread you suggested, but it seems to deal with general sound problems, which isn't the issue here.

Since my original post, I've discovered a further problem with video within Firefox, so I think it's a Firefox problem, not an audio problem.

The first problem arose when I was trying to send a Flash e-card; some cards on the site played without sound, while others produced a load crackling.  (I've used the site many times from Windows and had no trouble.)  In both cases, the video element played perfectly.

I've since discovered I cannot play embedded videos eg on the BBC news site.  The loading symbol appears, with the message "loading player", but nothing happens after that.  After a few seconds, I can right-click on the blank panel and bring up the Gnash menu, but still can't play the video.  On one site, the Flash advertisements play just fine, but I can't watch any of the movies in the main content.

I have both the Totem and Gnash Mozilla plug-ins installed.

Any further advice would be appreciated.

---

### Post by Bearly Able on 2009-03-04
It's just occurred to me that the obvious place to look for a solution is on the Mozilla Web site.  They say installing libflashsupport will fix the problem, but I've tried that and it hasn't.  They also suggest downloading Flash 10 from Adobe.  Firefox is asking me if I want to open it with the GDebi Package Installer, but I don't know - I've never installed anything this way before.  I know I'm being a coward, but I'd appreciate some advice before I screw things up any further!

---

### Post by cwsnyder on 2009-03-05
GDebi Package Installer is for any general .deb installation file for Debian, Ubuntu or their derivatives.  I have installed Flash 10 on my Ubuntu 8.04 and 8.10 installations using this method without problems.  .deb files are package files which will check for proper dependencies.

---

### Post by gandaran on 2009-03-05
> **Lesley Lutomski said:**
> Thanks for the reply.  The post I followed states it also applies to Hardy.  I've looked at the thread you suggested, but it seems to deal with general sound problems, which isn't the issue here.

Since my original post, I've discovered a further problem with video within Firefox, so I think it's a Firefox problem, not an audio problem.

The first problem arose when I was trying to send a Flash e-card; some cards on the site played without sound, while others produced a load crackling.  (I've used the site many times from Windows and had no trouble.)  In both cases, the video element played perfectly.

I've since discovered I cannot play embedded videos eg on the BBC news site.  The loading symbol appears, with the message "loading player", but nothing happens after that.  After a few seconds, I can right-click on the blank panel and bring up the Gnash menu, but still can't play the video.  On one site, the Flash advertisements play just fine, but I can't watch any of the movies in the main content.

I have both the Totem and Gnash Mozilla plug-ins installed.

Any further advice would be appreciated.
why do do have the gnash plugin installed? if you don't want to use adobe flash then it's okay but don't expect the adobe flash plugin to work perfectly if you have any other flash package installed getting in the way.
the perfect setup is just to have adobe flash 10  (not adobe flash 9 which has the flash sound problem, flash 10 should fix this) installed and no libflashsupport too, libflashsupport is for use with adobe flash 9 it conflicts with flash 10.
if you still experience flash sound problem with only adobe flash 10 installed then you have to fix pulseaudio [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

---

### Post by Bearly Able on 2009-03-05
Thanks, cwsnyder - I've installed Flash 10 no problem.  I was just a bit anxious about going ahead, as Firefox in Windows occasionally gave me very weird suggestions for opening files, and in this case, I didn't have enough knowledge to decide if it was right or not.

Gandaran, thanks for your reply - it's solved my problem.  The Gnash plug-in must be installed by default - I've never knowingly added it.  Nor did I deliberately install Flash - I guess it comes as part of the ubuntu-restricted-extras package I installed in my initial attempt to solve the sound problem.  Anyway, upgrading to Flash 10 didn't fix things until I uninstalled the Gnash plug-in.  I'm still finding my way around Ubuntu and hadn't realised there was a software conflict here.  That's why I'm posting in the forums, and why I'm grateful to folk like you who can point out my errors.

Thanks again guys.

---

