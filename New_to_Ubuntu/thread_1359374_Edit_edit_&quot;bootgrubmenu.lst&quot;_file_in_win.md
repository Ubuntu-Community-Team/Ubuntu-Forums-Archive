---
title: "Edit edit &quot;/boot/grub/menu.lst&quot; file in windows xp"
date: 2009-12-19
forum: New to Ubuntu
---

### Post by aabmas on 2009-12-19
At first, I had my keyboard connected to a ps/2 port so it worked upon startup.  That port broke in addition to my original usbs, so now it's connected through a PCI usb card.  The problem is that it doesn't work on startup, so I can't choose between windows or Ubuntu when GRUB asks me to choose an OS.  Before the ps/2 port broke, I set up my "/boot/grub/menu.lst" file to load windows at the top of the list.  Since I can't choose anything but windows, I can't even start Ubuntu.  Windows doesn't even see the Linux Ext 3 partition let alone access files in it.  Please help me change the OS order!!!


                                                                       Please Help!!, aabmas

---

### Post by drs305 on 2009-12-19
One way to access linux files is to install the freeware app  *ext2fs* in Windows. It will allow you to read ext2/3 partitions from within Windows.

[http://www.fs-driver.org/]("http://www.fs-driver.org/")

Added: aabmas reported in post #6 that he had more luck with Ext2 Fsd found at [http://www.ext2fsd.com/?page_id=25]("http://www.ext2fsd.com/?page_id=25")that

---

### Post by Jerry N on 2009-12-19
Have you tried booting from your original Ubuntu Live CD and editting menu.lst from there?  Or download the latest version of Puppy Linux and boot from it.  You could download the gadget that allows Windows to see an Ext3 partition but I have never tried it and don't remember its name offhand.

Jerry

---

### Post by aabmas on 2009-12-19
> **drs305 said:**
> One way to access linux files is to install the freeware app  *ext2fs* in Windows. It will allow you to read ext2/3 partitions from within Windows.

[http://www.fs-driver.org/](http://www.fs-driver.org/)


Okay.  I downloaded and installed it.  Window's now recognizes the partition but it wants me to format it.  The troubleshooting page on the website said to run the program "mountdiag.exe" which I got from the website.  It's diagnosis is that the program didn't mount the drive because the file system has an inode size unequal to 128 bytes (it's inode size is 256 bytes).  I think I basically understand what it's saying there, but then it goes on to say that: 

     "the only way to solve it is to back up the volume's files and format the file system: give the mkfs.ex3 utility the -I 128 switch.  Finally, restore all backed up files.  After that, the Ex2 IFS software should be able to able to access the volume."

I'm wondering, where is the mkfs.ex3 utility, and what is the "-I 128 switch?"  Also, how do I back it up if windows can't even see the volume?

---

### Post by Sidewinder1 on 2009-12-19
> **jerry n said:**
> have you tried booting from your original ubuntu live cd and editting menu.lst from there?  Or download the latest version of puppy linux and boot from it.  You could download the gadget that allows windows to see an ext3 partition but i have never tried it and don't remember its name offhand.

Jerry

+1

---

### Post by aabmas on 2009-12-19
Wow!  I downladed Ext2 Fsd and it worked flawlessly after a restart.  Thank you, aabmas

---

