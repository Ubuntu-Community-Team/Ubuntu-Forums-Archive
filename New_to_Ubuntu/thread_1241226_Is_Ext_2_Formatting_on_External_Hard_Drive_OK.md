---
title: "Is Ext 2 Formatting on External Hard Drive OK?"
date: 2009-08-15
forum: New to Ubuntu
---

### Post by mikodo on 2009-08-15
Hello everyone,

When I wanted to use an external hard drive that previously had a Conficker worm on it from my days with Vista, I reformatted it with Gparted. Now I am using it as a medium for backups with Ubuntu. It is formatted as Ext2. I'm reading this is old compared to Ext3 and 4.

Is it alright to leave it as such? If I want to use it for more than just backups, should I learn how to format it to Ext 3 or 4? 

Thank you.

See screenshot of same.

---

### Post by jrothwell97 on 2009-08-15
ext2 is fine. It's well supported and mature, so there's no reason why you can't use it. Of course, you can use ext3 or ext4 if you want, but ext2 is just fine.

---

### Post by kayvortex on 2009-08-15
The only issue is the fact that ext3/4 are journaled file systems, whereas ext2 is not; so, in an unclean shutdown (like a crash), your data would be "safer" under ext3/4. Seeing as your hard drive is being used as a backup device, I'd personally recommend, in order to safeguard your data as much as possible (especially as you don't seem to have used much of it yet, so reformatting wouldn't be too much of an inconvenience), using ext3. I'd exclude ext4 for now for the same reason because enabling extents has issues on losing data under a crash if data hasn't been written to the disk yet (I've installed jaunty on ext4 and fsck has made file system repairs on hard reboots; so it's better to be safe and stick with ext3).

But, then again, it's not that much of an issue: I wont rebuke you for sticking with ext2.

---

### Post by mikodo on 2009-08-15
> **kayvortex said:**
> The only issue is the fact that ext3/4 are journaled file systems, whereas ext2 is not; so, in an unclean shutdown (like a crash), your data would be "safer" under ext3/4. Seeing as your hard drive is being used as a backup device, I'd personally recommend, in order to safeguard your data as much as possible (especially as you don't seem to have used much of it yet, so reformatting wouldn't be too much of an inconvenience), using ext3. I'd exclude ext4 for now for the same reason because enabling extents has issues on losing data under a crash if data hasn't been written to the disk yet (I've installed jaunty on ext4 and fsck has made file system repairs on hard reboots; so it's better to be safe and stick with ext3).

But, then again, it's not that much of an issue: I wont rebuke you for sticking with ext2.

Thanks for the post and advice. I changed the external hard drive to ext3. I agree it is best to use all precautions with back upped data as I can, (binary files to follow). With the journaled service in ext3, I do notice it being slower to access; A penalty for the extra security, I suppose.

mikodo

---

### Post by mrbiggbrain on 2009-08-16
If its a platter based HDD, EXT3, however for flashdrives and SSD always use EXT2, the journaling will kill a flash drive or SSD quickly

---

### Post by SunnyRabbiera on 2009-08-16
There is nothing really wrong with using EXT2, its an older FS but not nearly as useless as say FAT32.

---

### Post by mikodo on 2009-08-16
> **mrbiggbrain said:**
> If its a platter based HDD, EXT3, however for flashdrives and SSD always use EXT2, the journaling will kill a flash drive or SSD quickly

Thanks for the input. It's a platter HDD, so I guess I got this one right. (EXT3).

mikodo

---

