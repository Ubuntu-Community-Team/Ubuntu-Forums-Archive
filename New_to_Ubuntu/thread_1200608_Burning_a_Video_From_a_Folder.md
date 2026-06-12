---
title: "Burning a Video From a Folder?"
date: 2009-06-30
forum: New to Ubuntu
---

### Post by Lazy-buntu on 2009-06-30
I've got this folder of video parts:

VIDEO_TS.BUP
VIDEO_TS.IFO  
VTS_01_1.VOB

etc.

I'm trying to burn a DVD from these parts. I went to Brasero and tried Video project and threw all of them in the window and Brasero complains about the BUP and IFO files not being video files.

I'm not too sure about what the BUP and IFO files are for (maybe for a DVD menu and chapters?). How do I go about creating a DVD using all of these parts? I tried Brasero and DeVeDe to no avail. I heard K3B might help, but I'd rather not install all of the KDE requirements.

---

### Post by decoherence on 2009-06-30
You might try qdvdauthor. It's a Qt program but it doesn't depend on KDE.

Otherwise, I'd say bite the bullet and use K3B. It's the only KDE program I use.

> **Lazy-buntu said:**
> I've got this folder of video parts:

VIDEO_TS.BUP
VIDEO_TS.IFO  
VTS_01_1.VOB

etc.

I'm trying to burn a DVD from these parts. I went to Brasero and tried Video project and threw all of them in the window and Brasero complains about the BUP and IFO files not being video files.

I'm not too sure about what the BUP and IFO files are for (maybe for a DVD menu and chapters?). How do I go about creating a DVD using all of these parts? I tried Brasero and DeVeDe to no avail. I heard K3B might help, but I'd rather not install all of the KDE requirements.

---

### Post by Lazy-buntu on 2009-06-30
Alright I'll try that, do you know what the BUP and IFO files are for?

---

### Post by Lazy-buntu on 2009-06-30
QDVDAUTHOR crashed on me twice. I'm trying imgburn in WINE now to see if I have any luck. I'll let you know how that goes.

---

### Post by halitech on 2009-06-30
[http://en.wikipedia.org/wiki/BUP](http://en.wikipedia.org/wiki/BUP)

From Wikipedia, the free encyclopedia
Jump to: navigation, search

BUP (Back UP) is the filename extension of some files stored on video DVDs.

The BUP file is a backup of the IFO file on a DVD, which contains the information about the organization of tracks, menus, chapters, subtitles on the disc. The BUP files are used in the event that the corresponding IFO file is unreadable, perhaps due to a scratch on the surface of the disc.

Other DVD files include VOB files.

---

### Post by Lazy-buntu on 2009-06-30
I tried building an ISO from those files using ImgBurn and I mounted the ISO. The video works, but no sound or menu/chapters.

What's odd is I've got the .avi's of this DVD on my other computer, which I burned to DVD and it has the same problem. Video plays, but no sound.

I'll see if I did something wrong in ImgBurn. Any clue why there's no sound? If I play the VOB files, there's sound.

---

### Post by halitech on 2009-06-30
try playing the iso with vlc, its the only one I've had success with

---

### Post by Lazy-buntu on 2009-06-30
The problem is I wanted to burn this to disc to watch in my DVD player. I can play it fine on my computer as the VOB files or AVI files.

---

