---
title: "Resizing an extended partition"
date: 2009-04-11
forum: New to Ubuntu
---

### Post by m_ad on 2009-04-11
I had a computer with JUST vista on it, and wanted to install not only Ubuntu, but a few other *nix OSes as well. I loaded the Ubuntu live cd and fired up gparted.

I created 2 primary partitions (10GB each) in the beginning of the drive, which is Ubuntu and openSUSE. I created an extended partition on the rest of the disc, and put my swap space and home partitions inside it. I had 30GB left of unallocated space INSIDE the extended partition.

Now, I planned on installing other OSes inside this extended partition using the unallocated space. Today, when I went to create a 10GB partition using the 30GB of unallocated space using the Ubuntu live cd, the 30GB that I had put INSIDE the extended partition is now outside of it.

This is a problem because I potentially want to install more OSes.



To make a long story short (actually, the story is already long)..

Using the Ubuntu live cd and gparted, I cannot resize the extended partition to include this unallocated space.

Any suggestions?

---

### Post by Elfy on 2009-04-11
Is the unallocated space contiguous with the extended - if not you need to move partitions about so that it is.

Can you do a screenshot of gparted.

---

### Post by m_ad on 2009-04-11
Yes, it is contiguous. I'll take a screenshot now.. give me a minute.

Thanks for the speedy response.

---

### Post by m_ad on 2009-04-11
Here is a screenshot

and somehow there is still 8mb of unallocated space inside the extended :confused:

---

### Post by Elfy on 2009-04-11
Right click swap and turn it off then you should be able to move the unallocated into the extended.

Turn the swap back on when you've finished

---

### Post by m_ad on 2009-04-11
Ah, this worked!

Didn't even think of that. Thanks a lot forestpixie, I appreciate your time.

Hey, what happened to the thanks button?

---

### Post by Elfy on 2009-04-11
welcome :)

---

