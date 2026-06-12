---
title: "Flash Drive Partition Screw Up"
date: 2010-05-04
forum: New to Ubuntu
---

### Post by Zionoxis on 2010-05-04
Hello everyone. I'm completely new and well, I have accidentaly messed up my flash drive while trying to make it so other computers can boot Ubuntu from it. As I just installed Ubuntu today for my first time, I think it may not have been my best descision.

Either way, I was following a guide that told me to type commands into Terminal. It deleted the partition, created a new one, and set it as FAT16. My 8GB flash drive, is now a 750mb flash drive because I messed up somewhere. I have returned the file system to FAT so Windows 7 can read it...

Does anyone know how I can return my 8GB's back and the CORRECT way to set it up so I can boot from it?

---

### Post by pizza-is-good on 2010-05-04
OK, here we go.

Go to Ubuntu. Plug in your flash drive. Open up GParted.
(If you don't have it do:
```
sudo apt-get install gparted
``` in the terminal)

On the top right hand corner of GParted, you will see a drop down menu with all your data volumes. Find your flash drive, and click on it.

Right click on all the partitions that you see in your usb, and delete them all. (This will delete all your data in the usb)

Then click apply on top (Green check mark I think)

Wait for it to get done.

Then right click the empty space (gray) and click new. Set the format to FAT32. Make sure it says 'primary partition' somewhere.

Then do apply again.

Wait for it. Your usb is now back to normal, if all went well.

(Sorry for being a little vague. I'm going from memory here, but I am sure I am right.:lolflag:)

Now, about the bootable. (Make sure to unplug and re-plug in your usb)

Go to the Ubunut USB start-up disk createor.

Find the .iso

Select your flash drive.

Select the options you want, and create it.

---

