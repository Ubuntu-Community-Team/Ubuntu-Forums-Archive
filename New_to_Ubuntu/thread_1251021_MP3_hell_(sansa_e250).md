---
title: "MP3 hell (sansa e250)"
date: 2009-08-27
forum: New to Ubuntu
---

### Post by mimicoco on 2009-08-27
Hi guys. I would really appreciate some help with my MP3 issues. 
I've tried to search existing threads but am getting nowhere..

I have a sansa e250, has trouble mounting, doesn't appear on my desktop or in my places in MSC mode, only in MTP when locked. I've tried with Rythmbox and Amarock and while i can spend hours transfering files, when i disconnect the mp3 the files disappear. same with drag and dropping.

am thinking of putting rockbox but instructions are to have the player in MSC, but in that mode the player seems to disapear. 

Please help!!

---

### Post by mimicoco on 2009-08-27
please?

is there somewhere else i should be going for help?

---

### Post by 3rdalbum on 2009-08-27
Please be patient; not a large percentage of the forum's users have a Sansa e250. I don't.

But this sounds similar to what users of certain Sony Walkman players experience on Jaunty; basically, Gnome mounts those Walkmans as MTP-only, and it just doesn't work properly. My mother has one of the affected Walkmans, so that's how I know about it.

The fix is to plug in the player and wait for it to be recognised as MTP. Then run this command:

```
killall gvfs-gphoto2-volume-monitor
```

Unmount, unplug, plug the MP3 player back in, and it should appear as a USB Mass Storage device.

I hope this does the job for you.

---

### Post by mimicoco on 2009-08-27
thanks 3rdalbum, sorry for seeming cranky, im tearing my hair out with this thing. might need to go for a walk. 

once its a usb device can i install rockbox? or should i not bother at that point?
 
thanks, Andrea

---

### Post by sydbat on 2009-08-27
> **mimicoco said:**
> thanks 3rdalbum, sorry for seeming cranky, im tearing my hair out with this thing. might need to go for a walk. 

once its a usb device can i install rockbox? or should i not bother at that point?
 
thanks, AndreaI would give the file transfer (drag 'n' drop) another go first. It might be simpler.

If that still does not work, perhaps the rockbox option is worth looking at.

And remember to unmount your Sanza before unplugging it so the data does not (potentially) become corrupted.

---

### Post by mimicoco on 2009-08-27
I ran the killall, and it still doesnt recognise the player, only after  gvfs-mount -li  will it show up, and then with an error message:

Error initializing camera: -60: Could not lock the device

---

### Post by mimicoco on 2009-08-27
no joy. 

the player is still only appearing under MTP, and looks the same as before, i can drag and drop music files into the MUSIC folder but when i turn on the player it says No Song

do i perhaps need to reinstall the firmware?

---

### Post by BrokenPoet on 2009-08-28
I just purchased an old e280 and had similar issues.  I found assistance [_**here**_]("http://www.mattwoodward.com/blog/index.cfm?event=showEntry&entryId=E24FA790-C19F-4674-A6FE8AA9E5D8FE83"), which brought me [_**here**_]("https://bugs.launchpad.net/ubuntu/+bug/345916"), and ultimately I added the source at the bottom of [_**this**_]("https://bugs.launchpad.net/ubuntu/+source/libgphoto2/+bug/355998") bug report, updated libgphoto2 and somewhere along the way it started working.  (I also made the foolish error of not shifting the Sansa over to MSC until after doing all three of the above, so you may find success sooner than I.)

---

