---
title: "cannot view data disc or DVD"
date: 2011-01-25
forum: New to Ubuntu
---

### Post by Nagle75 on 2011-01-25
I am extremely frustrated! is there an icon for pulling my hair out? LoL! Can someone please tell me how to view the contents of a data disc? & please don't tell me that when I put the disc in, that it should "just work", because it doesn't. Also I have instructional videos that are on DVD, that I occasionally watch. On windows, when I popped in a data disc or one of my instructional videos, it always asked me which program to open or view the disc with, & if for some reason it didn't, I could always use the simple failsafe of going into "my computer" & right clicking on the DVD-rom icon & choose "explore" & it would always show me the contents of the DVD, & then I could drag the folder to my desktop & play it from there, if it didn't automatically play. I just don't understand why it's so difficult to do this in ubuntu? When I go into the "disc utility" it shows me the cd/dvd-drive & says that it's located at /dev/sr0. Yet when I try to find this via nautilus, I can't find it anywhere. If this device is hidden, there must be a way to un-hide it & make it easier to work with. All my videos worked fine on Windows, so I know it's not my cd/dvd device. My music cd's work fine when I load them in the tray. For some reason, this only happens w/ data & video. I really hope that something small like this doesn't drive me back to using windows, but I really need to be able to view data discs & DVD's. Thanks for your time.:)

---

### Post by Zzl1xndd on 2011-01-25
Normally when placing a data DVD in the drive it will automatically mount, and display on icon on the desktop. Does this happen or does nothing happen at all?

If you have DVD movies then follow this document to enable playback:

[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

---

### Post by xgt001 on 2011-01-25
hi :)
make sure u have the side pane enabled in the nautilus browser and in that select places submenu.......... u should see ur DVD drive.... just click on it and u must see all ur drive contents as well :D

---

### Post by Nagle75 on 2011-01-25
Well, I don't understand why, but yes, you're right! It did finally put an icon on my desktop. It took a few moments, but it did work, so that's good news. I'll take a look at this other thread, as I haven't seen it before. Thanks so much!

---

### Post by Bucky Ball on 2011-01-25
Pop the disk in, open an appropriate app. Does that see the disk?

I am on Xfce desktop at the moment but from memory, System>Administration (or could be Preferences)>Removable Media and Hardware (or something similar). Have you got the boxes checked to automatically mount optical device?

---

### Post by Zzl1xndd on 2011-01-25
No problem, the link is just about enabling play back of encrypted DVDs. 

Normally manufacturers install some kind of program to do this that has the proper codec. You may or may not needed it.

---

### Post by Nagle75 on 2011-01-25
Well... I checked the synaptic package manager to see whether or not I have that package & I do in fact have libdvdread4, however underneath when I read more about that package it says that you may also need to intsall libdvdcss? I could see the data disc in the side pane & it also put the icon on my desktop, but still not sure why the video isn't working or what to try next.

---

### Post by Bucky Ball on 2011-01-25
Maybe you don't have the correct codecs installed. System>Administration>Synaptics Package Manager, search for and install 'ubuntu-restricted-extras'. This will install java, codecs and other things.

Also, try VLC media player, also available in Synaptics. This will load required codecs too from memory.

---

### Post by Nagle75 on 2011-01-25
More specifically... when I try to open the DVD via VLC I try to browse to /dev/sr0 the sr0 is greyed out, so I'm not sure what that means, but it's not letting me do much of anything.

---

