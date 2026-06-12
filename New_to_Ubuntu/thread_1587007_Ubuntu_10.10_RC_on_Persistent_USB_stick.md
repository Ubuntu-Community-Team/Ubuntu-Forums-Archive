---
title: "Ubuntu 10.10 RC on Persistent USB stick?"
date: 2010-10-02
forum: New to Ubuntu
---

### Post by oregonbob on 2010-10-02
Has anyone successfully installed a persistent USB stick of the new 10.10?

So far I have only found this for older versions. Or maybe it is crazy to want to persistent a beta (RC). I just like to play with it and have it save my changes that only persistent does.

---

### Post by skyjacker on 2010-10-02
Go to this site and it will give you instructions on how to create your own persistent partition (casper rw) file    [http://www.pendrivelinux.com/create-a-larger-than-4gb-casper-partition/](http://www.pendrivelinux.com/create-a-larger-than-4gb-casper-partition/)

---

### Post by oregonbob on 2010-10-04
I achieved this first partitioning an 8GB USB stick with a 2GB FAT32, then I boot a 10.10RC live CD and told it to install Ubuntu on the USB drive. It made the remainder of the drive an ext4 + 370MB swap. It works! I've only booted it around 4 times so I don't know if there are any problems.

I tried booting the USB stick on an older PC and got a grub error that it couldn't find partition. I should have made the FAT32 partition only around 800MB and this would not be an issue. So keep your FAT32, first partition under 1024 cyl boundary or older BIOS can't see it.

I have persistence and everything. It took around 12 hours to install ubuntu on USB when using an old PC.

---

### Post by beew on 2010-10-04
I created a live usb with 3g persistence for Maverick by using just the start up disk utility from Lucid. Worked great. But then my start up disk utility may be newer than the one in the Ubuntu repo because I have added a lot of ppas, so it could be from one of them (I do remember there was an upgrade about a montb ago though can't remember where it was from)

---

