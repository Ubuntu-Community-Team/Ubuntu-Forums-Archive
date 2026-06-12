---
title: "Dual boot advice needed"
date: 2009-10-15
forum: New to Ubuntu
---

### Post by barcelonic on 2009-10-15
Im thinking of getting a dual boo so that i have Vista and Ubuntu. But i have some questions to make sure this is the right decision and i cant seem to find the info online...
 
A) if i install Vista to C: and Ubuntu to D: (i have two built-in hdds), does that mean i can't save Linux files to C: and i cant save Windows files to D: ??
 
B) Are there any drawbacks I should know about to using a dual boot?
 
C) Does Ubuntu require anti-virus software, and will I need to install anti-virus software on Vista before I use Vista for the first time, or will Vista only be at risk when Im using it?

Thanks in advance!  :)

---

### Post by ubuntakias on 2009-10-15
A)When you are in ubuntu you can load and save files from/to your windows D: partition directly and when using windows you have to install something extra to do it.I think the best idea is to make a new partition for your data, so you'll have vista partition,ubuntu partition and data partition.
B)I can't think of any drawbacks.
C)No antivirus for ubuntu.Everything you normally use for Vista.

---

### Post by 5nak3 on 2009-10-15
Well I'll try and help, although I'm by no means an expert.

A) I honestly don't know about this as I have only one hard drive which I have partitioned.

B) Drawbacks, well if you had only one hdd, I'd say you'd be splitting the hdd up and thus losing some free space. But as you have two different drives the only problem i would say is that you can't share files between the two systems. 

I mean on a single hdd, Linux will happily read the windows partition and so you can open up files, save to the windows the partition etc.
But windows will not read the linux partition. There are programs that should allow this but I've not managed to get them to work.

With a dual hdd I'm not sure how this will work.

Other drawbacks are that linux will take some time to get used to, and will no doubt need some tinkering, installing certain files to run media such as .avi or .mp3. It will take a lot of reading and paitence to learn, do not just expect to get into the linux OS and have everything as you did on your windows partition.

C) While ubuntu does not necessarily need a virus scanner, it is still advisable to exercise caution when using a computer. There is a very good topic on ubuntu safety which is worth a read. I'm short of time and so will not be able to dig up the link at the moment. But it is on these forums. 

When I get back home, I'll try and update the answer as I'll have more time.

Hope this is at last a start.

---

### Post by barcelonic on 2009-10-15
> **ubuntakias said:**
> A)When you are in ubuntu you can load and save files from/to your windows D: partition directly and when using windows you have to install something extra to do it.I think the best idea is to make a new partition for your data, so you'll have vista partition,ubuntu partition and data partition.
B)I can't think of any drawbacks.
C)No antivirus for ubuntu.Everything you normally use for Vista.

so how do u suggest i do the partitions - i have two physical drives with 75Gb on each.
i'll be saving downloads onto my externall HDD anyway so i'll really only need the space for software instalations.

will vista use the free space on the ubuntu partition as virtual memory??

---

### Post by vipulkelkar on 2009-10-15
Hi 
I havent used vista-ubuntu dual boot...I have xp and ubuntu on my PC..
I'll share whatever i can..

You can access ntfs formatted drive from ubuntu
So make an ntfs drive so that u can access the data in it from both,ubuntu and win

Anti virus is not necessary for ubuntu,still u can install one

---

### Post by barcelonic on 2009-10-15
So say I download an MKV or AVI file on Ubuntu and store it on the Ubuntu partition and play it on Ubuntu, if I then decide to move it over to Windows it won't move?

How about if I move it to my external HDD (NTFS) and then copy it to the Windows partition from there?

---

