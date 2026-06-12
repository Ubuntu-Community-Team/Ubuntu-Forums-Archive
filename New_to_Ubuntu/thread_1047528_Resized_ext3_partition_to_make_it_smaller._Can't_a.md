---
title: "Resized ext3 partition to make it smaller. Can't allocate space to NTSF"
date: 2009-01-22
forum: New to Ubuntu
---

### Post by barsofham on 2009-01-22
I'm trying to decrease the size of my Ubuntu partition (ext3) and increase the size of my Windows partition (NTFS). I Already resized the ext3 partition and moved the unallocated space next to the NTFS partition. Why can't I allocate that space to the NTFS? It doesn't give me the option to increase the size of the NTFS partition. It only gives me the option of increasing the ext3 partition. Any thoughts? I'm using the Intrepid Ibex Live CD and running GParted. Here's a screen shot.
[IMG]http://farm4.static.flickr.com/3522/3217836439_72e9b14ce5.jpg[/IMG]

Thanks for your help guys!

---

### Post by taurus on 2009-01-22
It is because your unallocated space is in extended partition.  And right now, you cannot resize your extended partition because you have the swap partition mounted (locked).  Therefore, you need to unmount you swap first.  Then, resize your extended partition so the unallocated space should be in primary, after /dev/sda1.

Applications -> Accessories -> Terminal
```
sudo swapoff
```
You probably have to restart gparted.

---

### Post by drs305 on 2009-01-22
You are trying to expand the primary partition with space in an extended partition. First shrink the extended partitiion (sda2). You have to select it from the bottom section, you can't click on it in the top. Unmount all the partitions.

Shrink sda2 and it will leave free space *outside* the extended partition. Then you will be able to add it to the first partition.

Back up data before moving anything around.

---

### Post by avtolle on 2009-01-22
The unallocated space is inside the extended partition, and as I understand things, this makes it unavailable to any partition outside the extended partition. My thought on this is that you will need to shrink the extended partition, and move it so the unallocated space is then adjacent to the NFTS partition then resize the NFTS partition into it. You will, of course, need to have the partition unmounted to do this, and I recommend using a Live CD for this purpose. For safety's sake, if you have an external hard drive you can use for this purpose, back up your files from the Ubuntu partition onto it. BTW, you will need to select the swap partition and select "swapoff" on the dropdown menu under Partition (as I recall) to unlock the extended partition so it may be moved/resized. This sounds rather daunting to me, and hopefully someone with more knowledge can come into the discussion with a good way to do this.

---

### Post by barsofham on 2009-01-22
Thanks guys! That did the trick.


For other users, I didn't use the terminal since it had a bunch of options and I didn't know what I was doing. I used GParted and selected the right clicked on the swap partition and turned it off. Then I clicked on sda2 and resized it, then resized the ntfs partition.

Thanks again.

---

