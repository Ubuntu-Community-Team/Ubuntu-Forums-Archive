---
title: "Installation: Help with partitions"
date: 2010-12-28
forum: New to Ubuntu
---

### Post by Mooseeeeey on 2010-12-28
Hello, I'm a newb to Linux and higher computer community and am finally trying out Ubuntu.  I have it downloaded, burned, and get to installation but need help with the partitioning.  I currently have a 160GB hardrive with 3 partitions: 40GB for Windows Xp, 100GB for data, and a (currently) blank 20GB partition which is where I want to install Ubuntu(10.10) to.  I go through installation but when it gets to partitioning part I'm afraid I'll really mess something up so I'm asking for help.  What options do I use to install Linux onto the 20GB partition, and not make any changes to the drive?  Any help would be appreciated so I can learn and hopefully get into this.

---

### Post by seawolf167 on 2010-12-28
The easiest way is to simply select the option to "install side-by-side and choose which to boot upon startup" (the wording is close).

This automatically creates the ext partitions for home / and swap

If however, you want to create the partitions yourself, a place to start from for your first install would be something like

/ (root) - 10 GB
swap - 4GB (assuming 2GB ram)
/home - 6GB remainder

Note that 20 GB isn't a very large partition anymore (Ubuntu now recommends 10GB minimum I believe for the root partition)

Here is a link to the Dual Booting help section I suggest you read:
[URL="https://help.ubuntu.com/community/WindowsDualBoot"]
https://help.ubuntu.com/community/WindowsDualBoot[/URL]

---

### Post by TeoBigusGeekus on 2010-12-28
What I'd do with the 20GB:
Choose manual partitioning and select the 20GB partition. Right click it and select delete partition.

From these 20GB:

Create a new 1GB partition which you should use as swap (a sort of hard disk pseudo ram that helps real ram when things get tight).

Create a new 9GB partition, give ext4 as its file system and / as its mount point. This will be your root partition.

Create a new 10GB partiton with the remaining space, give ext4 again for file system and /home as the mount point. This will be your home partition, where all your setting will be stored. Whenever you want to upgrade ubuntu, you will use the same /home partition, thus keeping your settings in a new installation.

Finally, choose the 100GB partition and give as its mount point /media/DATA. Take care NOT to choose format the partition - you have been warned.

---

### Post by Mooseeeeey on 2010-12-28
Ok I'm reading through the link you gave me and backing up data now, but I have another question: What the /root and /swap and /home ?

---

### Post by TeoBigusGeekus on 2010-12-28
> **seawolf167 said:**
> The easiest way is to simply select the option to "install side-by-side and choose which to boot upon startup" (the wording is close).

This automatically creates the ext partitions for home / and swap

If however, you want to create the partitions yourself, a place to start from for your first install would be something like

/ (root) - 10 GB
swap - 4GB (assuming 2GB ram)
/home - 6GB remainder

Note that 20 GB isn't a very large partition anymore (Ubuntu now recommends 10GB minimum I believe for the root partition)

Here is a link to the Dual Booting help section I suggest you read:
[URL="https://help.ubuntu.com/community/WindowsDualBoot"]
https://help.ubuntu.com/community/WindowsDualBoot[/URL]

I wouldn't recommend the side by side installation in Maverick.
[http://ubuntuforums.org/showthread.php?t=1652807]("http://ubuntuforums.org/showthread.php?t=1652807")

---

### Post by Mooseeeeey on 2010-12-28
I thought that side-by-side installation made another partition.

---

### Post by TeoBigusGeekus on 2010-12-28
> **Mooseeeeey said:**
> I thought that side-by-side installation made another partition.
That's what laugh1 thought as well...

Go with the manual partition, just to be sure.

---

### Post by amjjawad on 2010-12-28
Hello and welcome :)

Kindly check my signature and have a look at the first and the second link.
The second link will answer lots of your questions and will help you to install Ubuntu without problems (hopefully).

---

### Post by theozzlives on 2010-12-28
> **Mooseeeeey said:**
> Ok I'm reading through the link you gave me and backing up data now, but I have another question: What the /root and /swap and /home ?

/ is the root directory that spawns all other directories and mount points. It also contains all your programs, OS and such (like the old DOS C:\).

/home is where your specific settings and files are (like Documents and Settings).

swap is a portion of your drive that uses your HD as RAM (like a Windows pagefile).

---

### Post by ezsit on 2010-12-28
You will need to delete the partition you set aside for Linux and let Ubuntu create the partition for you during installation. You should use manual partitioning to do this. If you try to install as it stands now, Ubuntu will see no available space since all space is currently partitioned. Available space should be left unpartitioned.

