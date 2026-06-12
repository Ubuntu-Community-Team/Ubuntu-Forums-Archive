---
title: "fstab - newbie warning!"
date: 2008-10-25
forum: Networking &amp; Wireless
---

### Post by scoopy on 2008-10-25
Hi there

after reading around the forums it would seem that my problem of saving OpenOffice 3.0 files on a windows xp home machine without getting errors is by setting up perpetual network mounts using fstab.

i've made a new folder /media/winmounts

so this is the code that I have:
```
//studycom/j /media/winmounts cifs username=guest,password=,uid=1000,iocharset=utf8,codepage=unicode,unicode  0  
```

this opens a new nautilus window opened to /media/winmounts

However, I would like it open to my windows share //studycom/j

Any ideas.

---

### Post by scoopy on 2008-10-25
Why is no one replying?  Is it because I wear glasses?

---

### Post by Iowan on 2008-10-25
I wear glasses, too... but (unusual as it may seem) I don't spend all waking hours on the Forums.  Although I've gotten Samba shares to work, I haven't (yet) done the permanent mount, fstab-thing.  [This]("http://ubuntuforums.org/showthread.php?t=288534") How-To explains better than I can, but it appears that you already have the sharing part working.  (Notice the "Open Office save errors" section in the link). 

Are you saying the code works, but the label is wrong - or the mount is not your Windows box?

---

