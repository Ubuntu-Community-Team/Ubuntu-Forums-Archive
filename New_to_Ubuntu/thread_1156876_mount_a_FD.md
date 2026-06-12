---
title: "mount a FD"
date: 2009-05-12
forum: New to Ubuntu
---

### Post by nyuwa on 2009-05-12
I am trying (for a very long time already) to achieve something a simple as putting a FD into the computer, read and write it.
Yet, with Ubuntu (Linux) I cannot find any FD icon.
I read that you have to "mount" it, and after writing to the disk "unmount" it.
How?
Somewhere I read, if you put a FD into the computer, you will find, that a FD icon will automatically pop up under:
/filesystem/media
That is NOT the case. Nor does such an icon appear on the desktop.
Once, I was also told, that I need to input a million character long command in the terminal window. How does that work?

I have been using computers for almost 25 (long before the event of Windows) years, but have NEVER experienced any trouble with reading or writing to a FD.
Can that really be so difficult?

---

### Post by 3rdalbum on 2009-05-12
The "floppy" module is not loaded by default. I'm sure there's a good reason why not - maybe it causes problems with some more widely-used modules for current hardware.

You need to insert the floppy module:

```
sudo modprobe floppy
```

From there you may need to manually mount the floppy drive or it might mount automatically from then on. I don't know for sure - it's been 10 years since I've had a floppy drive and I wouldn't be surprised if no Ubuntu developers have them anymore.

---

### Post by nyuwa on 2009-05-13
Thank you.
The sudo thing worked.
Does that mean, I have to run this command every time I turn on the computer?

All my computers do have FDDs. Even if I may appear like a prehistoric: FDs always have been and still are a very convenient little item. And since they have been around since the dawn of (computer) time, there should be no technical problems with reading a FD, shouldn't it?

---

### Post by TheLions on 2009-05-13
> **nyuwa said:**
> Thank you.
The sudo thing worked.
Does that mean, I have to run this command every time I turn on the computer?

All my computers do have FDDs. Even if I may appear like a prehistoric: FDs always have been and still are a very convenient little item. And since they have been around since the dawn of (computer) time, there should be no technical problems with reading a FD, shouldn't it?

add this line to your /etc/fstab:

/dev/fd0 /media/floppy auto rw,noauto,user,sync 0 0

(open conf file with:
gksudo gedit /etc/fstab
)

---

### Post by nyuwa on 2009-05-13
I just restarted the computer after powering down (this does not work either).
Had to do the same thing all over.

Now, that is one for user friendliness.

---

### Post by nyuwa on 2009-05-13
> **TheLions said:**
> add this line to your /etc/fstab:

/dev/fd0 /media/floppy auto rw,noauto,user,sync 0 0

(open conf file with:
gksudo gedit /etc/fstab
)

Well, I got lots of things on the screen, that I do not understand, but I think managed to edit the designated file as instructed.
Yet, after restarting the computer there is no FD. Not on the desktop, not in the file system or under "media".

I AM probably too stupid to be permitted to use Linux (as has been indicated elsewhere), but, please, having a computer with a FDD all I want to do is stick a FD in, read/write it.
I have done this for 25 years on all sorts of DOS (in the good old days), Windows, Mac computers. That is simply how it works: stick the FD in = finish.

Yes, I know, I know, they were NOT Linux .... but having to work 30 times more than with a Windows PC for such a simple thing. I really fail to see the advantage of that.
(this applies to a lot of other equally simple things I cannot make to work)

from a really tired beginner

---

### Post by TheLions on 2009-05-13
ok here is nice HOW-TO which should answer all your answers:

[http://ubuntuforums.org/showthread.php?t=3687](http://ubuntuforums.org/showthread.php?t=3687)

Good Luck!:)

---

### Post by NHArticleTen on 2009-05-13
or this might even be newer and easier to follow:

[http://ubuntuforums.org/showthread.php?t=1060386](http://ubuntuforums.org/showthread.php?t=1060386)

---

