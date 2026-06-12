---
title: "gparted help"
date: 2010-04-02
forum: New to Ubuntu
---

### Post by evilED on 2010-04-02
I just installed ubuntu 9.10 on my macbook to dual boot w/ Mac OS 10.5.  After getting my partitions set up I'm left with roughly 9 gbs of unallocated space.

Now, I want to allocate that space to my Mac partition, but gparted won't let me exceed the maximum space of said partition. (about 53 gbs) Is there anyway I can alter the maximum space of the Mac partition to incorporate this unallocated space?

I'm not really sure what I'm doing, its only my third day using ubuntu.:confused:

---

### Post by Chesamo on 2010-04-02
You can manage the size of your OSX partition (which I assume is HFS+) through the Disk Utility tool found in Applications > Utilities on OSX.

---

### Post by evilED on 2010-04-02
Disk Utility crashes when I try to go to the partition tab. It gives me an internal error that its lost the connection to the Disk Management Tool.

This is all new territory for me.   :-k

---

### Post by Chesamo on 2010-04-02
Interesting. AFAIK, HFS+ has no such restriction. What is the exact error that GParted gives you?

---

### Post by evilED on 2010-04-02
Gparted doesn't give me any errors.  It just won't allow me to increase the size of my HFS+ partition, only decrease it (thus increasing the unallocated space, which is the opposite of what I'm trying to do..)

---

### Post by Chesamo on 2010-04-02
Right-click the partition and hit "Resize/Move". Make the two Free Space boxes 0 and see what happens. If you can't, try to just keep hitting the up arrow on the Partition Size box.

---

### Post by evilED on 2010-04-02
ok, I've been trying this.  When I put 0 in the Following Free space, the Proceeding free space jumps to 9 gb, and vice versa.  I can't click on the up arrow because its grey.  All it will let me do is move the partition or decrease its size, not increase it because its already at the designated Maximum space.  Can I increase the maximum space of the HFS+ somehow?

---

### Post by srs5694 on 2010-04-02
It's possible you're missing some packages in Ubuntu. Try this at a Linux command prompt (Terminal, Konsole, xterm, or text-mode login):

```

sudo apt-get install hfsplus hfsprogs

```

This will install some HFS+-related software, if it's not already installed. I can't guarantee that this will fix the problem, but it might.

There may be some ways to temporarily or permanently adjust the partition table to get Disk Utility in OS X to work with the disk. My hunch is that it's getting confused by the Linux partition type codes. To advise you further on this course of action, though, I'll need to know more about your partitions. Before going further, though, you should say whether you're using a PowerPC system or an Intel system. I know less about what might be happening with PowerPC systems. To provide the necessary information on Intel systems, do this:


[list=1]
[*]Download and install my [GPT fdisk](http://sourceforge.net/projects/gptfdisk/files/). (You can install the OS X or Linux version; for the latter, download the .deb file for your architecture.)
[*]Type "sudo gdisk -l /dev/sda" and show the output here. (Change "/dev/sda" to "/dev/disk0" if you use the OS X version of GPT fdisk.)
[*]In Linux, type "sudo fdisk -lu /dev/sda" and show the output here. (OS X also has an fdisk command that provides similar information, but its details differ.)
[/list]

---

### Post by evilED on 2010-04-02
Sorry it took me so long to get back, my dogs suddenly got into a fight and had to be seperated. Anyway, I'm running an Intel macbook. 

I ran gparted from my liveboot cd and took some snapshots:

SDA2 is the one I want to expand.  but see the Maximum size? And the grey UP arrow for the New Size?  I have a feeling I'm missing something very simple here.  Dragging the arrow won't work either, it doesn't go anywhere.

---

### Post by evilED on 2010-04-02
OK, here's what I got


Found valid GPT with hybrid MBR; using GPT.
Disk /dev/disk0: 156301488 sectors, 74.5 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): 599BF68F-CF03-43FE-95D2-1A040FE74641
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 156301454
Partitions will be aligned on 1-sector boundaries
Total free space is 18999502 sectors (9.1 GiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1              40          409639   200.0 MiB   EF00  EFI System Partition
   2          409640       113393703   53.9 GiB    AF00  Untitled
   4       132393200       132395153   977.0 KiB   EF02  
   5       132395154       155193982   10.9 GiB    0700  
   6       155193983       156301454   540.8 MiB   8200

---

### Post by evilED on 2010-04-02
maybe this is easier to read

---

### Post by egalvan on 2010-04-02
In the gparted window, click on the top-left tab (called Gparted)

then click on "Show Features"

This will pop up a matrix showing what file systems and what operations are supported.

---

### Post by srs5694 on 2010-04-02
Have you tried installing the packages I recommended? If not, please do so. Also, your partition table is set up with a hybrid MBR, which I believe is unnecessary in this case (although if you're using Apple's Boot Camp, I don't know how it might interact with Linux and partition requirements). It may be possible to get Disk Utility to work if you convert the disk to a straight GPT configuration by using the 'n' option on gdisk's experts' menu, but I think it's safer to try to get HFS+ resizing support working by installing those packages. If you do attempt to modify your partitions, I *strongly* recommend that you create a backup of your current partition table via the 'b' option on gdisk's main menu before you do anything else.

---

