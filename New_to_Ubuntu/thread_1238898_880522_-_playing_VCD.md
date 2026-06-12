---
title: "880522 - playing VCD"
date: 2009-08-12
forum: New to Ubuntu
---

### Post by hamidi on 2009-08-12
hi
when i insert the CD-ROM in the drive, Ubuntu brings up a window containing of its contents. if its a VCD an additional button titled Open Movie Player appears. when i click on it, Movie Player is started and prompts that a suitable plugin is needed. when i click on Search, it tries to find VCD protocol source plugin, but it seems it can't. in a dialog, it prompts that No packages with the requested plugins found. then it says:

An error occured
The playback of this movie requires a VCD protocol source plugin which is not installed.

what can i do?
thx

---

### Post by mthalis on 2009-08-13
Read this 
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by ArmenianLeader4 on 2009-08-13
you dont have to use the default video player. realplayer is available for free on their website. just google realplayer, download, and use. no WINE nessecary.

---

### Post by hamidi on 2009-08-15
i read the document, mthalis, but couldn't find the reason.
i prefer not to use any additional movie player for this purpose. just one video player, which is installed by default with the ubuntu must work. besides, i need to know how to solve the issue, not just to play the VCD. however, i tried vlc and it caused the error:
```
VLC could not read the file
```
i couldn't find why. i thought that the cd might be corrupted or be not readable. but the vlc i installed in the virtual machine with Windows could read and play it without any problem.
i'm going to try realplayer as u said also.

---

### Post by hamidi on 2009-08-15
i searched for realplayer in the synaptic package manager and it found no match. i also tried "real player", real player, real AND player, etc. but it found many things but real player!!!

---

### Post by mgmiller on 2009-08-15
realplayer is in the medibuntu repository.  You must enable medibuntu first.  Once that's done, use synaptic to search for realplayer and you will find it.  

 Here is the link:
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

This repository is also your source for win32codecs, win64codecs, dvdcss2, skype, googleearth and a host of other useful things.

The instructions are really just a bunch of copy and paste into terminal things.  It shouldn't take more than a few seconds to do the whole thing.

---

