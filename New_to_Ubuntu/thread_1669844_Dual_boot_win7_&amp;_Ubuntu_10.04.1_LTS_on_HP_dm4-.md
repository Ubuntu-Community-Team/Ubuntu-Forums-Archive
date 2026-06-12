---
title: "Dual boot win7 &amp; Ubuntu 10.04.1 LTS on HP dm4-1160us"
date: 2011-01-18
forum: New to Ubuntu
---

### Post by rj98942 on 2011-01-18
I have searched the forums and found alot of problems that ubuntu seems to have with the wireless and touchpad on the hp's. i found a post dealing with the fact that HP likes to ship their PC's with the 4 maximum partitions already in use. but now i have a question that is very basic. when i'm installing and i get to the screen where i choose where i want Ubuntu to be installed i only get 2 options. the first is to wipe the hard drive completely and install ubuntu and kill windows 7. the second is the advanced tab. under the advanced tab i can see all 4 partitions. i can select the partition that i want to install it on. but as soon as i try to proceed, it says something about that partition not being selected as a boot partition. i know this is probably very tedious and such but if someone has a chance and the knowledge, i would appreciate all the help i could get with this. i have another computer that is connected to the internet so i could use a messenger like msn or yahoo for chatting if someone has the time for a "live session" if you will. thank you for your time and efforts in advance.

ryan

---

### Post by smurphy_it on 2011-01-18
You should run gparted, and post a screenshot in here so we can see exactly what you are talking about.

in a terminal fdisk -l or sudo fdisk -l would help too.

---

### Post by Mark Phelps on 2011-01-18
> **rj98942 said:**
> ... i can see all 4 partitions...
This is the maximum number of Primary partitions you can have.  So, the partitioner can not create any more partitions for Ubuntu.

If you install in this manner, you will be installing INSIDE MS Windows (known as Wubi) -- which I don't recommend.

But, unless you want to delete one of your existing partitions, you have no other choice.

Also, since you're running Win7, first thing you should do is run the Backup feature and select the option to create an burn a Win7 Repair CD.  IF you do install Ubuntu in dual-boot mode, you may need to use that CD to restore/repair the Win7 Boot Loader.

---

### Post by Jerry N on 2011-01-18
Better follow Mark's advice and create those backup DVDs because it sounds like you are about to make a mess of your machine.  You can't just arbitrarily select a partition and install Ubuntu in it.  You are going to have to delete some partition, probably the HP tools partition, and then make 40GB or so of space by using Win 7's built in partition tools to shrink the main Windows partition.  You then used gparted to create an extended partition in the newly found space and divide the extended partition into logical partitions as required for your Ubuntu install, ie a swap partition and the required "/" partition.  

I haven't tried this yet so good luck!

Jerry

Slight correction:  I have installed Ubuntu 10.04 on an older HP laptop that only had 3 of the partitions used up and I did this after cloning the 80GB hard drive onto a new 320GB hard drive.  I haven't gotten up the nerve to delete the HP tools partition on my HP Mini 210 yet.  I am waiting to see how this works out for someone else:)

---

### Post by rj98942 on 2011-01-18
smurphy_it: 

I typed this out by hand so that's why it's not showing up quite right i think. if it's not clear enough, let me know how to copy and paste the output into here so it shows up correctly. thanks.

sudo fdisk-l says:

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
Disk identifier: 0x522b6e86 

   Device Boot                  Start               End            Blocks             Id             System
/dev/sda1    *                           1                26            203776            7             HPFS/NTFS
partition 1 does not end on a cylinder boundary.
/dev/sda2                             26               28859      231603200+       7            HPFS/NTFS
/dev/sda3                        28859           60789         256472063+       7           HPFS/NTFS
/dev/sda4                       60789             60802            105496           c           W95 FAT32 (LBA)



Mark Phelps: thank you for the advice. before i started any of this process, i did a full backup and created a restore dvd. i did get carried away however and used /dev/sda3 which was the hp recovery as my new dedicated Ubuntu partition. so with that, i wiped the recovery part (figuring that i have my backups and recovery dvd). i cut my c drive (/dev/sda2) in half so windows and Ubuntu both get roughly the same amount of playing space. to combat the windows bootloader problem which i have had before on a previously failed attempt with another computer, after cutting down the size of /dev/sda2 with the windows partition tool thing, i rebooted into windows a couple times. the first time it had to do a checkdisk and after that, it boots up just fine in windows so hopefully that issue wont come up. 

Jerry N: I hope i dont make a mess of this machine but if i do, it's brand new so i have nothing on it as far as data goes. i'm actually kind of glad that i can be a guinea pig for you and hopefully alot of other people who were turned off by the idea of dual booting win7 and ubuntu 10.04 on an HP dm4. 


I hope i have provided some decent info and i hope that the screen shot turns out so you can see it well. thanks for the help so far guys.

---

### Post by rj98942 on 2011-01-19
just trying to bring up my post. i know it's probably cheap but maybe i can get some additional eyes on in.

---

