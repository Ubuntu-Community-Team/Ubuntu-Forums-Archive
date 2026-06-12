---
title: "Strange Partition"
date: 2011-04-17
forum: New to Ubuntu
---

### Post by DaveMcC on 2011-04-17
Since I decided to upgrade this computer from ubuntu 32bit to 64bit, I have noted a strange partition when I ran the disk utility
Ignore the partition on the left, thats winxp "needed" but instead look at the one on the right I have high-lite the top part showing 56gb the lower part is the old 32bit partition
Why is this still here after I re-formatted he drive on the upgrade

[IMG]http://i7.photobucket.com/albums/y282/dtmcc/Ubuntu00-1.jpg[/IMG]

Dave

---

### Post by Leppie on 2011-04-17
the screenie isn't very clear...

---

### Post by scott-ian on 2011-04-17
An extended partition is one that contains others inside of it.  On your computer, it contains the Linux system files and swap memory.

---

### Post by Dondermans on 2011-04-17
I would like to recommend choosing less compression when saving as .jpg or using -for example- .png instead.

---

### Post by scott-ian on 2011-04-17
For good screen shots, you can press the "print screen" button on your keyboard and save as a png.

---

### Post by DaveMcC on 2011-04-17
I can give you any size of screen shot you like, its just that most of the other fourms like nothing larger than 480 wide

Dave

---

### Post by scott-ian on 2011-04-17
What exactly are you asking about?  Is it the contents of the extended partition?

---

### Post by Leppie on 2011-04-17
> **scott-ian said:**
> What exactly are you asking about?  Is it the contents of the extended partition?
i think he is indeed worried about the extended partition.

---

### Post by scott-ian on 2011-04-17
I don't exactly see the problem.  The extended partition contains a standard Ubuntu install.

---

### Post by DaveMcC on 2011-04-17
Is this normal?

[IMG]http://i7.photobucket.com/albums/y282/dtmcc/Ubuntu01.jpg[/IMG]

Note the diff

[IMG]http://i7.photobucket.com/albums/y282/dtmcc/Ubuntu00-2.jpg[/IMG]


Thats 3 ubuntu partitions
Dave

---

### Post by Dutch70 on 2011-04-17
When you upgraded from 32 bit to 64 bit, you installed the 64-bit into the partition where the 32-bit was. Which is correct & what you should have done.

Also, It would be much better if you would use the paper clip in the toolbar to attach your pic, no matter what size it is. I for one don't want to have to scroll sideways to see the pic.

Here is an example of an attached pic & my partitions in Disk Utility.

Edit: OMG, I see I was too late.

---

### Post by Blasphemist on 2011-04-17
> **DaveMcC said:**
> Since I decided to upgrade this computer from ubuntu 32bit to 64bit, I have noted a strange partition when I ran the disk utility
Ignore the partition on the left, thats winxp "needed" but instead look at the one on the right I have high-lite the top part showing 56gb the lower part is the old 32bit partition
Why is this still here after I re-formatted he drive on the upgrade

[IMG]http://i7.photobucket.com/albums/y282/dtmcc/Ubuntu00-1.jpg[/IMG]

Dave

Yours shows correct. ext4 is your ubuntu and the swap is using the rest of that extended partition.

---

### Post by DaveMcC on 2011-04-17
Thanks for a look at your drive "Dutch70" it is looking normal, mine that is
Could you explain more on ( use the paper clip in the toolbar to attach your pic)

Dave

---

### Post by Dutch70 on 2011-04-17
Sure, let's just say you save a pic to your desktop. When you click the paper clip in the toolbar of your post, like in the pic below. It will bring up a window, just click "browse" navigate to the pic on your desktop that you want to post, click it, and then click upload. You won't see the pic before you post it, unless you click "preview" instead of "submit".

---

