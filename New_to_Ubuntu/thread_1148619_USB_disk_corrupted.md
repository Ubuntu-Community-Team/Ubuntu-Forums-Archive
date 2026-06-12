---
title: "USB disk corrupted?"
date: 2009-05-04
forum: New to Ubuntu
---

### Post by gatorbrit on 2009-05-04
I having a western digitial passport USB disk that I use all the time.  I am frequently having the disk become read only and then when i use fcsk it finds lots of corrupted files and writes them out as FSCK0001.REC etc etc.

Is there a way to tell if this disk is fried and I should junk it? 

Would reformatting it help?

If so, I assume I should format it to FAT 32?


THanks


Rich

---

### Post by card_ace on 2009-05-04
i have this problem too.  I have a WD 250 GB external HDD, and yesterday when i plugged it into my parents' vista machine it was read only.  ok, annoying, but no big deal.  next i went back to my machine on ubuntu and i'm assuming it was still read only because i couldn't copy a file to it.  the "paste" button was grayed out.  but today i ran it on an XP machine and its fine again.  mine is formatted to NTFS.  i'm just plain confused at the moment :confused:

---

### Post by gatorbrit on 2009-05-04
I think that the disk can behave badly if it is unplugged without properly unmounting it.   So that's one thing to check for.   After mine has gone read only, running fcsk solves this issue but I end up with a bunch of files getting trashed which is obviously not great...

---

### Post by llamabr on 2009-05-04
> **gatorbrit said:**
> I think that the disk can behave badly if it is unplugged without properly unmounting it.   So that's one thing to check for.   After mine has gone read only, running fcsk solves this issue but I end up with a bunch of files getting trashed which is obviously not great...

I think that's right.  Before you yank it out of a windows box, be sure to 'unmount' it by clicking that little button in the lower right hand box, called 'safely eject disk' or something.

If windows is not finished writing when you pull it out, it'll corrupt the entire fs.

---

### Post by card_ace on 2009-05-04
take it from experience.  MAKE SURE YOU SAFELY EJECT IN WINDOWS!!!  i didn't do it one time.  entire disk went screwy.  windows couldn't read it all all and linux could read it perfectly.  still not sure how that one happened but i had to reformat to fix it.  don't go down that road if you can help it.  but i'm not sure why it went read only this time.

---

### Post by HermanAB on 2009-05-04
Howdy,

It is important that you use a journaled file system on removable disks.  If it is Linux only, then Ext3 is good.  If you need to share it with Windows, then you have to use NTFS.  

Never use Ext2 or FAT on removable disks.  Those file systems are inherently unreliable.

---

### Post by gatorbrit on 2009-05-04
Thanks - I just reformatted it as NTFS and I am re-copying all my files over.  We'll see how it goes.

---

