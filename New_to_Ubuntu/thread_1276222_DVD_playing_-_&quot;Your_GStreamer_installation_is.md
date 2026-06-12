---
title: "DVD playing - &quot;Your GStreamer installation is missing a plug-in&quot; error"
date: 2009-09-26
forum: New to Ubuntu
---

### Post by mjp29 on 2009-09-26
I went to [https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

and used terminal to input the 2 lines for 9.04

however, when I put a dvd movie in to play I get the gstreamer installation is missing a plug-in error

---

### Post by mikeyphi on 2009-09-27
If you haven't already - I'd suggest you install 'Ubuntu Restricted Extras' using Applications - Add/Remove

Normally missing software is automatically downloaded - except, probably, in this case where there might be copyright issues!

---

### Post by baltadt on 2009-09-27
you have to install libdvdcss2 from synaptic package manager...although it is against the copyright law in the USA.  Your chose to install or not. I am not telling you to do it. ;)

---

### Post by Ratscallion on 2009-09-27
At the moment, libdvdcss2 is inaccessable. Therefore, I went for this: [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

---

### Post by mjp29 on 2009-09-28
> **baltadt said:**
> you have to install libdvdcss2 from synaptic package manager...although it is against the copyright law in the USA.  Your chose to install or not. I am not telling you to do it. ;)

Why is it against copyright laws in the U.S. - ?  (not copying, just viewing a dvd I purchased).

I'm guessing that MS Windows and Apple Mac os X both pay a royalty fee to someone to allow their operating systems to play dvd's (and none is paid with Ubuntu-restricted-extras installed) - ?

---

### Post by humphreybc on 2009-09-28
Install the Medibuntu repository ([https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu))

Then install these packages:

libdvdcss
ubuntu-restricted-extras

All the "gstreamer" packages from Add/Remove.

Then, use VLC to play your movie and it should work.

---

### Post by 3rdalbum on 2009-09-28
libdvdcss2 is inside the Medibuntu repository, and besides Totem Gstreamer won't play DVDs anyway. You are much better off to use VLC; it is a much superior video player and it does an excellent job of DVDs.

---

### Post by kevdog on 2009-09-28
Is that really true about totem-gstreamer with the plugins installed?  Honestly I use vlc, but I think its codec quality is crap.

---

### Post by Ratscallion on 2009-09-29
*sigh* 
- Any video player in Ubuntu CAN play DVDs...
- I've tried enabling the medibuntu repos, yet Ubuntu will NOT allow download of libdvdcss2...
- However, there is a teeny little thing you can do, which is [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683) there and allows you to do it.

---

### Post by m4tic on 2009-09-29
I don't get this, but on my pc, before i installed the codecs, it told me what was missing and gave me a download option, i have all the repositories enabled

---

### Post by Ratscallion on 2009-09-29
> **m4tic said:**
> I don't get this, but on my pc, before i installed the codecs, it told me what was missing and gave me a download option, i have all the repositories enabled
What's the actual problem there (i'm not sure I get that one...)

---

### Post by mjp29 on 2009-09-29
> **Ratscallion said:**
> *sigh* 
- Any video player in Ubuntu CAN play DVDs...
- I've tried enabling the medibuntu repos, yet Ubuntu will NOT allow download of libdvdcss2...
- However, there is a teeny little thing you can do, which is [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683) there and allows you to do it.

I'm sure any video player in Ubuntu "CAN" play DVDs.  However, I've found that with different computers (different hardware) the VLC mediaplayer works more often (on 2 Ubuntu computers I have here).  See my post in media section here at link [http://ubuntuforums.org/showthread.php?t=1278675](http://ubuntuforums.org/showthread.php?t=1278675)

I'm sure someone that knows more about this than me and can actually code linux could make any video player play a dvd - but for the casual user it may be better to just use vlc mediaplayer.

---

### Post by mjp29 on 2009-09-29
> **m4tic said:**
> I don't get this, but on my pc, before i installed the codecs, it told me what was missing and gave me a download option, i have all the repositories enabled

I too wish you would state your problem (can you not get dvd to play on your computer).  See my post at [http://ubuntuforums.org/showthread.php?t=1278675](http://ubuntuforums.org/showthread.php?t=1278675)

Also, have you done everything users have suggested doing here and have you installed VLC mediaplayer on your computer (and tried to get it to play DVDs instead of trying to get moveiplayer to make DVDs play)

---

### Post by Ratscallion on 2009-09-30
> **mjp29 said:**
> I too wish you would state your problem (can you not get dvd to play on your computer).  See my post at [http://ubuntuforums.org/showthread.php?t=1278675](http://ubuntuforums.org/showthread.php?t=1278675)

Also, have you done everything users have suggested doing here and have you installed VLC mediaplayer on your computer (and tried to get it to play DVDs instead of trying to get moveiplayer to make DVDs play)
And followed my link, which was the only way I got it to work...

---