I would, during installation, delete your 20GB partition and create one 19GB partition and label it root / and one 1GB partition for SWAP.

---

### Post by Mooseeeeey on 2010-12-28
Ok so during installation I go to the last option (advanced one) delete 20GB partition, make 3 new ones with 10GB for root, 9GB for home, and 1GB for swap(I have 512MB RAM, is that enough?)

---

### Post by amjjawad on 2010-12-28
> **Mooseeeeey said:**
> Ok so during installation I go to the last option (advanced one) delete 20GB partition, make 3 new ones with 10GB for root, 9GB for home, and 1GB for swap(I have 512MB RAM, is that enough?)

You need to learn the basics of partitioning.
Making 3 partitions while you already have another 2 is NOT possible if the other 2 are Primary Partitions.
If one of them is Extended then there is no problem at all.

Edit: [https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

---

### Post by Mooseeeeey on 2010-12-28
Ok Im reading the partitioning basics article but whats a way of figuring out if they're primary or extended in Windows?

---

### Post by amjjawad on 2010-12-28
> **Mooseeeeey said:**
> Ok Im reading the partitioning basics article but whats a way of figuring out if they're primary or extended in Windows?

Disk Manager

Right Click on My Computer > Manage > Disk Manager

---

### Post by Mooseeeeey on 2010-12-28
Ok Im looking at it and It says this in the tables
Volume Type FileSystem Status
(C: ) Basic NTFS Healthy(System)
(D: ) Basic NTFS Healthy(Page File)
(D: ) Basic NTFS Healthy
I'm assuming basic is Primary. So can anyone give me a suggestion on what to do here?

---

### Post by amjjawad on 2010-12-28
> **Mooseeeeey said:**
> Ok Im looking at it and It says this in the tables
Volume Type FileSystem Status
(C: ) Basic NTFS Healthy(System)
(D: ) Basic NTFS Healthy(Page File)
(D: ) Basic NTFS Healthy
I'm assuming basic is Primary. So can anyone give me a suggestion on what to do here?

Check the colors. At the bottom of the Disc Manager.
Or
Post a clear Screenshot here.

---

### Post by Mooseeeeey on 2010-12-28
EDIT: Sorry didn't see key at bottom, C: is Primary and D: and E: are Logical, but have a green border that says it's extended.

---

### Post by amjjawad on 2010-12-28
> **Mooseeeeey said:**
> EDIT: Sorry didn't see key at bottom, C: is Primary and D: and E: are Logical.

Exactly.
That is what I want ;)

C and D are Primary. E is Logical which means it's inside the Extended Partition.
It means your Extended Partition is 20GB ONLY.

Inside that partition (Extended), you need to create 2 Partitions.
/ (root)
swap

Or

/ (root)
/home
swap

It's up to you.

Read more from that link I posted and refer to the Dual-Booting Guide in my signature.

Good luck :)

---

### Post by Mooseeeeey on 2010-12-28
Sorry you ninja'd me before I could get in the 3rd edit(fail on my part)  There's a green border around D: AND E: which I think means they're both part of the Extended Partition.

---

### Post by amjjawad on 2010-12-28
> **Mooseeeeey said:**
> Sorry you ninja'd me before I could get in the 3rd edit(fail on my part)  There's a green border around D: AND E: which I think means they're both part of the Extended Partition.

Which means you can play around with "E" which is 20GB but not "D".

---

### Post by amjjawad on 2010-12-28
To make it much easier for you.
Start to backup your important Data.

Then, while you're in Windows, try to remove partition "E" which is 20GB which is the same partition you want to install Ubuntu on (I mean use that 20GB for Ubuntu) and leave it as unallocated partition. I'm using Ubuntu now, can't remember what does Windows call it but the color should be black. ALL that should be done inside that green border.

Then, from Ubuntu LiveCD, you can create the partitions you needed using GParted.

Again, have a look at the Dual-Booting Guide because it has lots of screenshots and so easy to follow.
[http://ubuntuforums.org/showthread.php?p=10257675](http://ubuntuforums.org/showthread.php?p=10257675)

---

### Post by Mooseeeeey on 2010-12-28
The border around D: and E: is continuous not 2 separate so I thought that it meant they were both Logical Partitions of the Extended Partition.

---

### Post by amjjawad on 2010-12-28
> **Mooseeeeey said:**
> The border around D: and E: is continuous not 2 separate so I thought that it meant they were both Logical Partitions of the Extended Partition.

Yes, I know. The green bored means this is the extended partition.
Any partition inside the extended partition is logical one.

---

### Post by amjjawad on 2010-12-28
[IMG]http://3.bp.blogspot.com/_T1ntsqbeRcI/TKyxgLi71mI/AAAAAAAAAAM/4B5uLnUh5A8/s1600/Disk+Manager.PNG[/IMG]


I know it's a messy one but that's all what I have now :)

