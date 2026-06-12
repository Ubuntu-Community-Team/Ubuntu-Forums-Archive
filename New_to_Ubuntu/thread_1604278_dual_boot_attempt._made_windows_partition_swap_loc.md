---
title: "dual boot attempt. made windows partition swap location. crap."
date: 2010-10-23
forum: New to Ubuntu
---

### Post by bolezhinkov on 2010-10-23
I just installed 10.10 on a small 7gb partition of the lone hard drive in my laptop.

I selected the only other partition (about 280gb, which had windows 7 64-bit installed as the OS) as the location for the ubuntu swap file. 

I am unable to select windows 7 as an option in GRUB when I boot the computer. I am unable to see the partition of the hard drive (NTFS format) that has my windows files on it, while using the file browser in ubuntu.

I have updated GRUBS. when I check to see, there is not a menu entry listed for windows 7. just ubuntu, ubuntu safe mode and two memory checks - I can't dual boot to windows 7 now. 

Has creating the swap location to be c: (where windows was installed) created this mistake?

thanks in advance!!

---

### Post by mister_playboy on 2010-10-23
> **bolezhinkov said:**
> Has creating the swap location to be c: (where windows was installed) created this mistake?

Yes, it did.  When it asked you if the partition should be formatted and you said yes, you destroyed your Windows install.

---

### Post by bolezhinkov on 2010-10-23
ruh roh. 

I didn't have the format box selected during the ubuntu installation from the usb key and it seems to have installed way too quickly to format the 280gb partition to be swap . . . 

right now the computer only sees the 8 gigabytes that I partitioned for ubuntu originally, no mention of the other 280 that should be kicking around somewhere. 

would the  original c: partition in NTFS not even show up in the file system if it was all swap?

---

### Post by mister_playboy on 2010-10-23
I have no idea if NTFS can be used as swap in Ubuntu, I just assumed you were prompted to format it to something else.  This quick formatting does not take very long, so the fact it happened quickly doesn't mean it wasn't formatted.  If Ubuntu isn't showing that partition in Nautilus as another drive, that seems to confirm it has been labeled as swap.  

It's certainly possible that the most of the data may still be on that partition, but I have no idea how you would fix it to be usable again.

What output do you get from running this in the terminal: ```
sudo fdisk -l
```

---

### Post by scratchysaurus on 2010-10-23
I did this 2 nights back. I believe we're both shafted and need to learn to accept our idiocy

---

### Post by mister_playboy on 2010-10-23
The ironic thing is that you may have little need for a swap partition in the first place.  Computers with 2GiB or more of RAM can get by quite well without any swap.

---

### Post by Quackers on 2010-10-23
I don't know how successful it may be but you could try testdisk which is available in the Synaptic Package Manager.

---

### Post by Sef on 2010-10-24
> I don't know how successful it may be but you could try testdisk which is available in the Synaptic Package Manager

TestDisk can recover lost partitions. You can download it from the repositories or from the [TestDisk site]("http://www.cgsecurity.org/wiki/TestDisk").

---

### Post by ArgusVision on 2010-10-24
My condolences to you on your situation. Best case scenario, you might be able to recover some data. I would definatly try TestDisk. If that doesn't do it, You might also try going back to Gparted and changing the label from swap to /windows. Leaving the 'format' box unchecked. I kinda' doubt that will work either because, if that partition was actually used as swap, the file allocation table (or the ntfs equvilent) was likely overwritten making accessing the files from the file manager improbable. You might have to resort to a file "carving" software... but hopefully you backed up your data recently...

---

### Post by Gone fishing on 2010-10-24
If you've formated the ntfs partition as swap (rather than formatted to Ext4 and over written it with Ubuntu). I think you may be able to get everything back.

Download on a different box! Parted magic you may be able to recover the ntfs partition with Test Disk. I recently hosed an ntfs partition when installing PCBSD (it over wrote the ntfs partition) and recovered all my data using Test Disk

Have a look at:

[http://ubuntuforums.org/showthread.php?t=1517401&highlight=Testdisk](http://ubuntuforums.org/showthread.php?t=1517401&highlight=Testdisk)

---

### Post by anewguy on 2010-10-24
> **mister_playboy said:**
> The ironic thing is that you may have little need for a swap partition in the first place.  Computers with 2GiB or more of RAM can get by quite well without any swap.

Laptop = may want to hibernate (yeah, I know that's always been a hit or miss with ubuntu).  Want to hibernate?  Need swap.

Dave

---

