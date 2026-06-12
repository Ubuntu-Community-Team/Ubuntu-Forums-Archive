---
title: "Need help with removing a partition"
date: 2011-06-24
forum: New to Ubuntu
---

### Post by Aaron-Mosela on 2011-06-24
Hey everyone

I am very new to Ubuntu (and Linux for that matter) I have Ubuntu set as my default OS with windows 7 and Mint as options in GRUB I have had a go on Mint and Linux and have decided that Mint isn't for me.

I would like to run Fedora instead of Mint I have tried to install it in unallocated place of about 32GB but it keeps saying there is not enough space.

After trying all day I haven't be able to fix this. I have came to the conclusion that I need to remove Mint in order to run Fedora (Because there is a 4th option to test the machine) and I am pretty sure you can only have 4 partitions that run OS's or something along those lines. 

Is there a way to remove mint without effecting Windows 7 or Ubuntu (I have backed everything up but would rather not have to delete everything) and if there is a way could you provide a guide or link that gives the basis of what needs to be done that would very helpful.

---

### Post by idoitprone on 2011-06-24
post results of```
 fdisk -l
```

i believe disk utility can remove partitions

---

### Post by Aaron-Mosela on 2011-06-24
I have had no such luck with that method sadly.

---

### Post by idoitprone on 2011-06-24
can you please open the terminal and post the results of 

```
sudo fdisk -l
```

i want to know if you hit the 4 primary partition limit

---

### Post by LittleGyko on 2011-06-24
I am not an expert but I can say a few things from my experience. You  can have atmost 3 primary partitions and 1 extended partition. For  example you could have 2 primary partitions and 1 extended partition.  You can further partition the extended partition into partitions, called logical partitions. You cannot  do this with primary partitions. You can install windows only on a  primary partition, But linux can be installed on a logical partition also.

Please post the result of 
```

sudo fdisk -l

```

---

### Post by -kg- on 2011-06-24
What the above posters have said is true.  You can only have 4 primary partitions, one of which can be (but not necessarily ***MUST*** be) an Extended partition.  An Extended partition is a special type of Primary partition in which you can create many other partitions, called Logical partitions.

If, as I and others above suspect, you already have 4 Primary partitions, then yes...one must be deleted in order to be able to create an Extended partition.  On the other hand, if you already have an Extended partition with one or more partitions created within it, then you're good to go without deleting a Partition (unless you want to).

What will be required in that case is to determine where the free 32GB is located on your hard drive.  If there is an Extended partition and the free 32GB is outside it (i.e., in the Primary partition space), you will need to "move" it inside the Extended partition.  This is done by moving partitions (if necessary) until the free space is next to the Extended partition, then expanding the EP into that free space.  That will place the free space within the EP, allowing you to create as many new partitions as you need.

So, yes.....the output of "sudo fdisk -l" would certainly be helpful.  Also helpful to you would be to read at the link in my signature block.

---

### Post by Aaron-Mosela on 2011-06-24
here are my results.
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


However when I installed Ubuntu on the CD and ran it as a live CD then went into GParted and right clicked on the space I wished to delete then deleted it. This then worked. 

Thankyou very much for your advice and help

---

### Post by idoitprone on 2011-06-24
> **Aaron-Mosela said:**
> here are my results.
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


However when I installed Ubuntu on the CD and ran it as a live CD then went into GParted and right clicked on the space I wished to delete then deleted it. This then worked. 

Thankyou very much for your advice and help

thats an error. sorry i did not reply back soon enough. air gear ovas are awesome. i want a copy monster 

the last character on fdisk is a lowercase "L" not a 1
```
sudo fdisk -l

```

---

### Post by dFlyer on 2011-06-24
You can only have 4 primary partitions. You can have as many logical partitions you want, but a logical partition will use one of your primary partitions.

---

### Post by -kg- on 2011-06-24
> **dFlyer said:**
> You can only have 4 primary partitions. You can have as many logical partitions you want, but a logical partition will use one of your primary partitions.

Actually, the Extended partition will use one of your primary partitions, but I'm sure he understood that.

---

### Post by Aaron-Mosela on 2011-06-25
Oh dear haha Silly mistake but now I know its and l. 

it's all sorted now though. 

-KG- thank you very much for that link helped a lot. 

and thank you to everyone else

---

