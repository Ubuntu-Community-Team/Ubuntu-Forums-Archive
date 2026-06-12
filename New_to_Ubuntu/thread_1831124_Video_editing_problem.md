---
title: "Video editing problem"
date: 2011-08-22
forum: New to Ubuntu
---

### Post by flyfishingphil on 2011-08-22
Just purchased a JVD Everio GX-HM30BU video camera. Had found very little ubuntu info but figured I could pull the SanDisk card, insert in my laptop and edit using OpenShot video editor. WRONG!

I get the impression that you have to have either Win$XP, Vista or 7, to operate the editing program that comes with it, but this also appears to be a requirement if you want to do anything.

Installed Wine, installed the Everio MediaBrowser pgm, but can't get there from here. (Can't get money back on camera, only "in store credit" if I return it.)

Outside of buying a stand alone cd/dvd recorder, if that would work, any ideas on how to get from the SDHC card to workable in the laptop?

EDIT:

Just looked around and came across some info that, hopefully, someone can help me with. 

Saw several referrals to WinFF and libavformat-extra-52 as being the best choices and they work with just about every FFMpeg format. Anybody familiar with these? Would they provide the necessaries to get into the video shot with the JVC?

---

### Post by LowSky on 2011-08-23
What format is the camera recording into?

Most formats should be editable from a Linux machine.

---

### Post by 3rdalbum on 2011-08-23
Probably best to forget using Wine for that program - it probably tries to access the camera directly, which Wine can't do.

Can you play the recorded footage on Linux, using Totem, VLC, or Gnome-Mplayer? If so then you should be able to put them into a video editor and work on them without having to use the Everio software.

---

### Post by flyfishingphil on 2011-08-23
Plugged the SD card into other computer running Win$ 7 it immediately opened video file. Under properties it shows the clip as being AVCHDVideo.(MTS). That help any? (Don't see any files listed using Movie Player or OpenShot Video in Ubuntu.)

3RDALBUM:
Haven't found a way to view it on Ubuntu 11.04 yet. For Video programs I have tried to open it with both "Movie Player" and OpenShot Video but no luck.

Thanks for quick responses.

EDIT: Brain fart!

Just wondering if it could have anything to do with the format of the sd card. Formatted as Fat32. Could that have anything to do with it not offering "open with" and only offering "open"?

2nd EDIT:
Not sure exactly what I did except look in different areas. Found if I follow this path I got into sample shoot I did and was able to load it into OpenShot Editor and play with it. Here's the steps:

Removed SD card from camera and inserted in card reader slot on laptop. It opened with 3 folders viewable (DCIM, EXTMOV, PRIVATE)
Click on private > 
click on AVCHD folder > 
Click on BDMV > 
Click on Stream > video(s) are viewable in box. 
Clicked on video and held button down to transfer to desktop. 
Right clicked on desktop video and clicked "Open with OpenShot". OpenShot opened with video clip available.

Love "figuring" out where stuff is hidden and getting it open.

Guess we can call this Solved!

---

