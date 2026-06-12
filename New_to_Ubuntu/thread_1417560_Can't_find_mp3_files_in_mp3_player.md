---
title: "Can't find mp3 files in mp3 player"
date: 2010-02-27
forum: New to Ubuntu
---

### Post by TurnOfTide on 2010-02-27
Normally I stick my sansa 2gig mp3 player in windows and I can just drag and drop mp3s on it. Yet for some reason, in Ubuntu, I am seeing completely different folders (like config/settings folders) and I do not see any of my mp3s. It seems like there are 2 filesystems on this thing and Linux is finding the wrong one for me. How can I fix this?

---

### Post by TurnOfTide on 2010-03-01
and.... bump

---

### Post by crf on 2010-03-01
Have you tried to show hidden files? (See the View menu in the File Browser)
It could be your music is in one.

---

### Post by ks07 on 2010-03-01
> **TurnOfTide said:**
> Normally I stick my sansa 2gig mp3 player in windows and I can just drag and drop mp3s on it. Yet for some reason, in Ubuntu, I am seeing completely different folders (like config/settings folders) and I do not see any of my mp3s. It seems like there are 2 filesystems on this thing and Linux is finding the wrong one for me. How can I fix this?
This seems likely, although I'd check the hidden files thing first. You could check for multiple partitions by plugging it in and doing ```
sudo fdisk -l
``` or possibly ```
mount
``` and looking in the output. If you're not sure what you're looking for, post the output here. (use the code tags) :)

---

### Post by TurnOfTide on 2010-03-01
I will try that when I get home, but the thing is that these folders in question that are showing up never show up on my windows box nor on my ps3. So it leaves me to believe there are 2 file systems. Again this isn't your typical ipod.

---

### Post by audiomick on 2010-03-01
The folders are possibly installation things for windows. I have a USB stick that has that sort of thing on it.
[ATTACH]148707[/ATTACH]
The only thing that shows up in Vista is the excel file.

---

### Post by TurnOfTide on 2010-03-01
So are you able to browse your files then?

---

