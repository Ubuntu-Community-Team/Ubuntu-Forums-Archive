---
title: "problems with ubuntu disk size"
date: 2010-03-23
forum: New to Ubuntu
---

### Post by liljon on 2010-03-23
Hi wonder if anyone can help me. 
I am new to Linux  and decided to have a dual on my system, Ubuntu and Sabayon. they both installed fine and it seemed that all was well. However I have just discovered that I had only allocated 2.2 Gb for Ubuntu during the partitioning process, and clearly this is n't enough as every time I try to install anything the system tells me there is no roon. i thought there might be a disk management utility in administration, however when I tried to open computer janitor I got this message

Failed to run computer-janitor-gtk as user root.

Unable to copy the user's Xauthorization file.

and when I tried to run software sources I got this message

Failed to run /usr/bin/software-properties-gtk as user root.

I realize that I have done something wrong, but can't work out what.

thank you 

LJ

---

### Post by srs5694 on 2010-03-23
Those errors are probably a result of the system running out of disk space. If you gave enough space to Sabayon, you may be able to use its tools to resize your Ubuntu partition; or you may need to use an emergency disc, such as an Ubuntu live CD or [Parted Magic.](http://partedmagic.com) In any event, GParted or a similar GUI tool is the easiest way to handle this task. The details of what you'll need to do depend on your exact layout, so if you need advice, you'll have to post more details. The output of "sudo fdisk -l" should be helpful, as should information on which partition(s) in your current setup do have free space that you'd be willing to give to Ubuntu.

---

### Post by liljon on 2010-03-23
When I was doing the second partition, for Ubuntu, I thought that I was giving over the rest of the hard drive space to Ubuntu which should have been around 29 Gb, but i must have messed something up. I ran the fdisk list and got the following output.

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xef24ef24

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *         192        6970    54452317+  83  Linux
/dev/sda2            6971        7296     2618595    5  Extended
/dev/sda3               1         191     1534176   82  Linux swap / Solaris
/dev/sda5            6971        7274     2441848+  83  Linux
/dev/sda6            7275        7296      176683+  82  Linux swap / Solaris

Partition table entries are not in disk order

I don't understand much of this output, hopefully it will make more sense to you 

thanks for your help

Lj

---

### Post by drs305 on 2010-03-23
Did you install Jaunty? This was a bug in Jaunty if the user chose "install side by side". I have only seen the problem with Windows, but perhaps it also affected your install. Of course, you may have ended up with a 2.2GB partition independent of this bug, but the solutions still apply.

I wrote a couple of guides about this. 

If the small partition was due to not moving the slider bar to the correct size, you can try another reinstall and move the slider during the partitioning process.
[HOWTO: 2.5 GB System Partition - What Went Wrong?]("http://ubuntuforums.org/showthread.php?p=7658271")


If the partition just ended up too small for other reasons,  you can resize the existing partitions (expanding Ubuntu by taking space from Windows).
[Expanding an Ubuntu System Partition]("http://ubuntuforums.org/showthread.php?t=1219270")

---

### Post by liljon on 2010-03-23
Thanks alot for all the help. It seems that this was the problem and I am going to re-install as a solution. As I am brand new to Linux I was wondering if there was any beginner's that either of you would recommend. After years of using Windows I am finding it difficult to navigate around the OS

---

### Post by drs305 on 2010-03-23
> **liljon said:**
> Thanks alot for all the help. It seems that this was the problem and I am going to re-install as a solution. As I am brand new to Linux I was wondering if there was any beginner's that either of you would recommend. After years of using Windows I am finding it difficult to navigate around the OS

I forgot to welcome you to Ubuntu and the Ubuntu forums. You will find good support and very helpful users here to ease your transition to Linux.

A good start is the free beginners guide, which you can download. It gives a very good overview of how linux and Ubuntu work. It is different than Windows but you will most likely learn to love it's flexibility.

Here is a link to the thread discussing the guide. It has the actual link to the download.
[Free Beginners Guide]("http://ubuntuforums.org/showthread.php?t=1052065")
This is a "sticky" in the Beginners Forum - so it's located at the top of the Beginners Forum main page.

---

### Post by srs5694 on 2010-03-23
It looks like you've given roughly 54GB of your drive space to /dev/sda1 -- that's presumably Sabayon. That leaves only about 4GB for everything else, including both Ubuntu and two swap partitions (you really need only one; two distributions can share a single swap partition). Your partitions are also out of sequence -- /dev/sda3 is at the start of the disk, followed by /dev/sda1 and then /dev/sda2 (which contains /dev/sda5 and /dev/sda6). This isn't an error, but it can be confusing.

If you haven't invested much time in configuring your system, you might find it easier to just wipe everything out and re-install it all. Recovering isn't all *that* hard, but you will need to boot an emergency disc and use GParted or a similar tool to shrink and move your partitions. This is always a bit risky, so if you have any important data on the computer, back it up first. You can then proceed:


[list=1]
[*]Boot an emergency disc, such as the PartedMagic I referenced in my previous post.
[*]If necessary, disable swap. You can do this by typing "swapoff -a" at a root shell prompt (the only type in PartedMagic). If swap is active, GParted may not let you do much of what you must do.
[*]Start GParted.
[*]Shrink /dev/sda1 (your Sabayon partition) to a reasonable size -- perhaps about half the disk.
[*]Expand your extended partition (/dev/sda2) to cover the space you've just cleared.
[*]Move and resize /dev/sda5 (your Ubuntu partition) to fill the cleared space.
[*](Optional) Delete /dev/sda6 (your ~175MB swap space). It's too small to be very useful, and its placement at the opposite side of the disk from your main swap space (/dev/sda3) will degrade performance.
[*]Select the option to apply your changes.
[*]Exit and reboot.
[/list]


It's conceivable that Ubuntu won't boot at this point, depending on how everything was set up, but chances are both it and Sabayon will boot. If you have problems booting either OS, post back. Such problems can be corrected.

Good luck!

---

### Post by liljon on 2010-03-23
Thanks again, and thanks for the welcome

I am not sure how mark my post as solved, but I pretty sure it is

Lj

---

### Post by drs305 on 2010-03-24
> **liljon said:**
> Thanks again, and thanks for the welcome

I am not sure how mark my post as solved, but I pretty sure it is

Lj

To mark it solved, go to the Thread Tools link at the top right of the first post. Click and, since you are the original poster, it will show an option to mark the thread solved. Once you have done so, you can return to the same link and remove the SOLVED tag if that should become necessary. Hopefully it won't!  ;-)

---

