---
title: "Uninstalled Ubuntu Only Drive Can't install XP or Vista? How to install XP/Vista?"
date: 2011-06-02
forum: New to Ubuntu
---

### Post by flatlined on 2011-06-02
I had Ubuntu 11.04 only installed on my hard drive. I couldn't get XP or Vista installation disk to install so I ended up reformatting the whole drive in Ubuntu back to NTSF and went through installation again and it's still not working.

How do I delete Ubuntu off my drive and install XP or Vista?

Thanks

---

### Post by SavageWolf on 2011-06-02
If the whole disk is formatted, than there is no OS on it...

How is it "not working"? Are there any error messages or anything?

---

### Post by flatlined on 2011-06-02
> **SavageWolf said:**
> If the whole disk is formatted, than there is no OS on it...

How is it "not working"? Are there any error messages or anything?


When booting up I get the Grub error message.

XP install says it can't install and Vista's install doesn't see the drive.

Thanks

---

### Post by mikewhatever on 2011-06-02
Boot from the Ubuntu CD and post the output of the following command from a terminal window:
```
sudo fdisk -l
```

---

### Post by sanderj on 2011-06-02
> **flatlined said:**
> I had Ubuntu 11.04 only installed on my hard drive. I couldn't get XP or Vista installation disk to install so I ended up reformatting the whole drive in Ubuntu back to NTSF and went through installation again and it's still not working.

How do I delete Ubuntu off my drive and install XP or Vista?

Thanks

See Microsoft's answer on this question: [http://support.microsoft.com/kb/314458](http://support.microsoft.com/kb/314458)

---

### Post by flatlined on 2011-06-02
> **mikewhatever said:**
> Boot from the Ubuntu CD and post the output of the following command from a terminal window:
```
sudo fdisk -l
```


Usage:
 fdisk [options] <disk>    change partition table
 fdisk [options] -l <disk> list partition table(s)
 fdisk -s <partition>      give partition size(s) in blocks

Options:
 -b <size>                 sector size (512, 1024, 2048 or 4096)
 -c                        switch off DOS-compatible mode
 -h                        print help
 -u <size>                 give sizes in sectors instead of cylinders
 -v                        print version
 -C <number>               specify the number of cylinders
 -H <number>               specify the number of heads
 -S <number>               specify the number of sectors per track

---

### Post by pricetech on 2011-06-02
That's actually a lower case ell, not a one.

But best follow sanderj's advice and use the link in his post.

---

### Post by flatlined on 2011-06-02
> **pricetech said:**
> That's actually a lower case ell, not a one.

But best follow sanderj's advice and use the link in his post.

I can't get that to work either.

---

### Post by sanderj on 2011-06-02
> **flatlined said:**
> I can't get that to work either.


Why not?

---

### Post by flatlined on 2011-06-02
> **sanderj said:**
> Why not?

None of the commands worked

It says to enter the commands in Command Prompt Is the command prompt the Terminal?

---

### Post by sanderj on 2011-06-02
> **flatlined said:**
> None of the commands worked

It says to enter the commands in Command Prompt Is the command prompt the Terminal?

Yes, it is. But maybe the GUI-way is better for you: 

Live-boot the Ubuntu CD. Do not intstall, but choose "live run" / "test run". 
Once Ubuntu is running, choose: System -> Administration -> Disk Utility. Then, on the left hand side, choose your harddisk (probably only one). Then, on the right hand side, select the partition, and select "Delete Partition" in the right lower corner. Repeat that for all partitions on your harddisk.

That's it. Do *not* create a new partition. Reboot your computer into the Windows setup.

HTH

---

### Post by flatlined on 2011-06-02
> **sanderj said:**
> Yes, it is. But maybe the GUI-way is better for you: 

Live-boot the Ubuntu CD. Do not intstall, but choose "live run" / "test run". 
Once Ubuntu is running, choose: System -> Administration -> Disk Utility. Then, on the left hand side, choose your harddisk (probably only one). Then, on the right hand side, select the partition, and select "Delete Partition" in the right lower corner. Repeat that for all partitions on your harddisk.

That's it. Do *not* create a new partition. Reboot your computer into the Windows setup.

HTH


Cool Thanks I'll give that a try later and let you know. I have to go do some things.

---

