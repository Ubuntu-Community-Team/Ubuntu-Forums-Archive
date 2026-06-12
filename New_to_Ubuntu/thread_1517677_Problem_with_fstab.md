---
title: "Problem with fstab"
date: 2010-06-25
forum: New to Ubuntu
---

### Post by nemodot on 2010-06-25
My computer won't boot now that I messed up with fstab.

I was following [this tutorial]("http://www.techenclave.com/guides-and-tutorials/automounting-ntfs-partitions-during-startup-ubuntu-161249.html") on how to auto mount ntfs partitions but something must have gone wrong.

When I turn on the computer all i get is a black screen.

How can I edit the fstab file in order to erase the lines i added?

---

### Post by bodhi.zazen on 2010-06-25
you will have to boot a live CD, mount your root partition, and edit fstab

Assuming your root partition is /dev/sda1

Boot a live CD and run:

```
sudo mount /dev/sda1 /mnt
gksu gedit /mnt/etc/fstab
```

edit the file, save the changes, and reboot to hard drive.

---

### Post by oldfred on 2010-06-25
The instructions said to run this:

sudo mount -a

That confirms that fstab is ok or not. If ok it just returns to the terminal.
Or it lists errors. You need to run that before rebooting to prevent issues.

---

### Post by philinux on 2010-06-25
Also run this from the livecd.

```
sudo blkid
```

And make sure the ones quoted on fstab match up.

---

