---
title: "Proper partition alignment WS20EARS with gparted?"
date: 2010-08-02
forum: New to Ubuntu
---

### Post by frostypepper on 2010-08-02
I have a 2Tib WD ears drive. I didn't realize initially that I had to format this drive in a certain way. Is there a easy way to do this and retain the data on the drive? 

Everything I have found via searches all point to fresh installs. Even if I cant save the data is it possible to get simplified instructions for gparted or similar?

While Im doing this would it be in my best interest to go with a gpt file table too? If I do will I have to manually make a separate tiny partition for the gpt table via gparted or can the advanced install of Ubuntu minimal handle it?

Finally I have a solid state disk on module (acer ap-sdm002gbpans-b) thats around 2Gib. Would I need to align this drive as well?

I certainly apologize for all the questions. Its just that I have been mulling over these problems for awhile and I needed to purge the questions and get some answers. My project has become so stymied; I just want to get the most out of this hardware.

---

### Post by sandyd on 2010-08-02
no way you can format without losing data.
[http://ubuntuforums.org/showthread.php?t=1456251&highlight=WD20EARS](http://ubuntuforums.org/showthread.php?t=1456251&highlight=WD20EARS)

also an entire thread here -> [http://ubuntuforums.org/showthread.php?t=1528312&highlight=western+digital](http://ubuntuforums.org/showthread.php?t=1528312&highlight=western+digital)
about it

---

### Post by frostypepper on 2010-08-03
Is there at least a way to re-align without a format? The drives currently have a msdos (mbr) for the partition table, which if I am not mistaken is perfectly fine for a 2Tib drive.

---

### Post by frostypepper on 2010-08-09
I have contacted Apacer about the SDM disk-on-module about alignment similar to a ssd. My reply was that they are still testing whether alignment is needed and what procedures are needed. 

I did read somewhere that these things need to observe 128 byte sectors. Now if standard formating tools assume a 512 byte sector then things should be ok. 512/4=128 bytes, so these default sector formats will span four 128 bytes ones. This should in theory at least not degenerate read/write performance.

Hope it helps somebody!

---

### Post by kr651129 on 2010-08-09
.

---

