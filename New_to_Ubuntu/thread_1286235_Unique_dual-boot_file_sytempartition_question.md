---
title: "Unique dual-boot file sytem/partition question"
date: 2009-10-08
forum: New to Ubuntu
---

### Post by c0ldfuse on 2009-10-08
In a bout of good luck I got my brother's T60 laptop which was "broken".  Ran ultimate boot disc, bad drive, replaced with 320GiB drive = free laptop (he was leaving the country and couldn't wait for a drive).

The laptop is going to be used for the following:
1) Personal use
2) DJing with mixvibes (digital vinyl emulation)

I've had good experiences with ubuntu on a buddy's comp and figured I should finally get around to using it.

I installed WinXP to a 15GiB partition (ntfs) because I'm certain mixvibes will work on WinXP. I now have the remaining 305GiB unpartitioned space and I am trying to decide how to shake this out.

Requirements:
1) Use Ubuntu as primary OS
2) Torrenting music and files on my primary OS to a drive that can be read/written by WinXP (aka, mixvibes).

Currently, after talking to several people, I think the best solution is to set up a data-partition which is Fat32 (say, 255GiB), then allowing Ubuntu to install in the remaining 50GiB space as ext3. What I dislike about this is the limitations fat32 will give me.

This set-up seems inelegant/ghetto as hell.  I don't want WinXP on fat32, and I don't particularly like the idea of my files on there either, but it seems the only way I can still use Ubuntu as my primary OS and fit my requirements.

The install disk I have is a no-touch auto configure for WinXP so reinstall of WinXP is painless if I need to start over and no files or anything need will to be backed up.

:confused:

---

### Post by Trebaruna on 2009-10-08
No offense, but this is hardly unique.

Ubuntu has no problems mounting, reading from or writing to NTFS volumes. Also, using a driver from [http://www.fs-driver.org/](http://www.fs-driver.org/) Windows has no problems with the same for Ext2 and 3.
So, make a partition for Windows. Make one for Ubuntu. Add a third for data (and potentially a fourth for swapspace) and you're all set.

---

### Post by c0ldfuse on 2009-10-08
> **Trebaruna said:**
> No offense, but this is hardly unique.
I didn't think it was initially, but it felt like going through the problem with others it wasn't.

> 
Ubuntu has no problems mounting, reading from or writing to NTFS volumes. Also, using a driver from [http://www.fs-driver.org/](http://www.fs-driver.org/) Windows has no problems with the same for Ext2 and 3.
So, make a partition for Windows. Make one for Ubuntu. Add a third for data (and potentially a fourth for swapspace) and you're all set.
Sounds good, I'll make the third ntfs, yes?

---

### Post by Trebaruna on 2009-10-08
> **c0ldfuse said:**
> Sounds good, I'll make the third ntfs, yes?
So far I've had no problems with either. NTFS makes your life a little easier because Windows (obviously) supports it out of the box, and so does Ubuntu.

---

### Post by gali98 on 2009-10-08
Don't use FAT32!!!
If you are wanting to torrent, that usually means large files. FAT32 has ~4gig file size limit. Like the others said use NTFS.
Kory

---

### Post by c0ldfuse on 2009-10-08
Installing now, thanks guys
15 - WinXP
250 - Data Storage
40 - Ubuntu
8MiB - Swap

---

### Post by gali98 on 2009-10-08
Hold up. You probably want more swap than that. Good practice is to have twice your amount of ram.
[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)
If you want to hibernate, you need at least your amount of ram and a little bit more.
Kory

---

### Post by Trebaruna on 2009-10-08
If it's not too late:
40 GiB for Ubuntu seems a little much. Since you won't put your data there, you only need a relatively small amount. I'd say 10 is plenty.

Also, the swap is supposed to be what Windows calls "virtual memory": if you run out of RAM, Ubuntu will start to put stuff there. 8MiB is clearly not very useful in that case. This likely won't happen terribly often, but it's very annoying if it does. More importantly, however, is hibernation: in this case Ubuntu will write all of your RAM to the swapspace. Again, 8MiB is not going to cut it.
I'd pick a size that's just a little more than your machine's total RAM if I ever intended to use hibernation.

EDIT: Gosh, there's a FAQ for that. Thanks gali :) I think twice your RAM is overkill, though.

---

### Post by gali98 on 2009-10-08
@Trebaruna lol...
I think there may be some math to it...
I have a 250GB hard drive, with 4GB of ram, and the ubuntu installer gave me 10GB swap.
But I'm not too worried about it..
Kory

---

### Post by louieb on 2009-10-08
> **gali98 said:**
> Don't use FAT32!!! ... use NTFS.

+1 - (I agree)

> **Trebaruna said:**
> ... I'd say 10GB is plenty..

Unless you plan to burn DVDs  play it safe and give extra room for temp files - say 15GB in size

> .swap ...a little more than your machine's total RAM...+1 - (I agree)

---

### Post by gali98 on 2009-10-08
> **louieb said:**
> Unless you plan to burn DVDs  play it safe and give extra room for temp files - say 15GB in size
I thought most programs use /tmp for that?
Or is the swap partition mounted to /tmp?
Kory

---

### Post by louieb on 2009-10-08
> **gali98 said:**
> I thought most programs use /tmp for that?

Sorry for my confusing statement. Your right /tmp is used by most programs for temporary file storage. 

 Since a DVD can hold 4GB+ -  I was trying to say -  make the install partition larger.  /tmp is in the install partition making it larger gives /tmp more room too. 

BTW: /tmp get emptied out when you reboot. IIRC it happens on shutdown.

---

### Post by gali98 on 2009-10-09
Ooooohhhh... I get what you are saying now (after reading it about three times :))
Yes, I agree lol... Thanks for explaining.
Kory

---

