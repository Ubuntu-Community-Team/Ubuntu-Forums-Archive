---
title: "Problems with installing"
date: 2009-04-14
forum: New to Ubuntu
---

### Post by adobrakic on 2009-04-14
I just bought [this](http://www.newegg.com/Product/Product.aspx?Item=N82E16834115539&nm_mc=EMC-IGNEFL040909&cm_mmc=EMC-IGNEFL040909-_-Notebooks-_-L0B-_-34115539) laptop, and I want to install Linux Mint on it. I've installed before, and it wasn't a problem, but that was on a different computer.

This computer had a partition already in place, 110 for vista, and 106 unused. I plan to leave the Vista on the 110gb, and install Linux onto the remaining 106. I'm on live-cd right now, and i formatted the 106gb to ext3, and once I get to picking where I want Linux to be installed, I get:

"No root file system is defined."

Any ideas?

---

### Post by halitech on 2009-04-14
you need to select where / (root) will go, where /home will be installed, and your swap space (at bare minimum).

---

### Post by adobrakic on 2009-04-14
How would I go about doing that?

I've been looking around on Google, but can't find anything I understand.

---

### Post by halitech on 2009-04-14
read here to understand partitioning:

[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

and here on how to setup a dual boot:

[http://www.psychocats.net/ubuntu/dualboot](http://www.psychocats.net/ubuntu/dualboot)

---

### Post by adobrakic on 2009-04-14
I've read both, but they don't explain how to select where root, home and swap will be. I'm familiar with actually installing Ubuntu, just never had to select where those three things should be placed.

---

### Post by halitech on 2009-04-14
you need to create the partitions in the area that you want to install, not just creae 1 big partition.

---

### Post by adobrakic on 2009-04-14
[img]http://img26.imageshack.us/img26/4366/screk.png[/img]

I tried making the highlighted partition 5gb smaller, and I get this:

[img]http://img118.imageshack.us/img118/2312/screenshotdevsdagparted.png[/img]

I'm not sure why two unallocated partitions come up, but I right click on the 4.7gb one and go to "new," and get this:

[img]http://img118.imageshack.us/img118/2410/41614511.png[/img]


Is that what you were meaning for me to do? Make the partition for Linux smaller and add the 'home,' 'root,' and 'swap' space?

---

### Post by halitech on 2009-04-14
why not just delete /dev/sda3 completely, start the install and you should get an option about using the largest free space when it comes to where you want to install. that way it will do everything else for you.

---

### Post by adobrakic on 2009-04-14
When I do that, it seems like it'll install Linux over the whole hdd:

[img]http://img524.imageshack.us/img524/4483/screenshotinstall.png[/img]

The 45% is the sda3 I formatted

---

### Post by Jakey_TheSnake on 2009-04-14
Why not try manual? Then I _know_ you will get a nice little easy button that will ask you where you want to install root (or something similar), then you just select "/" and you're done!

edit: the button will be under preferences or suchlike when you go via manual.

---

### Post by adobrakic on 2009-04-14
^ that's what I was trying earlier

would this work:

[img]http://img54.imageshack.us/img54/6570/screenshotinstall1.png[/img]

---

### Post by Therion on 2009-04-14
> **adobrakic said:**
> ^ that's what I was trying earlier

would this work:
That's probably what I would do for simplicities sake.  

Once everything was installed and running smoothly I'd boot to a gParted LiveCD and resize the partitions to use the remaining free space (assuming I was going to keep the dual-boot arrangement).  50GB and 60GB partitions are fine though...  You could even partition the free space using NTFS and just use it as shared partition...  Choices, choices!!!

---

### Post by brunogirin on 2009-04-14
The extended partition thing is a different problem. I'll come to it later. But the first problem first. The bare minimum you need for Ubuntu is 2 partitions: a root partition and a swap partition (a /home partition is a good idea but not essential).

So from your screenshot, your ext3 partition (/dev/sda3) should be mounted as the root file system which means have its "mountpoint" set to / (a single forward slash). The 4.7GB unused space next to that partition could be used as swap, in which case the file system type should be linux-swap. Have a look at the attached parted screen shot from my system:
- /dev/sda1 is an ext3 file system that has a "Mountpoint" called / => this is the root partition
- /dev/sda5 is a file system of type linux-swap with no mount point

So to resolve your first problem, you need to specify for your partition /dev/sda3 a mountpoint of /. You should have a drop down box in the partition details that includes a number of options, including /.

Now onto the second problem. You can't have more than 4 primary partitions. If you want to have more, one of your primary partitions needs to by of type "extended" and include paritions of other types inside. To come back to my screen shot, you will notice that /dev/sda2 is of type extended and contains 2 partitions: /dev/sda5 and /dev/sda6. In your case, you could create one large extended partition to contain all your Linux partitions.

---

### Post by halitech on 2009-04-14
thats going to reduce the size of your windows partition and still leave you with half the drive blank.

Try the manual and you should be able to select the empty space

---

### Post by adobrakic on 2009-04-14
brunogirin, for some reason I can't find the mountpoint option anywhere. I see it on your screen, however mine doesn't show:

[img]http://img4.imageshack.us/img4/3672/screenshotdevsdagpartedm.png[/img]

I think it'd just be easier to install Linux over the whole hdd, then resize it with gParted, and install Vista afterwards.

---

### Post by halitech on 2009-04-14
no it wouldn't cause windows doesn't like to play well with other OSes so you would have to reinstall grub and worry about it being on extended partitions instead of primary, etc.

---

### Post by adobrakic on 2009-04-15
Okay, well after deciding what to do, I went with this choice:
[img]http://img54.imageshack.us/img54/6570/screenshotinstall1.png[/img]

Should I make the unallocated space NTFS?

---

### Post by halitech on 2009-04-15
I would go NTFS if you plan on putting files over 2 gig on it, fat32 will work just as well if you won't be putting any large files on it.

---

### Post by adobrakic on 2009-04-15
Alright, sounds good.

Thanks

---

