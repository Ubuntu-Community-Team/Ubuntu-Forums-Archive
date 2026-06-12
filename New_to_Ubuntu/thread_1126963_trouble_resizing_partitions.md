---
title: "trouble resizing partitions"
date: 2009-04-15
forum: New to Ubuntu
---

### Post by querent on 2009-04-15
I'm trying to increase the size of my vista partition slightly.  (please don't hit me!  WoW patch!  I couldn't get Wine to work!)

When I run gparted from a live disk, I see the windows partition, then the linux.  I resized the linux, but the space was taken from the _right_ side.  So now it's windows, linux, then unallocated.  And it won't let me increase the ntfs chunk.  is there a way to deal with this?

---

### Post by bodhi.zazen on 2009-04-15
We need more details.

Post a screen shot of gparted.

---

### Post by querent on 2009-04-15
Thank you for your help.

Terribly sorry, but how?

---

### Post by querent on 2009-04-15
thought i had it there

---

### Post by querent on 2009-04-15
Here it is!  Running gparted from the hdd, not the live disk here.

---

### Post by -kg- on 2009-04-16
> **querent said:**
> I'm trying to increase the size of my vista partition slightly.  (please don't hit me!  WoW patch!  I couldn't get Wine to work!)

When I run gparted from a live disk, I see the windows partition, then the linux.  I resized the linux, but the space was taken from the _right_ side.  So now it's windows, linux, then unallocated.  And it won't let me increase the ntfs chunk.  is there a way to deal with this?

OK, I took a look at your screenshot.  Your Vista partition is a primary partition, and your Ubuntu partitions are inside of an Extended partition, making them Logical partitions instead of primary.

What you will need to do is to select your main Ubuntu partition (the ext 3, denoted as sda5) and move it to the right, next to your swap partition.  Then you will need to shrink the Extended Partition to the right, freeing up Primary partition space into which you can increase the size of your Vista partition.

I suggest reading [How To Partition]("https://help.ubuntu.com/community/HowtoPartition") in the Community Documentation.  This will give you a basic overview of what you need to do and why you need to do it, as well as step by step instructions on actually doing it.

---

### Post by querent on 2009-04-16
thanks for your help, but I'm still having issues.

After I re-extended the ext3 partition I selected the entire extended partition, but none of the options (resize, etc) were active.  meaning the buttons were all greyed out.

I even tried running gparted with sudo (though I think gparted always runs with root privilege, right?).

The link you provide (which I thank you for) said to shrink one of the logicals, then shrink the extended down, effectively squeezing everything together over the free space inside and leaving an equivalent amount free outside (with the primaries).  suddenly, though, i could no longer shrink the logicals.  (i did this once, in the pic above.)  who knows.

thoughts would be nice, but i'm probably just going to reformat.

Thanks!

---

### Post by Captain_Glen on 2009-04-16
Boot gparted off the live cd.  Then right click on the linux swap partition and click swap off.  Then move you linux partition so it is next to the swap partition.  Now you should be able to resize the whole extended partition by right clicking it and selecting resize/move.

---

### Post by nandemonai on 2009-04-16
What the above poster said. NEVER repartition from the disk you are trying to partition. Biiiig no no.

I trust you also have full backups right?

---

### Post by querent on 2009-04-16
Yeah, I didn't try to repartition from the hdd I was running off of.  It was just easier to grab the screen shot that way.

And yeah, I got backups.

Thanks all!  I'll try the newest suggestion when I get back this afternoon!

---