Edit: Please, IGNORE the above scheme. It's very very old and I was very new to Ubuntu. Everything has changed now ;)
I'm posting it here so that you'll understand it better.

---

### Post by Mooseeeeey on 2010-12-28
Ok I'm getting a bit lost but I thgink this is what Im supposed to do:
-Delete current E: drive
-Make the 3 new partitions in extended partition root, home, and swap.
-Make first two with ext4, 3rd with linux-swap  (Got that info from guide, not sure if it's right in this situation)
-Edit them to have root with /mount, home with /home, and swap with /swap
- Go through install

Does that seem right?
*Insert desperately hopeful face here*

---

### Post by amjjawad on 2010-12-28
In your case, you got 3 partitions: C,D and E

**C** is [COLOR=Navy]**Primary**[/COLOR]
**D** and **E** are **[COLOR=Blue]Logical[/COLOR]**

Each **[COLOR=Blue]Logical Partition[/COLOR]** is "inside" the **[COLOR=Green]Extended Partition[/COLOR]**.

Hope that will help you to understand the basics :)

---

### Post by Mooseeeeey on 2010-12-28
So do I need to get rid of the D: drive from the extended for it to work or does it not matter?

---

### Post by amjjawad on 2010-12-28
> **Mooseeeeey said:**
> Ok I'm getting a bit lost but I thgink this is what Im supposed to do:

Sorry if I made you feel like that. I'll make it more simpler.

> -Delete current E: drive

Yes, do that while you're in Windows. Make sure you don't have any important data on E.

> -Make the 3 new partitions in extended partition root, home, and swap.
Yes, using GParted while you're booting from the LiveCD.

> -Make first two with ext4, 3rd with linux-swap  (Got that info from guide, not sure if it's right in this situation)
root and home is ext4
swap is swap-linux

So yes :)

> -Edit them to have root with /mount, home with /home, and swap with /swap
Yes, yes but for swap, there is no mount point. Swap is swap.

> - Go through install

GO ahead :)


Good luck :)

---

### Post by amjjawad on 2010-12-28
> **Mooseeeeey said:**
> So do I need to get rid of the D: drive from the extended for it to work or does it not matter?

Take it easy. Try to read my posts from beginning.
Try to read that guide about partitioning again.

Trust me, if this is your first time, the best thing for you to do is reading :)

Now, I'll explain it again

C is **[COLOR=Navy]Primary[/COLOR]** - Forget it
D and E are inside a big partition called [COLOR=Green]**Extended**[/COLOR].

D and E are **[COLOR=Blue]Logical Partitions[/COLOR]**.

You need to get rid of E so that you can create 3 more Logical Partitions for Ubuntu.

[COLOR=Red]Creating Ubuntu Partitions MUST be done while you're booting from the LiveCD.[/COLOR]

C and D will remain the same.

Ok so far?

---

### Post by Mooseeeeey on 2010-12-28
Yes. So I don't need to worry about C: and D: aside from backing them up, correct?

---

### Post by amjjawad on 2010-12-28
> **Mooseeeeey said:**
> Yes. So I don't need to worry about C: and D: aside from backing them up, correct?

100% correct.

As long as C is Primary
D is Logical
E is Logical

:)

---

