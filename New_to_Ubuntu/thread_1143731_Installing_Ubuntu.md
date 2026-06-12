---
title: "Installing Ubuntu"
date: 2009-04-30
forum: New to Ubuntu
---

### Post by daniell59 on 2009-04-30
I was in the process of installing Ubuntu, and I did not know how to go any further. I am attaching an image of my last step. I am sorry for lack of clarity in the image. I want to put Ubuntu on my second hard drive. I guess I will need help with each step.

Thanks

---

### Post by johnwillis on 2009-04-30
You will need to format your free space with EXT3 (use the installer) and leave another 1Gb of space and use the SWAP format... 

Make a note of the drive letter (something like sdb2) where you put the ext 3 drive and make sure you select the mount point "/"

This is effectively the same as your C drive in windows...

**Make sure you have a backup of your data before you format anything...**

One installed you should be able to dual boot the system between Windows and Ubuntu using the menu that has been installed on startup..

Hope it helps!

---

### Post by Xero Xenith on 2009-04-30
+1 to johnwillis.

The Windows installer lets you install into free space, and it formats it into NTFS for you; Ubuntu doesn't do that in Manual install mode. Seeing as you have oodles of free space right there, you can select to install Ubuntu into the largest contigious free space on the previous step to the one you showed us, and it will configure it all for you. It should automatically do exactly what johnwillis said, actually.

---

### Post by daniell59 on 2009-04-30
> **johnwillis said:**
> You will need to format your free space with EXT3 (use the installer) and leave another 1Gb of space and use the SWAP format... 

Make a note of the drive letter (something like sdb2) where you put the ext 3 drive and make sure you select the mount point "/"

This is effectively the same as your C drive in windows...

**Make sure you have a backup of your data before you format anything...**

One installed you should be able to dual boot the system between Windows and Ubuntu using the menu that has been installed on startup..

Hope it helps!

How do I format my free space?
Please forgive me for any inane questions.

---

### Post by johnwillis on 2009-04-30
> **daniell59 said:**
> How do I format my free space?
Please forgive me for any inane questions.

When you get to the partition section like you are there let ubuntu use the option "Use largest free space" 

This will use the free disc space and set everything up for you...

-J

---

### Post by daniell59 on 2009-04-30
> **johnwillis said:**
> When you get to the partition section like you are there let ubuntu use the option "Use largest free space" 

This will use the free disc space and set everything up for you...

-J

How do I assure that Ubuntu will be put on the HD that does not have Vista on it. I saw that option, but was afraid that it would wipe out Vista.

---

### Post by johnwillis on 2009-04-30
> **daniell59 said:**
> How do I assure that Ubuntu will be put on the HD that does not have Vista on it. I saw that option, but was afraid that it would wipe out Vista.

If you have been careful setting it up, make sure you select install to free space then it will ONLY install to free space.

This should leave Vista alone...

As I say make sure you backup your data... that way if things do go wrong... you'll be ok.

Better to be safe than sorry...

-J

---

### Post by daniell59 on 2009-04-30
> **johnwillis said:**
> If you have been careful setting it up, make sure you select install to free space then it will ONLY install to free space.

This should leave Vista alone...

As I say make sure you backup your data... that way if things do go wrong... you'll be ok.

Better to be safe than sorry...

-J

Thanks
Will "select to free space" put Ubuntu on my second hard drive?
That is where I want it.
I better back up what is important, and get out all of my installation cds, just in case.

---

### Post by johnwillis on 2009-04-30
> **daniell59 said:**
> Thanks
Will "select to free space" put Ubuntu on my second hard drive?
That is where I want it.
I better back up what is important, and get out all of my installation cds, just in case.

Yes it will or should install to the free space you have made available...

Like I say worst case is that your restore from a backup...

You have inspired me to write a simple step by step guide to installing Ubuntu...

Subscribe to my RSS feed [www.john-willis.com](www.john-willis.com) to make sure you get told when I update the site with a guide...

---

### Post by daniell59 on 2009-04-30
> **johnwillis said:**
> Yes it will or should install to the free space you have made available...

Like I say worst case is that your restore from a backup...

You have inspired me to write a simple step by step guide to installing Ubuntu...

Subscribe to my RSS feed [www.john-willis.com](www.john-willis.com) to make sure you get told when I update the site with a guide...

Thanks

---

### Post by daniell59 on 2009-04-30
> **daniell59 said:**
> Thanks

Oh, one more clarificaton. Should I use manual install?

---