### Post by mapes12 on 2009-10-15
[http://members.iinet.net.au/~herman546/index.html](http://members.iinet.net.au/~herman546/index.html)

---

### Post by vipulkelkar on 2009-10-15
yes,it'll work when u put it in a ntfs drive from ubuntu and play it in windows..but i have a single hdd..

---

### Post by ubuntakias on 2009-10-15
25-30GB would be enough for ubuntu, so use the rest as your data partition.
Choosing NTFS filesystem for your data partition will make it accessible from both of your OSs (Vista and Ubuntu).You can make partitions during installation or by using GParted or any other software you are familiar with.
No,vista will not use free space on ubuntu partition as virtual memory.

---

### Post by barcelonic on 2009-10-15
> **ubuntakias said:**
> 25-30GB would be enough for ubuntu, so use the rest as your data partition.
Choosing NTFS filesystem for your data partition will make it accessible from both of your OSs (Vista and Ubuntu).You can make partitions during installation or by using GParted or any other software you are familiar with.
No,vista will not use free space on ubuntu partition as virtual memory.

So 30Gb will be enough for Ubuntu PLUS all the Linux software I'll be getting? Or just the Ubuntu installation itself? 

This is the part Im not too sure about. I won't be needing to store much data because I'll be using my NTFS external HDD. But I want to make sure I've got plenty of space for software installations on each partition, especially the Ubuntu one.

Could I, for example, use 60Gb on D: as Ubuntu partition, 50Gb on C: as Vista partition and have the remaining space from BOTH drives be classed as ONE partition (NTFS) for data??

Edit:  Also, I use a wireless N router for my 50Mb broadband, but I've heard there aren't many Linux drivers for N adapters - is this true? Should I be worried?? This is an urgent question as there is no point in me installing Ubuntu at all if I cannot access the internet at the speed I pay for.

Thanks

---

### Post by The Cog on 2009-10-15
I would guess that 10G is enough for Ubuntu and a normal set of system software. You also need for your /home directory (equivalent to My Documents on Windows) to live on a Linux filesystem. You could create a separate partition to share data, but I don't think it's worth the effort. Ubuntu can read/write a Windows partition, and with the right driver installed Windows can read/write a Ubuntu partition. I don't see a need for a "shared" partition.

I would advise just telling the installed to use the entire disk - just make sure you tell it to use the right disk! Back up your data first.

The installer will replace the bootloader on C: with GRUB which will ask you which OS you want to boot. Just remember that this bootloader relies on configuration files stored on on the Ubuntu partition so you would need to replace GRUB before ever removing or wiping the second drive.

---

### Post by tpjk on 2009-10-15
[x]("http://linux.oneandoneis2.org/LNW.htm")> **barcelonic said:**
> So 30Gb will be enough for Ubuntu PLUS all the Linux software I'll be getting? Or just the Ubuntu installation itself?

YES 30 GB will be enough for ubuntu and all kinds of additional software. remember, linux is not windows: [http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm) :]

on my hd the ubuntu installation and all additional programs only take up about 8 or 9 GB of space, and that includes programming tools such as netbeans (which at around 2 GB is probably the "heaviest" of all the apps i use).

---

### Post by barcelonic on 2009-10-15
So I think i'll not bother with a shared partition.

One more thing though, about that wireless issue i edited into my last post, is that going to be a problem for me?

Edit: I think i found drivers for my machine but I don't know if they are definitely compatible. Can someone pls tell me?
It says: "[FONT=Arial][SIZE=2]The information and software provided here are for Linux systems with Kernels 2.6.18 or greater with the mac80211 stack support."
How do I know if my machine meets those specs? I have an Acer Aspire 7730.
Source: [http://downloadcenter.intel.com/Detail_Desc.aspx?agr=Y&ProductID=2753&DwnldID=10315](http://downloadcenter.intel.com/Detail_Desc.aspx?agr=Y&ProductID=2753&DwnldID=10315)
[/SIZE][/FONT]

---

### Post by ubuntakias on 2009-10-15
The ubuntu installation takes approximately 2GB,you'll have plenty of free space for additional software.You can then arrange your partitions as you wish.

The best practice is to boot from a live cd and check if you can connect to the internet.I'm quite sure that it would be fine but try it!Burn a cd,put it in your pc and it will guide you...

---

### Post by zkriesse on 2009-10-15
For DualBoot help go here. [http://gwos.org/udsf/doku.php/core:dualbooting:ubuntu](http://gwos.org/udsf/doku.php/core:dualbooting:ubuntu)

---

