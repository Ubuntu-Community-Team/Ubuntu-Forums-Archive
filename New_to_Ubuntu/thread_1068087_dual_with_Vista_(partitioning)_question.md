---
title: "dual with Vista (partitioning) question"
date: 2009-02-12
forum: New to Ubuntu
---

### Post by mordi05 on 2009-02-12
Hi.
I would like to add Ubuntu along side Vista on my newly bought laptop.

However i am a bit rusty/unskilled on the rules of partitioning.
This is what I have to work with:

      [http://i44.tinypic.com/rlg6f4.jpg](http://i44.tinypic.com/rlg6f4.jpg)

I would like to keep those NTFS partitions that are on there, use the FAT32 for sharing, and add Ubuntu in the unallocated space.

But I see that they are all listed as "primary" will this be a problem? And what could I do to fix it?

Also if I remember correctly I will need a /, a /boot and a swap partition for ubuntu. Which of these need to be "primary"?

And last question, how big do my /boot need to be?

Many thanks in advance.

---

### Post by LowSky on 2009-02-12
Make the unallocated into a extened partiton oand then you can install more logical partions all you want, no need for "primary"

you really only need a / and swap.
though most people now suggest /, /home and swap (this is what I use)

---

### Post by kestrel1 on 2009-02-12
By the looks of it you should be OK as you have three primary partitions on the drive.
You can make an extended in the unused space & partition that to install Ubuntu.
I havr made a pdf file with instructions. If you want to download it look here:
[http://www.kcsdorset.co.uk/pdf/UbuntuInstall.pdf](http://www.kcsdorset.co.uk/pdf/UbuntuInstall.pdf)
Probably better pdf's else where. Let me know what you think.

---

### Post by mordi05 on 2009-02-12
Ok, thanks guys.
So to get it straight, I should make the unallocated space extended from within Vista before I boot the Ubuntu CD?

Also kestrel1, I see you don't make a /boot partition in your guide. What are the pros/cons of this?

---

### Post by kestrel1 on 2009-02-12
No real need for the /boot, others may think differently.
Personally I would make the extended partition & logical partitions in it using the Ubuntu live CD. You can do it during the install process.
If you want a bit more info contact me via my website, I do not charge. Always happy to help.
[http://www.kcsdorset.co.uk](http://www.kcsdorset.co.uk)

---

### Post by mordi05 on 2009-02-12
I'm sorry, I must be particularly slow. I am looking at the Intrepid Ibex manual partition page and still don't get this.

When I highlight the unallocated space I have only the option to make "new partition", and then I have to chose either primary or logical, as well as file system.

I don't see how I can make the unallocated space en extended partition.

Could I just make "/" my 4th primary partition and set swap as logical?

---

### Post by kestrel1 on 2009-02-12
You need to make the new partition & select logical. It will make the extended & put the logical in there.
You couldn't make '/' the fourth primary as an extended would make five & a logical need to be in an extended.

---

### Post by mordi05 on 2009-02-12
Ok, then.

So I first make one logical partition for (unallocatedSpaceSize - swapSize) for mount point /.

Then another logical partition for the rest of the allocated space as swap.

---

### Post by kestrel1 on 2009-02-13
Depends on how you want to set up your HD.
If you intend using Linux more & more I would suggest that you setup 10-15GB for your '/' partition, most of the space left for '/home' & 1 - 2GB for swap.
If you have a seperate '/home' partition you can carry on using that if you need to re-install & you won't delete your impportant data.
Say you have a 40GB drive, have 10 - 15GB for '/' , 23 - 28 for '/home' & what is left for swap.
My guide may help you.

---

