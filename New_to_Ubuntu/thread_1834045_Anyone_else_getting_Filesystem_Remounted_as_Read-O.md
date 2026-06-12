---
title: "Anyone else getting Filesystem Remounted as Read-Only on Maverick?"
date: 2011-08-26
forum: New to Ubuntu
---

### Post by 3602 on 2011-08-26
This has been happening to me for a while now.

The system just randomly freezes. Mostly in browser (Chrome) but sometimes in Nautilus too. If I'm playing music through YouTube, the music goes on. There is no input (no mouse, no keyboard) during the freeze and the only way to get out of it is by holding down the power button.

According to /var/log/syslog,

```
Aug 26 22:27:28 linux kernel: [    3.673595] EXT4-fs (sda1): orphan cleanup on readonly fs
Aug 26 22:27:28 linux kernel: [    3.673691] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 23069122
Aug 26 22:27:28 linux kernel: [    3.673763] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 23073767
Aug 26 22:27:28 linux kernel: [    3.673775] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 23073779
Aug 26 22:27:28 linux kernel: [    3.673786] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 23073772
Aug 26 22:27:28 linux kernel: [    3.673798] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 13239415
Aug 26 22:27:28 linux kernel: [    3.673810] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 13239294
Aug 26 22:27:28 linux kernel: [    3.673821] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 13239278
Aug 26 22:27:28 linux kernel: [    3.673832] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 13239121
Aug 26 22:27:28 linux kernel: [    3.673843] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 23073771
Aug 26 22:27:28 linux kernel: [    3.768304] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 23069269
```

And stuff like that during the next boot when such a freeze happens.

There is a bug open on Launchpad but it's dated back to 2010. It is apparently a bug in an older kernel that has been fixed, but now it's 2.6.35-30 and I'm still getting it.

So minutes ago I decided to open up maverick-proposed and I'm now using a proposed version of the 2.6.35-30 instead of the stable version, hopefully having this problem fixed.

Anyone else getting the same thing for the last days?

Thank you all very much.

---

### Post by jerrrys on 2011-08-27
looks like your not alone

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=ext4_orphan_cleanup&as_qdr=m6&sa=Google+Search&lang=en#881](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=ext4_orphan_cleanup&as_qdr=m6&sa=Google+Search&lang=en#881)

---

### Post by 3602 on 2011-08-27
Forgot to say, tested both RAM and HDD. No problems.

Hopefully the proposed kernel solves this problem.

---

### Post by 3602 on 2011-08-28
Good news,

The proposed kernel DOES NOT solve the problem.

---

### Post by jerrrys on 2011-08-28
how bout revert back ti 2.6.35.14?

---

### Post by 3602 on 2011-08-28
> **jerrrys said:**
> how bout revert back ti 2.6.35.14?

Yeah I'll try installing 35-25. Didn't happen on that one.

EDIT: Good, I'm now on 2.6.35-25-generic. I'll see how this goes.

---

### Post by jerrrys on 2011-08-28
the way i read it 35.14 is the latest long term verision and 35.25 is a stable verision.

[http://kernel.org/](http://kernel.org/)

---

### Post by 3602 on 2011-08-28
> **jerrrys said:**
> the way i read it 35.14 is the latest long term verision and 35.25 is a stable verision.

[http://kernel.org/](http://kernel.org/)

I only read 2.6.35-14 on that... I don't see 2.6.35-25.

---

### Post by jerrrys on 2011-08-28
been dropped?  look in synaptic, they should all be listed there.

---

### Post by jerrrys on 2011-08-28
ooooooh, had to look twice, must of had 25 on the brain.  its sure not anywhere else :)

---

### Post by jerrrys on 2011-08-28
did find a source

[http://packages.ubuntu.com/maverick/linux-image-2.6.35-25-virtual](http://packages.ubuntu.com/maverick/linux-image-2.6.35-25-virtual)

---

### Post by 3602 on 2011-08-28
Ah I'm using the *generic* one.

[http://packages.ubuntu.com/maverick/linux-image-2.6.35-25-generic](http://packages.ubuntu.com/maverick/linux-image-2.6.35-25-generic)

---

### Post by jerrrys on 2011-08-28
so just back up to the one you want.  you may already have it in grub boot option

---

### Post by 3602 on 2011-08-28
> **jerrrys said:**
> so just back up to the one you want.  you may already have it in grub boot option

Yep. I've also used *startupmanager* to make GRUB boot 2.6.35-25 default instead of the 35-30.

---

### Post by jerrrys on 2011-08-28
you got the easiest way in ubuntu, click away

---

### Post by 3602 on 2011-09-04
Well, it's been a week and I haven't got a single jam yet.

Looks like 35-25 really is free from this problem.

EDIT: But apparently VirtualBox has small problems with this older kernel. Eh.

---

### Post by 3602 on 2011-09-19
OK here's the thing.

During the last period of time, I have tested every available kernel from 35-26 to 35-30, including Proposed ones.

Results:

**ALL** of these kernels suffer from immediate and serious File System Mounted as Read-Only problems. The 35-25 that I have previously found to be stable, however, is not: it will also have this problem, but *only* if the computer is left idle for a very long period of time. During normal usage, the Read-Only problem does not happen on the 35-25.

Well ain't that interesting.

---

