---
title: "noob: install ubuntu to drive J?"
date: 2011-02-27
forum: New to Ubuntu
---

### Post by now0pen on 2011-02-27
I know a few basic troubleshooting (know how to search google for answers), but I am a total newbie with regards to ubuntu. My PC specs (I bought PC ~2008 )-- MS windows vista basic home edition; AMD athlon 64 processor 3600+; 1.0GB RAM; ATI Radeon 1250; 1TB external hard drive.

Here are the drives on my PC:

[IMG]http://img199.imageshack.us/img199/3047/mycomputerlm.jpg[/IMG]

I don't know what my drives H, G and H are for. Drive J is a 1TB external hard drive that I purchased a few months back. It connects to my PC via USB port at the back. (I have proprietary software in drive J that uses PostgresSQL that I use with my other poker software.)

I have tried installing ubuntu using WUBI over the weekend just to see how it goes, but found that too slow to use in the long term. I am now considering installing Dual boot vista and ubuntu on my PC. 

Here are my questions:

- I don't have a windows Vista recovery CD in case anything goes wrong. Can I go ahead and install ubuntu without one?
- when you say back up my files, does that mean I make copies of docs, pics, mp3, etc to a USB stick?
- can i install ubuntu on drive J? If so do I follow [this installation prodedure]("http://www.ubuntu.com/desktop/get-ubuntu/download") ([http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)) or something else?
- do I have to partition drive J beforehand or can i just go ahead with the installation process (wasn't there an option for this during install)?
- if i was able to install ubuntu on drive J (external hard drive), and I have a second PC, can I just connect the external hard drive on the second PC and run ubuntu? or do I have to do another dual boot install with the second PC?

Thanks for helping!

- jim

---

### Post by grahammechanical on 2011-02-27
Lots of questions. I would like to comment on some of them.

> I don't have a windows Vista recovery CD in case anything goes wrong. Can I go ahead and install ubuntu without one?

Answer: Of course you can. Make sure you do **not** tick Use the whole disc. That will most certainly wipe out your Windows installation.

> I don't know what my drives H, G and H are for. 

Do you have a Ubuntu Live CD? If so, load that up and see what it tells you about those drives. They are supposed to be removable drives. You should know what is plugged into your computer.

Other will be able to help with the other questions.

Regards.

Did you notice that Windows has partitioned your drive into two equal partitions. And also that DATA (D:) has less than one tenth of a Gigabyte used. What is it for? I do not know. I think that is where Windows stores information to do a Windows restore.

To install Ubuntu to this hard disc both of these partitions will need to be made smaller, to create space for Ubuntu.

> - when you say back up my files, does that mean I make copies of docs, pics, mp3, etc to a USB stick?

Answer: Yes. Anything that you do not want to lose.

---

### Post by seawolf167 on 2011-02-27
> **now0pen said:**
> I don't know what my drives H, G and H are for.

I'll guess that these are your smart card reader drives (this is normally how they show up in Win7) though without knowing more about your computer I could be wrong.

> **now0pen said:**
> I don't have a windows Vista recovery CD in case anything goes wrong. Can I go ahead and install ubuntu without one?

You can find Windows recovery disks [here]("http://neosmart.net/blog/2009/windows-7-system-repair-discs/").

> **now0pen said:**
> when you say back up my files, does that mean I make copies of docs, pics, mp3, etc to a USB stick?

Back up **everything **that you don't want to loose. Easiest way to do this IMO when installing a new OS is to simply clone your drive with [Clonezilla]("http://www.clonezilla.org").

> **now0pen said:**
> can i install ubuntu on drive J?

Yes, simply select the location during the install wizard, make sure you don't select to overwrite your Windows install (this is where having backups make you feel easier about what you're doing)

