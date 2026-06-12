---
title: "Boot From Inside Extended Partition?"
date: 2009-02-03
forum: New to Ubuntu
---

### Post by cfree220 on 2009-02-03
Hi, I was just wondering if it's possible to boot from a partition inside an extended partition. I'm setting up a Dell XPS M1530 in dual boot with a twist. It turns out that you can configure it such that the Dell Media Direct button boots an OS of your choosing. I had this up and working previously, however I had Ubuntu installed on a primary partition with the swap partition also primary. The result was that, while I was able to boot into either OS, I was not able to create a final partition to store user files.

Configuring the buttons is done with the Dell Media Direct CD. In an elevated command prompt:

```

X:\dellkit\rmbr.exe Y Z

```
Where X is the letter of the optical drive, Y is the number of the partition containing the OS you'd like to boot using the power button, and Z being the number of the partition to boot with the Media Direct button.

So, basically, I want to have my hard drive partitioning scheme to look something like this:

47MB Windows Boot Partition (Primary)

50GB Primary Partition for Windows (Previous installs show this to be about right for my needs)

16GB Extended Partition
     -8GB for OS
     -8GB Swap (I do hibernate)

~230GB Primary Partition for user files.

I've already screwed this up once, so any and all help would be appreciated!

Thanks in advance!
Chris

---

### Post by handydan918 on 2009-02-03
I don't know about this Dell utility, but GRUB can boot from any partition you can install an O/S to.

---

### Post by cfree220 on 2009-02-03
The way the configuration works is that GRUB stays on the same partition as Ubuntu, thereby allowing button boot w/o seeing the loader menu for either Windows or GRUB. How would I found out which partition number GRUB is on?

---

### Post by handydan918 on 2009-02-03
caljohnsmith seems to be the local boot genius, and has referred many people to a handy little script. You can download it and run it and it creates a text file that you can post back here with all kinds of useful partition information.

[script here.]("http://sourceforge.net/project/platformdownload.php?group_id=250055")

Then do ```
sudo bash ~/Desktop/boot_info_script*.sh
```

Someone should be able to get you sorted with that info.

---

### Post by cfree220 on 2009-02-03
Sounds good. I still have to reinstall Ubuntu, but after I do I'll take a look and post the output.

---

### Post by cfree220 on 2009-02-03
Actually.... it occurs to me that I won't have any way of running that script, as I won't be able to boot to Ubuntu until after I set up the Media Direct Button...

---

### Post by meierfra. on 2009-02-04
Couple of options:

1) Partition your drive as follows:

47MB Windows Boot Partition (Primary)
50GB Primary Partition for Windows 
8GB   Primary Partition for Ubuntu OS

~238 GB Extended Partition
  -8GB Swap
   ~230GB Logical Partition for user files.


2)  Use your partitioning scheme, but install Grub to the first  sector of the extended partition. Then use "X:\dellkit\rmbr.exe Y Z" with Z the number of your extended partition.


Let me know if you need more details.

---

