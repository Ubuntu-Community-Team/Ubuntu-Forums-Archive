---
title: "Using GParted?"
date: 2009-01-24
forum: New to Ubuntu
---

### Post by bludderz on 2009-01-24
Hi there,
I'm running Ubuntu on my external hard drive, but need to remove it, as I am going to install it on my internal hard drive.
How would I go about formatting the external hard drive?
I'm thinking of running GParted while on the LiveCD.
How, and where do I download GParted, and how large is it?
Also, is it even possible to run GParted while on the LiveCD to format my external hard drive?

Thanks,
Aaron.

---

### Post by taurus on 2009-01-24
The LiveCD already has gparted (System -> Administration) so no need to download anything if you run Ubuntu from it.  Just delete all the partitions and create a new one that takes up the whole harddrive and format it to whatever filesystem you want.

---

### Post by drs305 on 2009-01-24
Taurus beat me to it, but I'll add *gparted* is called "Partition Editor" in the menu he referenced.

---

### Post by bludderz on 2009-01-24
I removed all the partitions I could.
There are still two things listed:

/dev/sda1;
unallocated

It also doesn't give me the option to format to.
Help Please,
Aaron

---

### Post by bludderz on 2009-01-24
Whoops,
Disregard my last post.
Just had to unmount the drive.
Thanks for the helo ;)

Aaron.

---

### Post by aheckler on 2009-01-24
It should be noted that GParted does not really format a drive *per se*. To truly format (ie, erase everything) a disk, you may want to use DBAN, which there is a LiveCD version of as well. This will literally overwrite all the data on your drive.

---

### Post by drs305 on 2009-01-24
First, make sure you are trying to format the correct device. 
Next:
Are you trying to format sda1 or the unformatted space? Once you have selected sda1, *if it is unmounted*, you should be able to select the formatting. If you click on the top menu item *Partition* and see "Unmount" available, it means it is still mounted and you must unmount it first by clicking on *Unmount*. Then you should be able to select the type of formatting with the *Partition > Format to* option.

For the unallocated space, you will first have to create a partition, then you can format it.

---