> **now0pen said:**
> do I have to partition drive J beforehand or can i just go ahead with the installation process (wasn't there an option for this during install)?

You will partition this during the initial installation.

> **now0pen said:**
> if i was able to install ubuntu on drive J (external hard drive), and I have a second PC, can I just connect the external hard drive on the second PC and run ubuntu?

Your second PC would have a bootloader (assuming its using Windows) that wouldn't know to point to the Ubuntu installation, thus you would not be able to use it on another computer without modifying the bootloader (i.e. installing GRUB2)

---

### Post by now0pen on 2011-02-27
Thanks for the reply guys--I appreciate it. I went ahead with the dual boot install but found myself facing a wall and chose to cancel.

When I ran install ubuntu, it came to a point where the program was asking me to partition the disk drives. Which one was it referring to, Drive C? This was the first (Guided) option.

I looked it up in ubuntu and found this-- [https://help.ubuntu.com/8.04/switching/installing-partitioning.html](https://help.ubuntu.com/8.04/switching/installing-partitioning.html)

....where it was telling me to select manually edit partition. I selected manual and the next window showed the following:
 device                  size            used
dev/sda1 ntfs       10478          6020
dev/sda2 ntfs       79924          40020
dev/sda3 ntfs       74636          3200

at this point, I didn't know what to do anymore and chose cancel.

I did not find the option to install to drive J? Is this coming after install has finished with the partition?

Thanks again.

- jim

> **seawolf167 said:**
> 
Yes, simply select the location during the install wizard, make sure you don't select to overwrite your Windows install (this is where having backups make you feel easier about what you're doing)

You will partition this during the initial installation.


---

### Post by now0pen on 2011-02-27
PS
I installed using live CD ubuntu 8.04.1LTS

---

### Post by Mark Phelps on 2011-02-27
You were right to cancel.  Not know for sure which partition to use is a sure-fire way to wipe out your data.

While it can be OK to use the Ubuntu installer to shrink a Data partition (NOT an OS partition!), it would actually be better if you used the Vista Disk Management utility to shrink the "D" drive to make room for Ubuntu.  

Don't format the new free space -- let the Ubuntu installer do that.

And, if you've never used Ubuntu on this PC before, it is ALWAYS the best course of action to run it in LiveCD mode (Try it, do not install it) to see how well it detects your hardware and installs the proper drivers.

---

### Post by seawolf167 on 2011-02-27
Aye, I'd use the Windows partition editor to resize any Windows partitions. 

If you boot into Ubuntu (i.e. the "Try Ubuntu" option), then open a terminal (Applications -> Accessories -> Terminal)

then run the following command (with your "J:" drive plugged in):

```
sudo fdisk -l
```

and post the output here, we can take a look at the hdd's plugged into your computer and how they are formatted then give you advice on how to proceed.

Another word - the LTS versions have support for 2 years, so you might want to look at using the 10.04 LTS version instead of the 8.04 version.

---

### Post by now0pen on 2011-02-27
> **Mark Phelps said:**
> You were right to cancel.  Not know for sure which partition to use is a sure-fire way to wipe out your data.

While it can be OK to use the Ubuntu installer to shrink a Data partition (NOT an OS partition!), it would actually be better if you used the Vista Disk Management utility to shrink the "D" drive to make room for Ubuntu.  

Don't format the new free space -- let the Ubuntu installer do that.

And, if you've never used Ubuntu on this PC before, it is ALWAYS the best course of action to run it in LiveCD mode (Try it, do not install it) to see how well it detects your hardware and installs the proper drivers.

Thnks for the quick reply Mark,

I ran liveCD to test drive ubuntu on my pc. Everything was perfect! This is why I decided to take the next step and install a dual boot.

I will use the vista disk management utility following this-- [https://help.ubuntu.com/community/DualBoot/WindowsFirst](https://help.ubuntu.com/community/DualBoot/WindowsFirst)

and maybe this--

[https://help.ubuntu.com/community/HowtoResizeWindowsPartitions](https://help.ubuntu.com/community/HowtoResizeWindowsPartitions)

I'll go ahead with partition first and if all goes well, proceed to ubuntu dual boot install. I'll post here how everything goes. 

Thank you!

---

### Post by lisati on 2011-02-27
> **now0pen said:**
> 
- I don't have a windows Vista recovery CD in case anything goes wrong. Can I go ahead and install ubuntu without one?

You don't actually *need* a set of recovery disks, but it's sometimes useful to have one.

If you're lucky, your copy of Windows 7 will have come with software to help you create a set of recovery disks for your machine. The copies of XP and Vista I have came with suitable software preinstalled, as did my mother-in-law's laptop running Windows 7.

---

### Post by now0pen on 2011-02-27
> **seawolf167 said:**
> Aye, I'd use the Windows partition editor to resize any Windows partitions. 

If you boot into Ubuntu (i.e. the "Try Ubuntu" option), then open a terminal (Applications -> Accessories -> Terminal)

then run the following command (with your "J:" drive plugged in):

```
sudo fdisk -l
```and post the output here, we can take a look at the hdd's plugged into your computer and how they are formatted then give you advice on how to proceed.

Another word - the LTS versions have support for 2 years, so you might want to look at using the 10.04 LTS version instead of the 8.04 version.

will do that. one moment pls.

---

### Post by Hakunka-Matata on 2011-02-27
Installing 10.04 LTS sounds like a good option.  If for some reason you choose to install Maverick (10.10) beware of a bug in the installer.  

Look at this [https://wiki.ubuntu.com/MaverickMeerkat/ReleaseNotes#Boot,%20installation,%20upgrade%20and%20post-install]("https://wiki.ubuntu.com/MaverickMeerkat/ReleaseNotes#Boot,%20installation,%20upgrade%20and%20post-install") link and pay special attention to the first bullet.  bug ([COLOR="Red"]655950[/COLOR])

---

### Post by now0pen on 2011-02-27
On liveCD, i clicked on applications, accessories, terminal typed in sudo fdisk -1 and got the following:

ubuntu@ubuntu:~$ sudo fdisk -1
fdisk: invalid option -- 1

Usage: fdisk [-b SSZ] [-u] DISK     Change partition table
       fdisk -l [-b SSZ] [-u] DISK  List partition table(s)
       fdisk -s PARTITION           Give partition size(s) in blocks
       fdisk -v                     Give fdisk version
Here DISK is something like /dev/hdb or /dev/sda
and PARTITION is something like /dev/hda7
-u: give Start and End in sector (instead of cylinder) units
-b 2048: (for certain MO disks) use 2048-byte sectors
ubuntu@ubuntu:~$ sudo fdisk-1
sudo: fdisk-1: command not found
ubuntu@ubuntu:~$ sudo fdisk 1

Unable to open 1
ubuntu@ubuntu:~$ 

------
I'm not sure if these are the info you are looking for. I thought I got an error message the first line and tried different commands.

Was this what you were looking for? Drive J was plugged in when I ran these.

---

### Post by Hakunka-Matata on 2011-02-27
The command is ```
sudo fdisk -l
```

that's lower case L , copying and pasting commands avoids typos. :)

---

### Post by now0pen on 2011-02-27
> **Hakunka-Matata said:**
> The command is ```
sudo fdisk -l
```that's lower case L , copying and pasting commands avoids typos. :)

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcb5f671e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1274    10233373+  27  Unknown
/dev/sda2   *        1275       10383    73168042+   6  FAT16
/dev/sda3           10384       19457    72886905    7  HPFS/NTFS

Disk /dev/sdb: 1000.2 GB, 1000202043392 bytes
255 heads, 63 sectors/track, 121600 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00261ddd

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      121601   976758784    7  HPFS/NTFS
ubuntu@ubuntu:~$ 
ubuntu@ubuntu:~$

---

### Post by now0pen on 2011-02-27
i hope i got that right this time. how do i go from here?

---

### Post by Hakunka-Matata on 2011-02-27
Yes, you got it right.  Your disk has no extra room available to create the partitions necessary to install Ubuntu OS into.  To understand this better try looking at your disk by using Ubuntu's "GParted Partition Editor".  "System > Administration > GParted.  Don't change anything yet, just look at the Graphic and you'll see where there is no free space available.  

You can shrink your windows partitions to create the free space necessary, you should do that through windows.  

That's the first thing to do.  

I include a thumbnail for reference of my systems hard drives, showing how GParted displays information.  I'm using 10.10 and the program is named "GParted Partition Editor", if you're using a 8.04 LiveCD, the program name is not identical, it might be named simply "Parted"

---

### Post by now0pen on 2011-02-27
> **Hakunka-Matata said:**
> Yes, you got it right.  Your disk has no extra room available to create the partitions necessary to install Ubuntu OS into.  To understand this better try looking at your disk by using Ubuntu's "GParted Partition Editor".  "System > Administration > GParted.  Don't change anything yet, just look at the Graphic and you'll see where there is no free space available.  

You can shrink your windows partitions to create the free space necessary, you should do that through windows.  

That's the first thing to do.  

I include a thumbnail for reference of my systems hard drives, showing how GParted displays information.  I'm using 10.10 and the program is named "GParted Partition Editor", if you're using a 8.04 LiveCD, the program name is not identical, it might be named simply "Parted"

I right clicked on MyComputer, Manage, DiskManagement
From there, I clicked on drive D, shrink volume
the numbers showed 50/50 (about 35K MB each) and I clicked ok.

Was this correct? What's next? If not, how do I undo that?

---

### Post by now0pen on 2011-02-27
also,

i tried downloading 10.10 to my usb stick, but when I reboot to run ubuntu, my pc didn't reboot from the usb stick. i went into bios to change boot sequence. first is cdrom. then next to boot from usb fdd.

since boot from that settings didn't work, i went in again and changed usb fdd to usb zip. that didn't work either. 

am i missing something here?

if i cannot boot from usb stick to install 10.10, i might have to run live CD and instal 8.04LTS. Will wait for feedback before doing anything.

I appreciate your help. Thank you very much!

- jim

---

### Post by Hakunka-Matata on 2011-02-27
Ok, you're doing fine.  There are several steps and it's late now, so I'm signing off.  I'll check back in tomorrow but you're on the right track.  If you have data you cannot afford to lose in your Windows partitions, think about backing that up first.  

You could just go to ubuntu.com/ and read a bit about what's involved in installing the system.  

You're doing the necessary things first, so you're already started.

---

### Post by now0pen on 2011-02-28
This message was posted from windows OS after ubuntu dual boot install.

Everything looks normal. Will log out and restart on ubuntu.

---

### Post by now0pen on 2011-02-28
This message posted from ubuntu OS. Everthing seems to be running A-OK. 

Next step for me is to upgrade ubuntu 8.04LTS to 10.10.

Thank you everyone for helping me with this process. I really appreciate your help!

---

### Post by Hakunka-Matata on 2011-02-28
Glad to see it went well.  I didn't notice your post #18 until just now.  That may be a blessing in disguise, not getting 10.10 LiveCD to boot.  Please read my post #11, go to the Link and read the first paragraph in the "Known Issues" section.  It will show up at the top of the page if you use the HyperLink.  Everything has gone well for you so far, so don't let 10.10s installer throw you a curve ball after you've done so well.

When you're done with this thread, please mark it Solved. [COLOR="Red"][SIZE="2"]_Thread Tools_[/SIZE][/COLOR] at the top, on Right Hand Side.

---

### Post by now0pen on 2011-02-28
Everything, including upgrade from 8.04LTS to 10.04LTS finished last night. With everyone's help in this forum, the installation process wasn't as hard as I thought it would be.

Thank you and have a nice day!

---