### Post by Quackers on 2011-01-19
What you appear to have done is just make sda2 smaller and sda3 bigger.
The important thing here is that you still have 4 primary partitions. You can't install Ubuntu to a Windows partition. You still need to delete a partition to make unallocated space for an extended partition to be created. In this extended partition you can have as many logical partitions as you wish.
I see you have labelled sda3 as "ubuntu", so I assume that is where you want to install Ubuntu. If that is the case you should backup any data in that partition then delete that partition using the Windows disk management screen.
That will leave you with 3 primary partitions and some unallocated space. You can then create an extended partition either with gparted on the Ubuntu live cd/usb or with the installer, as part of the installation procedure.

BTW, if you have shrunk your C: drive you should reboot into Windows a couple of times to see if it is happy (unless you defragmented C: first).

---

### Post by rj98942 on 2011-01-19
it posted too many times

---

### Post by rj98942 on 2011-01-19
.

---

### Post by rj98942 on 2011-01-19
Quackers: thank you. that was maybe the description that i need. 

Now for another question before i get too dedicated. i would like my HP dm4 to be able to use the sleep and hibernate features if at all possible. I have loaded another screenshot of GParted so now you guys can see what I am working with. The large unallocated space is what i would like to use for Ubuntu 10.04. Would it be possible to set up a space on my hard drive that both Windows 7 Home Premium and Ubuntu 10.04 LTS could access? Like a data storage place where I could keep my pictures and music? If it is possible with my current setup, that would be great. Thank you all again for your time and knowledge. 

I forgot to mention that i have been using Fedora 14 for the past couple months. I was never any good with it and I like the way Ubuntu "feels" but I am still very new to the Linux community.

---

### Post by rj98942 on 2011-01-19
.

---

### Post by rj98942 on 2011-01-19
just another BUMP

---

### Post by smurphy_it on 2011-01-21
Linux can read just about any file system, including ntfs.  You can save files in your C drive (ntfs) file system for windows 7.  Then just mount the drive in Ubuntu and access it.

As for power saving features like hibernation and what not, it "should" work out of the gate.  However, if you run into issues you should start posting in here the problems.  Make sure you include your hardware specs so people know what to work with.

---

### Post by oldfred on 2011-01-21
If dual booting you have to be careful of sleep/hibernate. If you write into a hibernated system, you will probably damage the system.

Much better with dual boot to create another NTFS partition for any data you want to share. You can easily read from the system partition but should not write into it unless you have to do repairs.

If you have used the 3 primary and created the 4th primary as extended then all the additional partitions will be logical inside the extended. Windows will read & write from a logical NTFS and Ubuntu will boot from logical partitions.

For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home:
1. 10-20 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext3(or ext4)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.

---

### Post by rj98942 on 2011-01-21
After tons of research I discovered some answers through google and official documents from both Ubuntu 10.04 and Windows 7 Home Premium. HP with all of their wisdom and such decided to use all 4 partitions that are allowed. On my HP dm4-1160us I took the liberty of deleting the HP TOOLS and HP RECOVERY (D drive) so I could have 2 actual partitions to work with. After deleting those partitions in Windows, I decreased the size of my C drive to give Ubuntu more room to play. I have a 500 Gb HD and let windows keep about 200 GB. I restarted Windows a couple of times. The first restart it had to do a run check disk. Every restart after that was normal. I then inserted my Live CD with Ubuntu 10.04 and went to GParted. With my remaining +/- 300GB I split that up a bit more. I wanted to use a shared "Data" drive that both Windows and Ubuntu could read and write. I made my "Data" drive about 200 GB because storage space is goodness. In GParted, I split up the drive so there was the remaining empty space before the Data drive that I was creating. From what I understand, this would put the two operating systems close together on the HD with allt the Data at the end of the drive. When I created the data drive, I formatted it to be NTFS and labled it using GParted. I then restarted back into Windows because I'm paranoid and don't wanna mess that up too bad. I then restarted back into my Ubuntu Live CD and started with the Install process. On step 4, where you decide where to put Ubuntu, I selected the one that uses the most continous free space. (I'm writing this out of memory if you couldn't tell). When I tried to move on to step 5, I did get a warning about not having any dedicated swap space. I'm gonna be honest with you. I don't let my notebook sleep or hibernate. It's either on and in use or its off. 

Then after all the install stuff finished up, I started with the updates. While the system was updating i went to System > Preferences > Mouse and then under the Touchpad Tab, I disabled Scrolling. I am now able to use the touchpad without problems. I can not click and hold with one finger while moving the object with the other finger though. Double click with the touchpad to "grab" the window or whatever and drag it to where you need it to go. Then drop it. I have yet to get the fingerprint reader to work. I'm not really worried about it either. 

So that was my experience with Dual Booting Windows 7 and Ubuntu 10.04 on a HP dm4-1160us.

---

### Post by gordintoronto on 2011-01-21
I'm disappointed that your research didn't find issue 41 of Full Circle Magazine...

---

### Post by rj98942 on 2011-01-21
Honestly gordonintoronto, I was not aware of the magazine Full Circle. I got tired of looking through all crap that Google came up with (+/- 385,000 when you search "dual booting windows 7 and ubuntu 10.04). I figured to follow the documentation of Ubuntu 10.04 and Windows 7 that I found.

---