### Post by Mooseeeeey on 2010-12-28
Ok so then I Boot with LiveCD, and do the partitioning, do the stuff with assigning Mounts (/ to root which will be 10GB, /home to home that'll be 9GB, and 1GB will be /swap.  Is that correct with mounts?

P.S.  If you can I made a tinychat for faster communication:
[http://tinychat.com/7ugig]("http://tinychat.com/7ugig")

---

### Post by amjjawad on 2010-12-28
> **Mooseeeeey said:**
> Ok so then I Boot with LiveCD, and do the partitioning, do the stuff with assigning Mounts (/ to root which will be 10GB, /home to home that'll be 9GB, and 1GB will be /swap.  Is that correct with mounts?

P.S.  If you can I made a tinychat for faster communication:
[http://tinychat.com/7ugig](http://tinychat.com/7ugig)

Yes but as I mentioned before, you don't need to mount swap. 

My connection is very slow for such chat :( sorry.
However, I'll try it again.

Edit: Sorry mate, with my current bad connection, can't make it.

---

### Post by Mooseeeeey on 2010-12-28
Ok well ix nay the chat.  So do you think I'm ready to try this? Im about to get the last of my files off the Hard drive and burning a DVD of my ghost then I'll be giving it all a go.
Edit: Does it matter what file system I use for root and home?  I saw in the tutorial it used ext4

---

### Post by amjjawad on 2010-12-28
> **Mooseeeeey said:**
> Ok well ix nay the chat.  So do you think I'm ready to try this? Im about to get the last of my files off the Hard drive and burning a DVD of my ghost then I'll be giving it all a go.

Well, it's you who can decide whether you're ready or not :)

If you ask my opinion, I guess you need to read more. I feel you have some weak points in the basics. Sorry, no offense but reading more will open lots of locked doors :)

Above all, I recommend to create a LiveUSB (in case your machine is capable of booting from USB) and keep using Ubuntu from there for few days. Try to be more familiar with it.
By doing so, you will NOT make any changes to your system.

Or

You could install Ubuntu on an External HDD or USB-Disk and no changes to be made to your HDD. Check the 3rd link in my signature.

Or

You could do a normal installation just like we explained to you here :)

You have now 3 choices see which one is easier for you :)

---

### Post by Mooseeeeey on 2010-12-28
With LiveUSB does it let me save anyything I do(installed applications, documents, etc.)?

---

### Post by amjjawad on 2010-12-28
> **Mooseeeeey said:**
> With LiveUSB does it let me save anyything I do(installed applications, documents, etc.)?

You can save them on your other partitions.
Ubuntu by default can access NTFS Partitions. While Windows can't access ext4 by default.

---

### Post by Mooseeeeey on 2010-12-28
Ok well I've decided I gunna install onto a 16GB flash drive I found, get used to linux/Ubuntu and then install onto HDD after I get comfortable. HUGE thank you for all the help.

---

### Post by amjjawad on 2010-12-28
> **Mooseeeeey said:**
> Ok well I've decided I gunna install onto a 16GB flash drive I found, get used to linux/Ubuntu and then install onto HDD after I get comfortable. HUGE thank you for all the help.

Good choice :)
Don't forget to have a look at the 3rd Link in my signature. It's 2 in 1 guide actually. Forget Wubi, just read the steps of HOWTO Install Ubuntu into an USB-Drive.

You're most welcome.
Let us know if you need anything ;)

---

### Post by Mooseeeeey on 2010-12-28
Ok well I've been farting around with Ubunutu from LiveCD and I'm wondering if it will be faster with real installation.  It seems to be going ridiculously slow, it takes about a minute to get the Software Center open, and the Top and bottom status bars disappear after about 5 minutes and I don't know how to get them back.
Info: 3.00 Ghz Processor, 512MB RAM

---

### Post by amjjawad on 2010-12-28
> **Mooseeeeey said:**
> Ok well I've been farting around with Ubunutu from LiveCD and I'm wondering if it will be faster with real installation.  It seems to be going ridiculously slow, it takes about a minute to get the Software Center open, and the Top and bottom status bars disappear after about 5 minutes and I don't know how to get them back.

Definitely, the slowest Ubuntu is the one from LiveCD.

Once you install, you'll beg it to stop ;)

Keep playing around with the LiveCD. As I said, just to be familiar with the new environment.

---

### Post by Mooseeeeey on 2010-12-28
OK, I'm back after a few hours of whats been going on:
1.  I just found out that I actually have a second, 93GB HDD, in my computer just with no data or power cables connected.
2.  Connected cables, drive worked, formatted it.
3. Used LiveCD and opened GPart
4. Made partitions on that HDD with one 70GB partition, (In extended partition):12GB ext4, 7GB ext4, 1GB linux-swap
5. Went through installation process, made 12GB as /, and 7GB as /home in mounting.
6. Set boot loader on the newely found HDD
7. Went through installation.
8. *About 2 minutes in I get an error(#5 I believe)  that says there are issues with either LiveCD or HDD.*
9.  Ben spending last 2 hours trying alternate methods of LiveCD and have had mass issues with integrity, and burning the disks
10. Tried making LiveUSB, wouldn't work and can't figure out BIOS options to make it boot from the USB properly.


Can anyone help me with all this?
* Going to try installation again and take note exactly what errors say.

---

### Post by Mooseeeeey on 2010-12-28
*Sorry double post*

---

### Post by amjjawad on 2010-12-29
Don't get me wrong but I guess you did not read any link from what I asked you to read :)

If you were trying to install to another HDD, why didn't you use the entire space for Ubuntu? as long as it's a 2nd HDD, there is no harm UNLESS there is some data you didn't backup and don't want to lose.

Problem during installation could be (mostly) bad downloaded file (MD5SUM to make sure), bad CD-Burn Process (Burn with Lower Speed) or could be problem with the HDD itself (you need to make sure there is nothing wrong with the HDD).

And good morning, I just woke up :)

