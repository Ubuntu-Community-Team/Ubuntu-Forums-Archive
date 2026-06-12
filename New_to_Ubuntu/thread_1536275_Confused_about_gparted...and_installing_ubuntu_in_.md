---
title: "Confused about gparted...and installing ubuntu in general."
date: 2010-07-22
forum: New to Ubuntu
---

### Post by Sidster67 on 2010-07-22
Alright so im trying to install ubuntu, but i want my data from windows xp to come with me.  I understand that I should download gparted and put win xp in one partition and my data in another.  Right?  and then when i switch to ubuntu it will just use that data i believe.  But gparted has to run from a flash drive.  i dont understand this.  i have to reformat my flash drive?  will this render it obsolete for other things?  then i boot it like it is an OS?  its all so confusing.  im pretty new.  help would be much appreciated

---

### Post by Elfy on 2010-07-22
Assuming that you are using the livecd to install ubuntu - there is already a partition editor on there in the system admin menu - you don't need to have gparted as well.

Also if you want to dual boot then you will get the option at the partition stage of the installer to deal with them then - you can resize the windows partition from that - do not pick Use Whole Drive - doing that will remove windows.

I think it is the "Install them side by side" option.

When you are in the livecd you can access the forum from firefox - also you can get to an irc help channel - if there's anyone in there - using the link in my sig.

