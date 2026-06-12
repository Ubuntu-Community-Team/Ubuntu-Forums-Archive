---
title: "Installing from LiveCD to SD Card"
date: 2011-02-06
forum: New to Ubuntu
---

### Post by FlamingFish on 2011-02-06
Hi,
I have Windows 7 installed on my laptop (Acer Aspire) HDD. 
If I were to install Ubuntu Netbook Remix to a SD Card from a LiveCD, would the boot loader on the HDD be affected in anyway, or would the boot loader only be written to the SD Card?

Thanks.

---

### Post by fabricator4 on 2011-02-06
> **FlamingFish said:**
> Hi,
I have Windows 7 installed on my laptop (Acer Aspire) HDD. 
If I were to install Ubuntu Netbook Remix to a SD Card from a LiveCD, would the boot loader on the HDD be affected in anyway, or would the boot loader only be written to the SD Card?

Thanks.

No it won't.  Specify the install partition manually. Make sure you select the SD card to work on. I like to use ext2 file system since it takes less space than ext4.  Also make a small swap file.  An 8 GB SD card is a good size as it leaves plenty of room, but a 4GB card will work.

If it makes it easier, you can set up the ext2 partition and the swap partition using Gparted off the live CD before you start the install.

If the SD card is (for example) sdb, then make sure you specify that the grub bootloader is to go on sdb1.  You'll also have to make sure that sdb1 mounts as root ("/") otherwise you'll get an error.

Now, when you boot off the SD you'll get the bootloader which will ask if you want to boot the Ubuntu kernal or the Windoze 7.  It will have Ubuntu as the timed default.

Chris.

---