---

### Post by amjjawad on 2010-12-29
> **Mooseeeeey said:**
> 
4. Made partitions on that HDD with one 70GB partition, (In extended partition):12GB ext4, 7GB ext4, 1GB linux-swap

Totally unnecessary.
As long as it's another HDD which means Ubuntu is the only OS that will use this HDD.
- Use the "entire" space of that HDD
-  You can create 3 Primary Partitions (root, home and swap) OR 1 Primary 1  Extended (extended partitions count as 1 primary partitions) and inside  that Extended there will be 2 Logical Partitions (home and swap) OR 2  Primary Partition with 1 Extended Partition and 1 Logical Partition  inside that extended Partition. These are all the possibilities.
- Don't forget to format each partition.

> 8. *About 2 minutes in I get an error(#5 I believe)  that says there are issues with either LiveCD or HDD.*

Any specific error message?

> 9.  Ben spending  last 2 hours trying alternate methods of LiveCD and have had mass issues  with integrity, and burning the disks

- In my first link (signature), there is HOWTO check MD5SUM. Not sure if I told you that already, sorry.
- Try lower speed, say 16x when you burn.

> 10. Tried making LiveUSB, wouldn't work and can't figure out BIOS options to make it boot from the USB properly.

- [http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download) - Step2. It shows how to create LiveUSB.
or
- [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

- While your USB is plugged in, reboot and enter BIOS
- You should have something like that unless your BIOS is totally different
[IMG]http://ubuntuforums.org/picture.php?albumid=2145&pictureid=7191[/IMG]

---

### Post by Mooseeeeey on 2010-12-29
Ok first off: Good morning! :D

Now,
I have read your links but maybe I'm not fully understanding everything but heres what I have to explain other things:
-I don't want to use the whole HDD space for Ubuntu because I want to keep part of the space for storage, did I do that wrong for what I want to do?
-Error message was(Not 100% accurate but close enough I think)
"The installer encountered and error copying files to the Hard Disk:
[Errno 5] Input/ Output error often due to faulty CD or drive, or faulty Hard Disk.(something saying 'we recomend'...." ...Clean CD, Hard Disk head, etc.

- I tried the USB-HDD option in BIOS and it didn't recognize anything.
EDIT: -I also tried checksumming my iso, but after burning before I can even check integrity through terminal from LiveCD I get errors.

---

### Post by amjjawad on 2010-12-29
> **Mooseeeeey said:**
> Ok first off: Good morning! :D

Now,
I have read your links but maybe I'm not fully understanding everything but heres what I have to explain other things:
-I don't want to use the whole HDD space for Ubuntu because I want to keep part of the space for storage, did I do that wrong for what I want to do?
-Error message was(Not 100% accurate but close enough I think)
"The installer encountered and error copying files to the Hard Disk:
[Errno 5] Input/ Output error often due to faulty CD or drive, or faulty Hard Disk.(something saying 'we recomend'...." ...Clean CD, Hard Disk head, etc.

- I tried the USB-HDD option in BIOS and it didn't recognize anything.
EDIT: -I also tried checksumming my iso, but after burning before I can even check integrity through terminal from LiveCD I get errors.


Good morning :)

What part that you didn't understand? I could explain it ;)

As long as that HDD will be used by Ubuntu, you can increase the size of each partition.
For example:
Make root 20-30GB
swap 1-2GB
/home 20-30GB
the remaining could be used as a data partition. After all, the whole HDD will be used by Ubuntu. You already have another HDD for Windows.

Of course, that's up to you :)
I mean, if you want to use only 30GB for Ubuntu and the reaming space for something else, of course you can do that but I'm sure you'll love Ubuntu and will come back here asking how to increase my partitions size ;)


That error message? hmmm, are you using 10.10?

Check md5sum again (make sure you're using the correct hash for your downloaded iso file).
Burn the CD at 16x speed for example

If the same message will show up, I guess you need to look into your HDD or your CD-Drive.

---

### Post by amjjawad on 2010-12-29
By the way, what OS are you using to burn the CD? what program?

---

### Post by Idefix82 on 2010-12-29
I mean no offence here, but I feel that amjjawad has been making the whole thing look rather more complicated than needed. You don't have to read books upon books to successfully install Ubuntu.

Firstly, BIOS setups can look **very** different, depending on the BIOS vendor. Sometimes, you can directly see USB among the options, when setting boot priorities, like in amjjawad's screen shot; sometimes, you can only choose between "hard drives" and "CD rom", but then there is a separate menu for the order, in which the hard drives should be tried and the USB is treated as one of the hard drives; sometimes, the USB stick only shows up as an option among the hard drives if it is connected at start up, so that your choice is not just "USB", but "USB PENDRIVE XYZ", that specific stick that you have inserted; and finally, some BIOSes just cannot boot from USB, in which case LiveCD is your only way to go. In short, you have to figure out how your specific BIOS works and look out for any one of the above options.

So here is my twopence on what you should do:
[LIST=1]
[*]Burn a LiveCD or create a USB stick. The guide to how to do that on the Ubuntu page is very detailed and you can't go wrong. If you burn a CD, do it at a slow speed (8x or 16x) and check the MD5 sum at the end. If you get errors during burning, then don't proceed and burn again.
[*]Boot from the medium that you just created and choose "try Ubuntu without making any changes". Make sure that Ubuntu starts up and recognises the most necessary hardware. If something is not recognised, it is very likely that you will be able to fix it, once Ubuntu is installed, but if you want to be safe, then you can ask here before installing.
[*]Now, either reboot and choose "Install" or click on the icon on the desktop from your live session.
[*]During the installation process, choose "manual partitioning". Create a primary partition (for /) and two secondary partitions (for /home and swap) on the HDD that you set aside for Ubuntu. I second amjjawad's suggestion to use the entire HDD for Ubuntu. If you think that you will eventually want to store your music, pictues, videos etc. on the Ubuntu HDD, you should set aside a lot of space for /home - maybe something like 30GB for / and 63GB for /home. In any case, 30GB should be more than enough for / (root), unless you are planning to install thousands and thousands of applications. Note that /home **is** traditionally used for storage of your personal files, such as music, videos, pictures, documents and so on. If you don't want to do that, then you will not need much space for /home at all. 10GB will be more than enough. Don't forget to format / and /home as ext4 or ext3. Swap is not formatted anyway.
[*]The important bit: you also have to specify on which HDD the boot loader should go. Choose the HDD that comes first in the boot order in the BIOS. The Ubuntu boot loader will incorporate Windows into the selection. If instead the BIOS tries to boot the HDD with the Windows boot loader first, then you will have to go into the BIOS, whenever you want to boot Ubuntu. In other words, either the boot loader should not go on the HDD with Ubuntu, but most likely on the HDD with Windows, or alternatively, put the boot loader on the Ubuntu-HDD, but make sure that the BIOS boots that HDD first.
[/LIST]

If you encounter specific problems, stop there and ask here. As I say, if you get errors during burning or during the verification of the MD5 checksum, don't even try to install from that CD. Instead burn a new one at lower speed, or using a higher quality blank CD or somebody else's burner, or go the USB root.

Finally, don't just say "It didn't work" or "it didn't recognise anything". Provide as many details as possible so that we can figure out, what exactly failed and how to repair it. Good luck! You will love it, once it's set up!

---

### Post by Mooseeeeey on 2010-12-29
Ok I think I'm clearer on the partitioning right now: I install with the wipe disk and install option and then just change partitions later on? or will that erase data?

Ok I'm using XP Home, and I've tried a ton of different burners and iso's:(I have md5sum checked all the iso's I try and burn, all passed except 2 so far.
The best working (post-burn)one I used CDBurnerXP, that I was able to open up LiveCD with, but that's the one I get disk error with.
I just tried 2 discs with 2 different ISO's, neither worked.  I downloaded another ISO( Probably the 15th time in past 24 hours) and it just passed md5sum.  Burning the ISO now going to try first with ImgBurn (It has built in verification that's worked), then will try with CD BurnerXP

---

### Post by Idefix82 on 2010-12-29
That sounds pretty annoying. What exactly was the problem with the USB option?

---

### Post by amjjawad on 2010-12-29
> **Idefix82 said:**
> I mean no offence here, but I feel that amjjawad has been making the whole thing look rather more complicated than needed. You don't have to read books upon books to successfully install Ubuntu.

Firstly, BIOS setups can look **very** different, depending on the BIOS vendor. Sometimes, you can directly see USB among the options, when setting boot priorities, like in amjjawad's screen shot; sometimes, you can only choose between "hard drives" and "CD rom", but then there is a separate menu for the order, in which the hard drives should be tried and the USB is treated as one of the hard drives; sometimes, the USB stick only shows up as an option among the hard drives if it is connected at start up, so that your choice is not just "USB", but "USB PENDRIVE XYZ", that specific stick that you have inserted; and finally, some BIOSes just cannot boot from USB, in which case LiveCD is your only way to go. In short, you have to figure out how your specific BIOS works and look out for any one of the above options.

So here is my twopence on what you should do:
[LIST=1]
[*]Burn a LiveCD or create a USB stick. The guide to how to do that on the Ubuntu page is very detailed and you can't go wrong. If you burn a CD, do it at a slow speed (8x or 16x) and check the MD5 sum at the end. If you get errors during burning, then don't proceed and burn again.
[*]Boot from the medium that you just created and choose "try Ubuntu without making any changes". Make sure that Ubuntu starts up and recognises the most necessary hardware. If something is not recognised, it is very likely that you will be able to fix it, once Ubuntu is installed, but if you want to be safe, then you can ask here before installing.
[*]Now, either reboot and choose "Install" or click on the icon on the desktop from your live session.
[*]During the installation process, choose "manual partitioning". Create a primary partition (for /) and two secondary partitions (for /home and swap) on the HDD that you set aside for Ubuntu. I second amjjawad's suggestion to use the entire HDD for Ubuntu. If you think that you will eventually want to store your music, pictues, videos etc. on the Ubuntu HDD, you should set aside a lot of space for /home - maybe something like 30GB for / and 63GB for /home. In any case, 30GB should be more than enough for / (root), unless you are planning to install thousands and thousands of applications. Note that /home **is** traditionally used for storage of your personal files, such as music, videos, pictures, documents and so on. If you don't want to do that, then you will not need much space for /home at all. 10GB will be more than enough. Don't forget to format / and /home as ext4 or ext3. Swap is not formatted anyway.
[*]The important bit: you also have to specify on which HDD the boot loader should go. Choose the HDD that comes first in the boot order in the BIOS. The Ubuntu boot loader will incorporate Windows into the selection. If instead the BIOS tries to boot the HDD with the Windows boot loader first, then you will have to go into the BIOS, whenever you want to boot Ubuntu. In other words, either the boot loader should not go on the HDD with Ubuntu, but most likely on the HDD with Windows, or alternatively, put the boot loader on the Ubuntu-HDD, but make sure that the BIOS boots that HDD first.
[/LIST]

If you encounter specific problems, stop there and ask here. As I say, if you get errors during burning or during the verification of the MD5 checksum, don't even try to install from that CD. Instead burn a new one at lower speed, or using a higher quality blank CD or somebody else's burner, or go the USB root.

Finally, don't just say "It didn't work" or "it didn't recognise anything". Provide as many details as possible so that we can figure out, what exactly failed and how to repair it. Good luck! You will love it, once it's set up!

No offense taken and I do respect your point of view as everyone here is trying his/her best to help others and each one has his/her own style :)

However, I'm trying to make it plain and simple. I always post the same words over and over again. I ended up by putting all that together in a very simple guide, thanks a lot for writing the same as of my guide but in different word :) **Edit**: I mean whatever you wrote, had been written but in different words.

I usually provide links to new comers. You have to read in order to make everything right. How to prove that? you already posted and the OP has to read your post in order to understand what is the next step and what he has to do so ... it is all about reading.

That's my humble point of view and again, no offense is taken, mate ;)

---

### Post by Mooseeeeey on 2010-12-29
Ok the problem with LiveUSB was that I used to create startup disk thing(forgot name and too lazy to look up :))for USB and it gave me the single-byte write error I think it was called and after about 20 mins it was only at 35% or so, then gave me error 2 minutes later. It didn't have any info inside the error box just plain "Error!" message.  SO i broke down and just copied off the data from my semi-working LiveCD and put it straight onto the USB.  I opened BIOS and found what I was 99% sure was what I wanted and tried all the different options that had USB in the name, but none worked.


