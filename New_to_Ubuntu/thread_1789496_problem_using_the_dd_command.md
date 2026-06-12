---
title: "problem using the dd command"
date: 2011-06-23
forum: New to Ubuntu
---

### Post by ClientAlive on 2011-06-23
Hi,

I'm running Ubuntu 10.04 LTS and want to create a raw file of my entire disk into a folder on my external hard drive. The external drive is 230 gig and the source/ local disk is roughly 36 gig.

I followed the code samples given at:

[http://www.brunolinux.com/02-The_Terminal/The_dd_command.html](http://www.brunolinux.com/02-The_Terminal/The_dd_command.html) (Heading: " Cloning an entire hard disk:")

And

[http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/](http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/) (" Cloning an entire hard disk:")

but modified the path after "of" to be the path to the folder on my external drive.

Below is the script I ran in the terminal:

```

dd if=/dev/hda of=/media/Lacie/Backup/HostClone/HostClone.img conv=notrunc,noerror

```

The above was copy/ pasted directly from the terminal

After pressing enter I get the following output:

```

dd: opening `/dev/hda': No such file or directory

```

Do I have to umount my local disk for this to work??! I can't see how that would possibly work since the o/s itself (and thus all the functionality of the system) is on that disk. If it were unmounted than how would you be able to do anything?

I really don't get this one guys. This would be my first time using the dd command and I know it can do a lot of damage if not used correctly. I feel I need to use this particular tool for the project I'm trying to do though. I know for certain it will work whereas I'm not so sure about other things.

Does anyone have any answers that might help me? Thanks in advance. I do appreciate it.
------------------

Edit:

By the way, this  [http://grantmcwilliams.com/tech/virtualization/virt-blog/184-convert-raw-disk-images-to-vdi-format](http://grantmcwilliams.com/tech/virtualization/virt-blog/184-convert-raw-disk-images-to-vdi-format)  page shows a dot before the first slash in the path after of but it the only code sample I've seen that does. Both the other links above do not have it and I consider linuxquestions to be pretty definitive and trust what they say. Could the guy with the dot be right? Don't feel like wiping out my hard drive tonight to find out.

Thanks

---

### Post by linuxman94 on 2011-06-23
Your drive is probably sda.  just to be sure can you post the result of ```
sudo fdisk -l
```

That goes in terminal by the way.  Applications -> Accessories -> Terminal

---

### Post by ClientAlive on 2011-06-23
> **linuxman94 said:**
> Your drive is probably sda.  just to be sure can you post the result of ```
sudo fdisk -l
```

That goes in terminal by the way.  Applications -> Accessories -> Terminal



```

Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0006d301

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4659    37419008   83  Linux
/dev/sda2            4659        4864     1648641    5  Extended
/dev/sda5            4659        4864     1648640   82  Linux swap / Solaris

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0002c61c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       30401   244196001   83  Linux

```

Cool!! I didn't know that told you all this!

So I'm guessing it should be:

```

dd if=/dev/sda of=/media/Lacie/Backup/HostClone/HostClone.img conv=notrunc,noerror

```

??

Seem right? Not gonna fry my ^$$ by runnin' that?

Thanks

---

### Post by ClientAlive on 2011-06-23
By the way, and I know this isn't what the orig post was about; but, is there any way to take that raw image I get from this and eliminate the free space from it yet leave the rest untouched?

Zerofree?

Any ideas? I'm new to this and just want to finally get this project right.
------------------

Edit:

By the way, how do I set the block size also?

would it be to include:

```

bs=512

```

??

And where in the line of code would I put that??

Thanks again.

Thanks a whole bunch!:D

---

### Post by linuxman94 on 2011-06-23
dd copies all of the data, including free space, because it is not aware of partitions.

---

### Post by ClientAlive on 2011-06-23
Cool. It's cool, I have a workaround/ other way to go about it.

Did you happen to see my very last question in the edit of my last post?

Thanks man.

---

### Post by linuxman94 on 2011-06-23
It goes anywhere after the of=/path/here

so for you it would be:

```
dd if=/dev/sda of=/media/Lacie/Backup/HostClone/HostClone.img conv=notrunc,noerror bs=512
```

---

### Post by ClientAlive on 2011-06-23
> **linuxman94 said:**
> It goes anywhere after the of=/path/here

so for you it would be:

```
dd if=/dev/sda of=/media/Lacie/Backup/HostClone/HostClone.img conv=notrunc,noerror bs=512
```


Perfect! Thank you so much!

Peace out man!!

---

### Post by linuxman94 on 2011-06-23
No problem! Please mark your thread as solved using the thread tools menu so others can benefit.

---

### Post by ClientAlive on 2011-06-24
Worked like a charm! Took about 20 min but worked fantastic.

Good stuff fellas.

:popcorn:

---