[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

---

### Post by cjv8888 on 2010-07-22
[This]("http://www.psychocats.net/ubuntu/index") should tell you all you need to know to install.

---

### Post by nothingspecial on 2010-07-22
First, if you are not sure what you are doing, make sure you have a backup of anything you don`t want to loose. If you press the wrong button then bamph! its gone.

Unplug any external drives that store backups or data and move them far away from the computer before you install.

You can use unetbootin to create a bootable live ubuntu installation disk

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

When you boot you will have to press escape or one on the F keys and select boot from usb, it should tell you which button on the screen

Once you have installed ubuntu, you can reformat the usb stick and use it for whatever you like

---

### Post by Elfy on 2010-07-22
> **cjv8888 said:**
> [This]("http://www.psychocats.net/ubuntu/index") should tell you all you need to know to install.

Except that the dual boot page now refers to wubi and not a normal dual boot - which is what the OP is after.

---

### Post by Sidster67 on 2010-07-22
ok i understand that if i just download ubuntu i will be able to edit the partitions a bit within the installation wizard.  

but say for example, (this may not be exactly what i want to do at fist, but eventually), i want to just install ubuntu right over top of windows.  wouldnt all of my files be gone!  and even with a backup, i still want to try to just transfer the files if i can.

and i dont think that the partition editor in the wizard gives you this much control, but from what ive read if you make a partition for your os, and a separate partition for your files, program files etc, than you could have 100 different operating systems on different partitions and they could all use the files out of that one partition.

maybe im just confused, but i want to check, because it seems like useful knowledge.

also thanks for all your help, i didnt know posting on forums was this incredibly fast or useful:D

---

### Post by Elfy on 2010-07-22
It really depends what it is you want to do as to how you need to go about it. The livecd has 2 ways to do the partitions 

1 - if you start the installer there is a section for partitioning - you can do a few things here - overwrite any existing partitions, resize existing partitions and then install to the new space, install to existing free space and install using manual options

2 - a partition editor, gparted, seperate from the installer.

It really depends on what you want to accomplish as to how you go about it.

---

### Post by Sidster67 on 2010-07-22
okay, that makes sense, and so would that work then, could i have that separate partition for data and then maybe dual boot ubuntu and windows for now and they would both be able to access that other data partiton?

and also im not sure how to download g parted.  ive read that it comes with a package of tools along with partimage and a couple others.  but then when i go to the gparted website.  it calls it a live cd, but i dont have a cd drive, just usb.  and i dont quite understand how a live cd works when it is a program rather than an OS.  Does it run like a separate OS when i boot it, or does it still run inside windows or whatever OS i could be using?

---

### Post by techunit on 2010-07-22
I have created a repository of Video Tutorials Covering Partitioning and Installing Ubuntu... While they may not fit your situation perfectly they may be worth a look... My signature has a link to my site.. once there you should find a dropdown for Install Ubuntu with tutorials covering most of the steps!... You probably should look at my video on [partitioning]("http://ubuntuvideotutorials.wordpress.com/install-ubuntu/guide-to-partitioning/") . The videos I have made don't yet cover installing multiple Operating systems.

---

### Post by The Cog on 2010-07-22
> **Sidster67 said:**
> okay, that makes sense, and so would that work then, could i have that separate partition for data and then maybe dual boot ubuntu and windows for now and they would both be able to access that other data partiton?
Exactly. This is probably the best way to go for now.
> and also im not sure how to download g parted.  ive read that it comes with a package of tools along with partimage and a couple others.  but then when i go to the gparted website.  it calls it a live cd, but i dont have a cd drive, just usb.  and i dont quite understand how a live cd works when it is a program rather than an OS.  Does it run like a separate OS when i boot it, or does it still run inside windows or whatever OS i could be using?
This excellent site has a section describing how to create a bootable USB stick, but for some reason it doesn't say how to install dual boot any more.

But just to explain about the live CD and bootable USB stick:
The live CD is bootable, just like a windows installer CD is. Except that the live CD boots up a complete Linux, running from the CD instead of running from hard disk. This complete Linux system allows you to do a bit of "try before you buy" hardware compatibility testing. It also has the gparted utility (Menu System->Administration->gparted). It also has an installer program (icon on the desktop) that can install Linux to your hard disk. The installer should give you the option of reducing the size of your windows partition to make room for the extra Linux partitions. You probably want to use this option.

BACK UP YOUR DATA FIRST!
Apart from a remote possibility of a software error scrambling your disk, there is a somewhat larger possibility of you making a mistake, or misunderstanding the installer and clicking the wrong thing. Especially since you are not familiar with partitioning.

That said, good luck and come back with more questions if you are unsure. We like to see new users here, and like to be able to help.

---

### Post by ezsit on 2010-07-22
This is how I would proceed in your shoes.

1. Backup all my files to an external hard drive, formatted NTFS. Once complete, unplug and put in a safe place.

2. Use the Ubuntu Desktop Live CD and boot the computer. Run the Live CD mode. When the desktop loads, test your sound, internet connection, any other devices you want to work and make sure everything works.

3. Go to the Admin menu and select Disk Partitioner or Gparted. Run the Disk Partiotioner (Gparted) and select from the Disk menu to write a new MBR (master boot record). You will be prompted for a type and the default (msdos type) is what you want. This will erase all partitions and wipe your drive. Make sure you have backed up your stuff first. Close Gparted and reboot.

4. When you take the Ubuntu CD out of the tray, place the Windows install DVD in (I assume you are using Windows 7). Run the Windows installer and when you partition the hard drive, create a single primary partition for Windows about 20GB in size. Leave the rest of the hard drive as unpartitioned space.

5. Once Windows is finished installing, reboot to make sure Windows installed correctly. Place the Ubuntu CD back in the tray and reboot. Let the Ubuntu CD boot into the live desktop and double click on the installer.

6. Once you get to the partitioning stage, choose Manual Partitioning and partition the drive as such:
   sda1   Windows   20GB   NTFS
   sda5   Linux     20GB   EXT4    /
   sda6   Linux     20GB   EXT4    /home
   sda7   SWAP       2GB   SWAP
   sda8   Windows   Remainder of drive


sda1 is the partition that you created with Windows during that installation.

sda5 is the first logical partition to create with the Ubuntu installer. 20GB is plenty for / (also called the root partition).

sda6 is your Ubuntu /home is the next partition to create and contains your user files and settings. 20GB should be enough and the /home partition must be a Linux filesystem.

sda7 is your SWAP space that needs to be created and used by Linux for virtual memory. 2GB should be plenty. However, if you are running a laptop and you want suspend and hibernate to work faster, set the SWAP space to 1.5 times your physical memory.

sda8 is the remainder of your drive and could be either FAT32 or NTFS. If you wish to use NTFS, I believe you need to format the partition with Windows. You may create the partition with the Ubuntu installer, however, before you can use the partition you may need to boot back into Windows after you are finished installing Ubuntu and format the partition as NTFS. Be careful to choose the correct partition! If in doubt, pick the largest partition located at the end of the drive.

Hope this helps.

---

### Post by Sidster67 on 2010-07-22
ok thanks that all makes a lot of sense.

so for backing up my files what would you recommend, clonezilla seems good. but then partimage comes in the systemrescuecd package along with gparted, which i will need if i want to actually install ubuntu which i believe i will.  

and so your saying that any program that is a live cd can be done with a flash drive? and it doesnt need to be reformatted or anything in order to boot from it?

---

### Post by Sidster67 on 2010-07-22
that last post of mine was directed at the cog, just to clarify...

but okay, this is what im thinking of doing, and i dont have an installation disk for windows just a hidden partition which contains an image of my hard drive at factory settings that i can boot from.

anyway i think im going to:

1. Back up my My Documents files onto an external drive.
2. Put the live cd onto a flash drive.
3. Boot the live cd in a virtual machine, and then use partedit to create an image of the hard drive, and store that on an external hard drive.
4. Use Gparted to create a partition for Windows, a partition for Ubuntu, a swap space for Ubuntu, and all my data that windows and ubuntu can both use.
5. Then eventually perhaps delete the windows partition.

---

### Post by ezsit on 2010-07-22
Were you directing your questions at me? If so:

1. for backup of my existing files I always use ZIP and copy the zip files to an external drive. Assuming you have Winzip or some similar compression program, go to My Documents folder and right-click to compress each folder containing my files. Go to the Local Settings folder, find the Mozilla folder, and compress the Mail folder from Thunderbird, copy the abook.mab file for addresses, and the bookmarks.html file for bookmarks. Then I copy all those files to and external hard drive. That is my backup routine.

2. I don't use flash media for booting OSes. I use live CD/DVD.

---

### Post by techunit on 2010-07-22
If you couldn't find the video on partitioning it is available [here]("http://ubuntuvideotutorials.wordpress.com/install-ubuntu/guide-to-partitioning/") it covers the basics of creating and removing resizing and creating more than four partitions... as for dualbooting you shouldn't have to much trouble because you are using windows XP and not Vista Or 7... XP doesn't break when partitioned with gparted.

---

### Post by The Cog on 2010-07-22
> **Sidster67 said:**
> ok thanks that all makes a lot of sense.

so for backing up my files what would you recommend, clonezilla seems good. but then partimage comes in the systemrescuecd package along with gparted, which i will need if i want to actually install ubuntu which i believe i will.  
No. I would just copy all the data to the backup drive. The reason for that is I'm not sure (no familiarity) that clonezilla can restore data to a different sized partition. Just copying the data files is something I understand, although I know I would lose all my apps and settings if I needed to restore. If you're sure that clonezilla can restore after you've tinkered with the partition table then fine, use that. > and so your saying that any program that is a live cd can be done with a flash drive? and it doesnt need to be reformatted or anything in order to boot from it?
I forgot to mention that. You can make a bootable flash stick (at least 1 Gig) and make it behave like a CD. Boot the whole OS from the stick. Actually, you can use some of the flash space to store changes too - something you can't do with a CD. I prefer booting flash to CD because it's so much faster.

---

### Post by The Cog on 2010-07-22
Nice post #11 from ezsit. 

One snippet missing from the partition plan: You need to make an "extended" partition to put all the logical partitions into. An extended partition acts as a container for all the logical pertitions. This would probably be sda2 in the above plan, and would occupy the whole disk apart from the bit sda1 occupies.

---

### Post by Sidster67 on 2010-07-22
so alright... my flash drive is only 512MB.

can i run it from the same external hard drive that my backup is on? or would that kind of wreck my ext. HD for anything else because it will need to be reformated in order to boot from it i believe.

and also, since gparted and other programs are run from a live cd, how can i have more than one running at the same time.  Once it run it can i save it to my hard drive and use it like a regular program?

---

### Post by nothingspecial on 2010-07-22
If you make a live usb stick, you don`t need a live cd.

They are the same thing. You can run gparted from either.

Aslong as you back up anything you don`t want to lose, and remove it from the computer before you start, then whatever happens, you can fix it.

If you only have stuff on the drive you want to install on and nowhere else, you may erase it.

The point is - BACK UP YOUR STUFF AND HAVE A GO -  if you do it wrong then{I,we,they,us} will help you fix it.

---

### Post by Sidster67 on 2010-07-22
yeah, i cant wait to start trying it, but there are still a couple things im not sure about.  first of all, when i boot from a flash drive, do i have to download infrarecorder or imgburn or anything like that as well as the systemrecuecd package or is there something that can do that in the sr package.

---

### Post by Sidster67 on 2010-07-22
and also, when i download a program that boots from a cd.  do i have to boot from that cd every single time i want to use it? because that seems like it would be really annoying

---

### Post by The Cog on 2010-07-22
Don't even think about installing Linux on your backup drive.

To install a live flash stick, it must be at least 1G. It puts the entire CD contents on the stick of course, and 512k wouldn't be big enough.

---

### Post by techunit on 2010-07-22
Here please look at these videos so you can get a feeling for how to install Ubuntu...

Actual Install (non-dual-boot) [here]("http://ubuntuvideotutorials.wordpress.com/install-ubuntu/tutorials/")

Create bootable flashdrive [here]("http://ubuntuvideotutorials.wordpress.com/category/utilities-2/bootable-flashdrive/") need 1gb at least recommended 2gb for persistant

Installing Ubuntu To A External HD [Here]("http://www.pendrivelinux.com/move-wubi-to-a-usb-flash-drive/") concerns moving a wubi install to a Harddrive only way I have gotten it to work.

partitioning in ubuntu [here]("http://ubuntuvideotutorials.wordpress.com/install-ubuntu/guide-to-partitioning/")

You should really do some home work on Ubuntu as it is generally a replacement for Windows... I hope these help... If you need more help ask away we aren't going to stop helping people...

What I think you should try first is creating a persistant bootable USB drive so your going to need a 5-dollar 2gb USB drive.

---

### Post by Sidster67 on 2010-07-22
yeah i have watched all of the videos you have linked so far, and i do feel like i am getting closer

but as you said i really want to make sure that ive done all my homework before i just try it.

im not really in that much of a rush anyways.  my main goal by installing ubuntu is just to learn more about computers anyway.  and ive already learned a ton in a matter of days!

im going to buy a better flash drive soon(probably tommorow) just so i can start doing some of this, and then hopefully it will lead somewhere.  im still not sure about how the livecd works(yes, even with the video, sadly)  but it seems that many programs on linux are installed this way, including linux itself.  although linux is just booted from the cd, and then can be written to the hard drive.

is this the same with all programs like this...and if so.  why? i guess it gives you that option to try before you buy.  is that it?

---

### Post by techunit on 2010-07-22
what are your computer  perhaps you can install ubuntu in a Virtual machine... it is a great way to try practically any OS and It is quite simple...

Another video... you can probably find the video pretty easily...

---

### Post by The Cog on 2010-07-23
> **Sidster67 said:**
> im still not sure about how the livecd works(yes, even with the video, sadly)  but it seems that many programs on linux are installed this way, including linux itself.  although linux is just booted from the cd, and then can be written to the hard drive.

is this the same with all programs like this...and if so.  why? i guess it gives you that option to try before you buy.  is that it?

Programs are installed in what way? By live CD? If that's what you're thinking, it's wrong. A live CD is just a CD that boots an operating system, much like you would normally boot an OS from a hard disk. A windows installer is a kind of live CD - it runs a cut-down version of windows that automatically runs the windows installer program. Same for the DOS installer CD. The difference with Linux live CDs is that they load to a normal user interface rather than launching a restricted installer program, which means you can do other things like try the OS out, or try to repair problems with the OS on your hard disk.

Once Ubuntu is installed to the hard disk, you will find that installing software is a little different to with windows. With windows you have to hunt round the internet for installers for whatever you want and pray that it isn't infected with malware. With Ubuntu and other Linux's, they provide repositories a bit like a smartphone app store, where you can download thousands of programs from a trusted source. Searching the internet for downloadable software should be the very last resort with Linux, not the first thing you try. In fact because Linux has software repositories you can download from, very little linux software is available on the general internet on the form of downloadable binaries. The writers generally only publish the source code, and assume that the repository maintainers will compile the program into the repositories for the users to download. It works very well but is totally alien to windows users unless they have a smart phone with an app store.

---

### Post by Sidster67 on 2010-07-28
are you sure? because right now i want to install systemrescuecd, which is a program. (in preparation for installing ubuntu)

but if you go to the site, all it has is the option of a livecd (you do have the option of using a flash drive), and it is an .iso image file.  and it specifically says in the instructions that i will have to make sure that my flash drive is first in the list for booting in the BIOS, and other instructions on booting from it, etc, etc.

So what is the deal with this?  it is a program but yet it runs it as a livecd, does it not?

---

### Post by Elfy on 2010-07-28
Yes - systemrescue runs from cd or usb - it's not a 'program' as such but a sort of 'OS' - this is the list of packages it includes [http://www.sysresccd.org/Detailed-packages-list](http://www.sysresccd.org/Detailed-packages-list)

I think you are possibly getting a bit confused and making more out of it than is necessary.

Once you have installed your OS to the HDD - then that is where it runs from.

---

### Post by Sidster67 on 2010-07-28
well i wanted do download systemrescuecd on windows before i did ubuntu.  are you saying it's impossible?  because i'd really rather do the image first, and just so i could experiment with the whole livecd thing.

but are you saying i would *half* tp install ubuntu and run it through there?  

and when you say run it like an os, do you mean i will be able to just run the program alone and i dont need an os running

---

### Post by Elfy on 2010-07-28
systemrescuecd is a sys admin livecd tool

This thread is moving beyond installing ubuntu and gparted.

If you want other information start other threads.

---

### Post by The Cog on 2010-07-28
When you make a system rescue CD, you are making a bootable CD. You can do this with either windows or linux - how you make the CD doesn't really matter. 

Once you have the system rescue CD (or equivalent USB stick), this is what you boot. You don't use another OS to run the system rescue CD, you boot from it. The CD contains an OS (probably a flavour of Linux) and a collection of utility programs like disk imaging programs, file recovery programs etc. The OS and the programs are all on the CD in the same way as windows, word and notepad are on your hard disk right now.

The same is true of the Ubuntu desktop CD. It contains both a Linux OS that it boots, and a collection of programs that the OS can run for you. These programs include a partitioner, file explorer and importantly, an installer that can install Ubuntu on the hard disk for you. You can run the desktop live CD even if you don't have any hard disks - it's all there on the CD.

---

### Post by Sidster67 on 2010-07-28
wow that was a great answer.  that covered a lot of my questions

so now i believe i know what to do.  ive copied the sytemrescuecd files onto the flash drive.

but when i try to boot from it the boot fails.

i tried to reformat my flash drive through the command prompt, but my flash drive doesnt show up in the disk partitioner.  though it does show up in my computer as removable storage, and also in disk management.

im not sure what the reason for this is...it's like it just groups my flash drive in with my hard drive which i expect it does.

ive heard the term, attached and unnattached with this.  is there a way i can separate my flash drive from my hard drive?

---

### Post by oldos2er on 2010-07-28
There's a program you need to run to make the flash drive bootable. See [http://www.sysresccd.org/Sysresccd-manual-en_How_to_install_SystemRescueCd_on_an_USB-stick#B.29_Recommended_USB_installation_method_from_Windows](http://www.sysresccd.org/Sysresccd-manual-en_How_to_install_SystemRescueCd_on_an_USB-stick#B.29_Recommended_USB_installation_method_from_Windows)

---

### Post by Sidster67 on 2010-07-31
thats exactly what i used.

ive got all of the files on the flash drive, and then ive gone to the BIOS settings, changes my flash drive to first in line and it just fails.

so what is wrong here

---

### Post by oldos2er on 2010-07-31
Can you check the flash drive on another computer?

---

### Post by Sidster67 on 2010-07-31
no not really..hmm

well what is supposed to happen?  maybe im just not waiting long enough.  like i looked it up on youtube and it took quite awhile, but it did say it failed.

or is there something else im missing?

---

### Post by oldos2er on 2010-07-31
If it says failed, I think you waited long enough. I just thought you could test the flash drive on another computer to see if it's working properly.

What are your system's specs?

---

### Post by Sidster67 on 2010-07-31
well like a 140 GB hard drive

i think 34 bit processor

i dont really know how im supposed to figure out my specs lol

---

### Post by oldos2er on 2010-07-31
What make/model is your computer? Once we know that, we can google for the specs. Or maybe there's something in XP you can use to give that information? I'm mainly interested in CPU, RAM, video device, IDE or SATA.

---

### Post by -kg- on 2010-08-01
You could also use [Unetbootin]("http://unetbootin.sourceforge.net/").  They have a Windows version.

One thing though...I tried several times using it to download the .iso's (the default setting) and couldn't get it to work.  The second selection (Diskimage) works fine, though.  Just download the .iso(s) you want to use and use Unetbootin to write them to the flash drive.  Makes it bootable every time with a minimum of effort.

---

### Post by Sidster67 on 2010-08-01
well my computer is a dell inspiron mini 10.

and i used a device similar to unetbootin, but specifically for systemrescue, and its supposed to be the best choice for it.

---

### Post by -kg- on 2010-08-02
Hey, if it works, use it.  I'm giving you an alternative that will work with pretty much any .iso you throw at it.  It has 41 distros listed in it's default list alone (including SystemRescue), and will work with many more.  They have a version for Windows, as well.

Like I said, though, I had problems using Unetbootin's default list (I think it has to do with bad downloads).  You're completely safe if you download the .iso yourself, check the checksum, then use the downloaded .iso to create the bootable USB flash drive.  That method worked every time.

I currently have the newest Linux Mint on it, but I think I'm going to end up with the full Knoppix Live DVD (3.6 GB).

---

### Post by oldos2er on 2010-08-02
> **Sidster67 said:**
> my computer is a dell inspiron mini 10.


Those specs look ok to run Ubuntu, although some Intel video chipsets may be problematic.

---

### Post by Sidster67 on 2010-08-02
I've been looking into Grub.

It looks as though this might be what I'm missing.

Is Grub or some multiboot loader completely necessary?

---

### Post by -kg- on 2010-08-03
> Is Grub or some multiboot loader completely necessary?

Yes.  Even if you are only using Windows, Windows has its own boot loader in the MBR of the primary drive.  In the more modern (NT-based) Windows OSes (up to XP and W2003 Server...starting with Vista, this was changed), this is called "ntldr".  GRUB or any other compatible boot loader will work as well, as long as it will detect the OS(es) you have loaded on the drive.

When a computer boots up, it first goes through BIOS posting operations, and after the posting is done (detection of installed hardware, etc.), it looks to the first sector of the primary hard drive for further booting information.  This is called the MBR (Master Boot Record) which contains the partition table for the drive (limited to 4 Primary partitions due to the space assigned it...64 Bytes) and, if one or more partitions are bootable, the boot loader program.

The boot loader in the MBR will continue the booting process handed off to it by BIOS.  Depending on which OS installed the boot loader into the MBR, it will point to the partition containing the subsequent boot up files for further information and further boot instructions.  If you have more than one OS installed, it will be pointed to the appropriate partition for the OS you have selected.

Here is a good description of the various Linux boot loaders and how they operate:

[http://www.xs4all.nl/~lennartb/bootloaders/node1.html]("http://www.xs4all.nl/~lennartb/bootloaders/node1.html")

---