Edit: This is completely off topic but I love this community and the other Linux communities I've seen.  How it's all people willing to help not trolls and spammed with '0|\/|FG U n00b! u dun know what *insert most complex theory of linux known to man*"

---

### Post by amjjawad on 2010-12-29
> **Mooseeeeey said:**
> Ok I think I'm clearer on the partitioning right now: I install with the wipe disk and install option and then just change partitions later on? or will that erase data?

If you'll go for Wipe Disk and Install option, you can not specificity mount points, etc manually. The installer will do it for you. If you want to go for that option, make sure to choose the correct HDD. If you'll choose the wrong one, all your data will be lost.

> 
Ok I'm using XP Home, and I've tried a ton of different burners and iso's:(I have md5sum checked all the iso's I try and burn, all passed except 2 so far.
The best working (post-burn)one I used CDBurnerXP, that I was able to open up LiveCD with, but that's the one I get disk error with.
I just tried 2 discs with 2 different ISO's, neither worked.  I downloaded another ISO( Probably the 15th time in past 24 hours) and it just passed md5sum.  Burning the ISO now going to try first with ImgBurn (It has built in verification that's worked), then will try with CD BurnerXP

Have you used the burner which is recommended by Ubuntu?
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)

If you pass MD5SUM then that iso file is fine. Just make sure to burn with lower speed.

