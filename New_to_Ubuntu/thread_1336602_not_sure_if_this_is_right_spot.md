---
title: "not sure if this is right spot"
date: 2009-11-24
forum: New to Ubuntu
---

### Post by bac0926 on 2009-11-24
I have a problem that at first I thought it was hardware incompatibility but now I am not sure.
When I first started UBUNTU it said I had a floppy drive(which I do) but I never used it. A couple of weeks ago I went to use it, The system showed the Icon for it but could not access it. Tried replacing the drive no luck,tried replacing the IDE cable,same result. Then for the hell of it I tried switching over to Windows XP It showed up and I could access it. I mentioned this to a friend who also runs Ubuntu. He had never tried his floppy before. He tried it in Ubuntu same result I had. He went Over to Windows he also could access it. Other than both running Ubuntu the machines are totally different. Any suggestions?

---

### Post by lisati on 2009-11-24
Does it make a difference if you have a disk in the floppy drive? I've noticed that it sometimes does with the USB floppy drive that I rarely use myself.

---

### Post by ajgreeny on 2009-11-24
In jaunty, if you go to the menu for places and move over the floppy drive it shows "Rescan floppy drive" which will do exactly that providing you have a disk in the drive.  It will then show in nautilus as a mounted drive just like you are wanting.

I am not sure about karmic's handling of floppies as I am still running jaunty as my main OS, but it is worth trying this sequence of mouse clicks, etc etc, to see if it works the same.

---

### Post by Tholley on 2009-11-24
Same prob here...
 
I don't think I ever used my floppy in 9.04, but recently tried in 9.10 and it shows it is there, put a disk in, and it says it can't be mounted because there is no media present.
 
So it is not reading the media for some reason...

---

### Post by bac0926 on 2009-11-24
1) makes no difference where there is a disc or not.
2) tried rescan nothing happens when I put a disc in no message no nothing it just sits in the drive.  
3) for what it's worth I have a couple of flash drives I put them in the, the,two USB ports,system recognizes both and recognizes my two CD-ROM drives?????

---

### Post by 3rdalbum on 2009-11-24
In the past, you had to "modprobe" the floppy module into the kernel:

```
sudo modprobe floppy
```

I'm not sure if this is still done... I haven't touched a floppy disk in the last nine years.

---

### Post by bac0926 on 2009-11-24
result still the same does nothing,no messages, no nothing:popcorn:

---

### Post by Jive Turkey on 2009-11-24
I had a similar struggle about a year ago.  In my situation I wanted to get the contents off of my floppies so I could throw them away.  My only computer with a fdd was running headless ubuntu server and I remember using a script to copy all of the files from about a dozen disks.

I remember having to modprobe the floppy driver, and install fdutils.  I bet if you install fdutils and check the man/help for it you will get some clues.

EDIT- You might consider backing up all your floppies ASAP since they are not a very stable medium.

---

### Post by bac0926 on 2009-11-24
I'll give that a try

---

### Post by darksideforge on 2009-11-24
It really does sound like it's a software issue though.  9.10 is still new...bugs are still around.  It'll be interesting to see what comes out of this. Good luck.

---

### Post by bac0926 on 2009-11-24
I forgot to mention that it's 8.04 (hardy)

---

