---
title: "can't view video's full screen on youtube ubu 9.10"
date: 2010-04-07
forum: New to Ubuntu
---

### Post by bradmayne04 on 2010-04-07
Can anyone tell me how to watch video "full screen" in youtube? when i click the "fullscreen" button nothing happens!!  I could have sworn i used to be able to?? maybe I'm wrong... anyways does anyone have any ideas, thoughts, comments, etc. let me know!! thanx in advance!!

---

### Post by Psumi on 2010-04-08
Before you ask for help, do you have the 64-bit or 32-bit flash?

If you installed from software centre or flashplugin-nonfree through the normal repos, then you have 32-bit flash.

Then you should try this: [http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)

extract the archive into your home directory. Then, in terminal: **sudo cp libflashplayer.so /usr/lib/mozilla/plugins**

If you have 64-bit flash, from the tutorials: [http://labs.adobe.com/downloads/flashplayer10_64bit.html](http://labs.adobe.com/downloads/flashplayer10_64bit.html)

I don't know where to put it though, as I haven't messed with 64-bit in ages. Also, if your motherboard has PAE enabled, then you don't need 64-bit ubuntu to get more RAM.

---

### Post by lidex on 2010-04-08
If you are going to install a new version of flash, I strongly recommend removing the old versions first as they will conflict. Go here for an easy installer/uninstaller: [http://ubuntuforums.org/showthread.php?t=1414595]("http://ubuntuforums.org/showthread.php?t=1414595")
Read the first post carefully.

I've also seen recently issues with youtube changing their flash implementation, so you may be affected by that.

---

### Post by bradmayne04 on 2010-04-13
Yeah it seems that some videos I can watch full screen on youtube and some i can't.  When I go to cartoon network or Hulu and watch Television shows I can always watch full screen without any problems! So maybe it is what you say where it's Youtube's deal and not mine?  I dunno.

---

### Post by bradmayne04 on 2010-04-13
How can I find out if I have the 32 bit or 64 bit flash?

> **Psumi said:**
> Before you ask for help, do you have the 64-bit or 32-bit flash?

If you installed from software centre or flashplugin-nonfree through the normal repos, then you have 32-bit flash.

Then you should try this: [http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)

extract the archive into your home directory. Then, in terminal: **sudo cp libflashplayer.so /usr/lib/mozilla/plugins**

If you have 64-bit flash, from the tutorials: [http://labs.adobe.com/downloads/flashplayer10_64bit.html](http://labs.adobe.com/downloads/flashplayer10_64bit.html)

I don't know where to put it though, as I haven't messed with 64-bit in ages. Also, if your motherboard has PAE enabled, then you don't need 64-bit ubuntu to get more RAM.

---

### Post by Sheridann on 2010-04-13
When you are looking at a video in YouTube, just go up to the address bar and edit the URL. You are going to remove the "watch?" section of the URL and change the "=" to a "/".

Then you can view the full screen mode..

---

### Post by bradmayne04 on 2010-04-14
> **Sheridann said:**
> When you are looking at a video in YouTube, just go up to the address bar and edit the URL. You are going to remove the "watch?" section of the URL and change the "=" to a "/".

Then you can view the full screen mode..

Umm no that did absolutely nothing at all.  Oh by the way when I can't watch in full screen I also can not press the "pause" button on the video.  Essentially nothing "clickable" works on about 50% of the videos on youtube.  Changing the = to / and did nothing... and removing the "watch" etc. did nothing doing the them together did nothing.  why would playing with the URL field do something like that anyways?  Oh and I do not remember installing flash on ubuntu at all.  I'm sure I did I just don't remember it.  There's no way of telling what version I have from the command line?  Like when I want to see what kernel I'm running I use uname -r
any more ideas guys/gals??

---

### Post by lidex on 2010-04-14
> **bradmayne04 said:**
> Umm no that did absolutely nothing at all.  Oh by the way when I can't watch in full screen I also can not press the "pause" button on the video.  Essentially nothing "clickable" works on about 50% of the videos on youtube.  Changing the = to / and did nothing... and removing the "watch" etc. did nothing doing the them together did nothing.  why would playing with the URL field do something like that anyways?  Oh and I do not remember installing flash on ubuntu at all.  I'm sure I did I just don't remember it.  There's no way of telling what version I have from the command line?  Like when I want to see what kernel I'm running I use uname -r
any more ideas guys/gals??

In firefox: Tools>AddOns>Plugins

---