---

### Post by amjjawad on 2010-12-29
> **Mooseeeeey said:**
> Ok the problem with LiveUSB was that I used to create startup disk thing(forgot name and too lazy to look up :))for USB and it gave me the single-byte write error I think it was called and after about 20 mins it was only at 35% or so, then gave me error 2 minutes later. It didn't have any info inside the error box just plain "Error!" message.  SO i broke down and just copied off the data from my semi-working LiveCD and put it straight onto the USB.  I opened BIOS and found what I was 99% sure was what I wanted and tried all the different options that had USB in the name, but none worked.


Have you formatted your USB before you create a LiveUSB?

Copying files from LiveCD to USB will not make that USB a bootable USB. That is why LiveUSB creators exist ;)

I guess I already posted that before but there you go again:
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download) - step#2 will show you howto create a LiveUSB

or

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

---

### Post by amjjawad on 2010-12-29
> **Mooseeeeey said:**
> Edit: This is completely off topic but I love this community and the other Linux communities I've seen.  How it's all people willing to help **not trolls and spammed with '0|\/|FG U n00b! u dun know what *insert most complex theory of linux known to man***"

Everyone was a novice and a beginner when he/she came here. NO ONE born knowing everything. Humans spend all their life by learning, learning and nothing but learning.

Yes, I love this forum because people here are respective but honestly, the best forum ever was antiX's forum. People there are amazing. No offense to Ubuntu's Forum but antiX's forum is my favorite ;)

