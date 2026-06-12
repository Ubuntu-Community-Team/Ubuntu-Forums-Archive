---
title: "No root file system is defined"
date: 2011-02-14
forum: New to Ubuntu
---

### Post by Oathanvil on 2011-02-14
[FONT=Verdana]I am a new user to Ubuntu I think my last attempt was back in around 2008 on UBUNTU ver 10.4. I am a Windows tech that needs to learn Ubuntu for my own peace of mind and credentials.[/FONT]
 
[FONT=Verdana]I just copied my ISO download version of Ubuntu 10.10 to DVD using Imgburn great program I just used that yesterday to create my MSDN Full version of Windows7 Ultimate 64 bit version, and install that to a new RAID0 on 1 Tera of drive space.[/FONT]
 
[FONT=Verdana]First thing I did being a Windows user was to shrink 1024x10 = 102400 of drive space so I had a 100 gig partition to install Ubuntu 10.10 to in dual boot mode.[/FONT]
 
[FONT=Verdana]I got along fine it never asked me for raid drivers at that point I started to get worried and shortly after it would not let me install to the 100 gig partition I created.[/FONT]
 
[FONT=Verdana]ERROR CODE: No root file system is defined[/FONT]
 
[FONT=Verdana]Being a new user from windows I presumed this to mean it has no raid driver to build on or possibly no Drive letter to work with or both.[/FONT]
 
[FONT=Verdana]I read forums all day long and have the perception that I need now a drive root C:\ and in Ubuntu that is a backslash to signify C so a "\" and also intrigued I read on to find that it also likes to have a second partition for what is called Home? I can only make a guess that this is not root C: or "\" but where my active files might later be used in a swap file space? I forget the identifier required for the home partition.[/FONT]
 
[FONT=Verdana]So since I failed so terribly even following the Ubuntu installation instructions to the letter.... I decided to back off being a tech and use the .exe right from the DVD at the Windows7 desktop and there you go.[/FONT]
[FONT=Verdana]I get a dual boot option to boot to Windows7 or Ubuntu I was very elated I could no w get into playing with the new operating system and code.[/FONT]
[FONT=Verdana]Well BOO guess what it starts to load the Ubuntu UI or desktop and halts on the same message "No root file system is defined"[/FONT]
 
[FONT=Verdana]Ok so I know I am seriously ranting on here not my intension I would really like to step on board with everyone and start to learn the application.[/FONT]
 
[FONT=Verdana]Sort a of 2008 to 2011 wish not yet resolved as I cant get the OS to load into any of the two different desktop systems I have had during that time. One was a high end Vista capable motherboard chipset also a RAID0 in Vista 32 bit or x86. [/FONT]
[FONT=Verdana]The second Motherboard is a crosshair IV motherboard with a AMD 6 core Phenom II and 8 gig of Corsair 1600MHz bench tested ram, on the 1 Terabyte RAID0 array.[/FONT]
 
[FONT=Verdana]I will post my screen shots from digital camera only to give you guys something to look at even if I understand you have seen all this before.[/FONT]
 
Sorry they should be in order if they are not you can sort that out.
Any help at all please!
 
[FONT=Verdana][ATTACH]183490[/ATTACH][/FONT]
 
[FONT=Verdana][ATTACH]183491[/ATTACH][/FONT]
 
[FONT=Verdana][ATTACH]183492[/ATTACH][/FONT]
 
[FONT=Verdana][ATTACH]183493[/ATTACH][/FONT]
 
[FONT=Verdana][ATTACH]183494[/ATTACH][/FONT]

---

### Post by grahammechanical on 2011-02-14
You have not set a mount point. Forget Windows drive letters. We are talking partitions. When you install you can use the partitioner to create partitions and then format them to the file system of your choice. You can tell the program where to install the Ubuntu OS but you have to set a mount point.

The mount point should be /      It is called root in Linux.

I assume that you are installing into the 107.4GB unallocated space. Yes? In my opinion you should convert that into two partitions. A 20GB partition that you give a mount point of /    And the rest which you use for your data. You give that a mount point of /home. You select the file system as you have done. It should be either ext3 or ext4. You can tick to format. Make sure that you do not tick to format the other partitions. You will lose everything on those partitions.

The installation process will put the Ubuntu OS into the / partition and set up the /home partition as your home folder where your user settings and data are kept. The installer program will also create a swap partition for you. You will need to set a size for that and a mount point of /swap.

Then the boot loader will know to look in the / partition for the Linux OS. It is a file called vmlinuz-2.6.35-25-generic. You will find it in Places>Filesystem>Boot. The version numbers change as the OS is updated. You will notice that the 20GB drive/partition is called File System and the 100Gb or so drive/partition is called Home Folder. 

Linux does things differently. You have to mount things in order to access them. This is why Linux is more secure. 

You will get the hang of things. I have. Ubuntu takes most of the effort out of it all.

Regards.

---

### Post by Oathanvil on 2011-02-14
OK! thank you for that I will try to do those things listed and be back to let you know how that works out.
 
Aye I will not go near the ntfs files system's.
 
If I dont post back in a day or so oop's

---

### Post by Oathanvil on 2011-02-14
[SIZE=2]RESOLVED![/SIZE]
 
[SIZE=2]THANK YOU grahmmechanical I did as you said had to think a little on the fly here.[/SIZE]
 
[FONT=Verdana]I created of course the 100 gig partition in Windows7 then booted to the Ubuntu dvd and created the / root drive then so as not to mess up the partitioning I created the /swap as 2x my installed hardware ram on hunch so 16 gig or 1024x16. that leaves the remaining respectable drive size of just under 80 gig for the /home partition.[/FONT]
 
[FONT=Verdana]It booted right to the desktop and I had it set to install updates and third party plugins so again thank you.[/FONT]
 
[FONT=Verdana]New verdaform city here we come! new life form created by the Enterprises ships computer and needed a little guidance from Data to get there ;)[/FONT]

---

