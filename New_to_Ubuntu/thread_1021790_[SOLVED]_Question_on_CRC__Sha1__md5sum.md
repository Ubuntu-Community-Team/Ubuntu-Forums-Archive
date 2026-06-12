---
title: "[SOLVED] Question on CRC / Sha1 / md5sum"
date: 2008-12-25
forum: New to Ubuntu
---

### Post by newbee70 on 2008-12-25
I need your help. I made a **"partimage"**backup of my drive to an internal HD, and then copied it to a removable usb HD " both formatted ntfs.
I then burned a DVD data disk of the file. 

When I tested the images I get a difference in CRC on the hard disks, but both the md5sum and the sha1 match on all 3 media devices.

here is my test results, but what is going on? Which image is right?


ghost@desktop2:/media/D$ cksum ghost2.bz.000
200196611 2699063387 ghost2.bz.000

ghost@desktop2:/media/E$ cksum ghost2.bz.000
3660823848 2699063387 ghost2.bz.000

ghost@desktop2:/media/cdrom0$ cksum ghost2.bz.000
200196611 2699063387 ghost2.bz.000

<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>
ghost@desktop2:/media/D$ sha1 ghost2.bz.000
585f98e34474035e106c480aac999909240864a9  ghost2.bz.000


ghost@desktop2:/media/cdrom0$ sha1 ghost2.bz.000
585f98e34474035e106c480aac999909240864a9  ghost2.bz.000


ghost@desktop2:/media/E$ sha1 ghost2.bz.000
585f98e34474035e106c480aac999909240864a9  ghost2.bz.000

<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>
ghost@desktop2:/media/D$ md5sum ghost2.bz.000
2bc11118b2e063f97c17e0d0469a91dc  ghost2.bz.000


ghost@desktop2:/media/E$ md5sum ghost2.bz.000
2bc11118b2e063f97c17e0d0469a91dc  ghost2.bz.000

ghost@desktop2:/media/cdrom0$ md5sum ghost2.bz.000
2bc11118b2e063f97c17e0d0469a91dc  ghost2.bz.000

---

### Post by Trebaruna on 2008-12-27
I've never used cksum. In fact, I wasn't aware of its existence before this post.

The chances of a collision in both md5 and sha1 for the same file (same checksum, different data) are basically zero. If md5sum and sha1sum say it's the same, it is. Don't worry about it.
Also, you might as well stop using cksum. You're better of using md5, and better still using sha1sum. There's even sha256 and the likes, but unless you are paranoid or have some high security application, don't bother.

---

### Post by newbee70 on 2008-12-27
> **Trebaruna said:**
> I've never used cksum. In fact, I wasn't aware of its existence before this post.

The chances of a collision in both md5 and sha1 for the same file (same checksum, different data) are basically zero. If md5sum and sha1sum say it's the same, it is. Don't worry about it.
Also, you might as well stop using cksum. You're better of using md5, and better still using sha1sum. There's even sha256 and the likes, but unless you are paranoid or have some high security application, don't bother.

Thanks for the reply:  helps to relieve my worries about having a bad backup.

I use checksum because partimage uses it when it loads the image for re installation.

---