Here, I spend most of the time. Helping others and learning in the process. What could be better than this?

---

### Post by Idefix82 on 2010-12-29
Just follow the step-by-step guide for creating a bootable usb stick, that is provided on the Ubuntu download page. Make sure that the file system is FAT16 or FAT32. You don't have to wipe it clean, you just have to have at least 1GB of space on it.

@anjjawad I tried to send you a private message, to not pollute this thread with meta discussions, but you don't seem to accept any :-(

And I agree with amjjawad, that once upon a time (not so long ago in my case) we all came here and were clueless beginners. Pretty quickly, you will find yourself in the position of being able to help other clueless beginners with some basic stuff, and it's a great way to give back to the community.

---

### Post by amjjawad on 2010-12-29
> **Idefix82 said:**
> @anjjawad I tried to send you a private message, to not pollute this thread with meta discussions, but you don't seem to accept any :-(

Really? let me check my options!

No worries mate, all what I wanted is to show my point of view to you of what I'm doing. Eventually, we are here to help each others, right? I'm sure you second that ;)


Edit: I didn't know I changed that option before. Anyway, you can PM me any time now.

---

### Post by Mooseeeeey on 2010-12-29
Ok so: I have a (hopefully) fully successfully burned disc, and have LiveCD up now( I'm on a laptop typing this) and need to know what to do. I click Specify partitions.  I have 60GB left after I made my data partition in GPart.  What do i do now?

---

### Post by Mooseeeeey on 2010-12-29
Ok  feel mad at myself.  I went through the entire installation succesfully and reboot. Windows Xp loads. I reread tutorial.  I put bootloader on 2nd HDD not the one with Windows on it.  Stupid me.  Now my question: if I reinstall with same options and everything just change where boot loader goes will it mess things up at all?

---

### Post by amjjawad on 2010-12-29
> **Mooseeeeey said:**
> Ok  feel mad at myself.  I went through the entire installation succesfully and reboot. Windows Xp loads. I reread tutorial.  I put bootloader on 2nd HDD not the one with Windows on it.  Stupid me.  Now my question: if I reinstall with same options and everything just change where boot loader goes will it mess things up at all?

It does not matter. As long as both OS's are working.
GRUB2 does not mind to be installed on the 2nd disk. As long as it's installed in the MBR.
Just make sure the HDD on which ubuntu is installed is the 1st HDD to boot from in BIOS.

---

