---
title: "Resizing active ext4 partition on Lucid, is it safe?"
date: 2010-05-31
forum: New to Ubuntu
---

### Post by occams_beard on 2010-05-31
I am currently dual booting Lucid and Karmic. My plan was to do a fresh install of Lucid and gradually move my stuff over from Karmic. Now that that is done, I have no use for Karmic and want delete the partition and free up the drive space its using.

How safe is it to resize the active ext4 partition on Lucid? 

I read some reports where data loss occurred when using Gparted on Jaunty to resize ext4. Is this still a problem? The very last thing I want to happen is data loss, or end up having to reinstall the OS, which would take me hours.

I am using Lucid 64 bit.

Any thoughts would be appreciated. I probably won't even risk it, but just was wondering how safe it is.

---

### Post by ron999 on 2010-05-31
No, don't risk it.
Use Gparted from the Ubuntu LiveCD.

---

### Post by nhasian on 2010-05-31
you should not resize a mounted partition.  boot off the liveCD first and while it is not mounted, then you can resize it.  of course always backup before modifying your partitions.

---

### Post by sdennie on 2010-05-31
I would be surprised if you can resize an ext4 partition while it's mounted but, even if you can, I would recommend using a live CD to do the resize.  ext* partition resizes are fairly (extremely?) reliable using that method.  Having said that, having a full backup of your data is highly encouraged before doing something like that.

---

### Post by wilee-nilee on 2010-05-31
Ubuntu does not have a virtual partition device for the main OS, as suggested you have to do it from a live cd or any other partitioning cd that is linux friendly.

If your question is can you safely re-size the partition from a live cd you should have no problems, but have everything backed up just in case, anything can happen and none of us know your setup.

---

### Post by occams_beard on 2010-06-01
Thank you everyone for the replies.

I think I will just format the karmic partition and use it for data storage. I don't want to risk obliterating my nice Lucid install :)

How would I go about cleaning out the karmic references in Grub after formatting my karmic partition? sudo update-grub ?

---

### Post by wilee-nilee on 2010-06-01
> **occams_beard said:**
> Thank you everyone for the replies.

I think I will just format the karmic partition and use it for data storage. I don't want to risk obliterating my nice Lucid install :)

How would I go about cleaning out the karmic references in Grub after formatting my karmic partition? sudo update-grub ?

If you just delete or reformat the Karmic partition I think the update-grub should remove Karmic from grub. If you have any problems or need more info you can post sudo fdisk -l and that will tell us what is actually there as far as partitions go. l=small case L

---

