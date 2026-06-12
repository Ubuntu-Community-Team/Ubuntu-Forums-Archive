---
title: "Difficult Installation"
date: 2011-06-22
forum: New to Ubuntu
---

### Post by E-Tramp on 2011-06-22
Ok, here is the deal.  I recently installed Ubuntu 7.10 and had a horrendous time trying to install it and ended up with a bad install because I couldn't figure out how to designate the partition I wanted it in the Root file partition.  I finally knew what I had to do in 7.10 to designate the Root File partition and I completely rewrote my hard drive with my Windows program to get rid of the 7.10 programming, and decided in the process to install a newer version out of necessity. I ordered a disk of 11.04.

Upon starting to install the newer version I find that the installation process has changed so much that I am once more unable to designate the partition I want to, to be the Root file partition. It say's to use the partition menu to designate the partition as the root file but, doesn't say what to do to do that, and I can't even find the "partition menu" to access it.  The only menu I seem to get to from that window in the process, has nothing about "root file" in it.  I can designate the swap file, I think, but, what the hell do I do to designate the root file?

---

### Post by Blasphemist on 2011-06-22
Try using this guide from Herman.
[http://members.iinet.net.au/~herman546/index.html](http://members.iinet.net.au/~herman546/index.html)

Or this one on disks and partitions.
[https://help.ubuntu.com/10.10/hardware/C/disks.html#creating-new-partition](https://help.ubuntu.com/10.10/hardware/C/disks.html#creating-new-partition)

---

### Post by E-Tramp on 2011-06-23
Alright, Jim is it?  This is not helpful. I apologize if I wasn't being clear, but, I don't need to create any partitions.  I don't need to resize any partitions.  They are already there and ready to use. What I need is to make the installation install where I have it ready for it to be installed.  It is not the same as with 7.10 at all, and I am more than just a little put out that it is not only not any easier than 7.10 but considerably less self evident.  I can't even find the proper menu or the proper designation to make the program install into the prepared space as it is.  I don't want it screwing up my system again resizing things I don't want resized.  That is how it trashed my system the first time.  All I want is to tell the system to install it here, and have it do what I want.  That should be fairly simple, and appearantly it is not.  It was simple in 7.10.  I just didn't know how to do it until I had already trashed my windows programming installing it where it wanted until it was too late.  Now I find that they have none of the same proceedure in 11.04, and I can't find a menu that desinates the partition or determine what the program is looking for or how to give that information from the information available at the point of installing the program.

A simple explanation of how and where to find the partition menu at the point of installation, and what information the program(and I mean 11.04) wants from that menu to make it install where I choose would suffice. On my system it is not going to be making any partitions on its own. It already did that and that was a mistake.  I will tell it where to go, not the other way around.  Just tell me how to tell it how to do it from the installation menus.

---

### Post by Blasphemist on 2011-06-23
After you choose to install Ubuntu, the Allocate Drive Space screen comes up. The options are dependent on what is already installed but there should be an option that says Something Else. This option provides the partition options you are looking for. This will allow you to choose the partition(s) to use.

---

### Post by E-Tramp on 2011-06-28
OK, well, here is the update on my attempt to install Ubuntu 11.04 on my computer.  I did find the right menu's and got the installation started, but, something went wrong and the installation froze and the program self terminated, and I had to discontinue the attempt.

after I shut the live disk down, I went back to Windows to delete the partitions and start from scratch.  I managed to delete one of the partions, but when I tried to delete the next one, it wouldn't delete.  I had put both partitions inside a logical drive so that I could have more than four partions on the hard drive (windows xp only allows up to four), and rather than delete the other partition, somehow the logical drive swallowed the partition right next to it, and three partitions now existed inside a logical drive, and I couldn't delete any of them.  I thought, well, just reboot the machine and maybe then it would take care of itself.  So, I did, only well, my hard drive just disappeared from the My computer file, and from the Disk Manager.

The computer says it is there and working properly, but, no way to access it.  The odd thing is that the Ubuntu disk does detect it, and I can access it and format it with Ubuntu.  For now I have replaced the hard drive and salvaged the files from the two partitions that I could get to in Ubuntu and the Data recovery program I have on my windows program, but, it took me three days to recover from my first attempt to install Ubuntu, and I am nervous about trying again after Three days and 65 dollars later.

I am going to ask a question now.  Do I have to have three partitions?  I recall reading something about "/", "/swap", and "/home", and I now am uncertain of the required partitions.  As I recall, 7.10 only had two, and I wonder where the third came into it.

---

### Post by Jagoly on 2011-06-28
You don't need a /home partition. That's just for safety. /home is where all of you documents and settings are stored. that way, if the / partition is corrupted, you won't lose anything.

What partitions is windows/oem currently using?

---

### Post by Ozymandias_117 on 2011-06-28
/home is just recommended, not required. (Well, swap is too, but... nevermind.)

swap is just swap, it's not mounted on root as /swap. - It's used when you run out of ram; just like a pagefile in Windows. (Highly recommended)

/ is where everything goes, analogous to C: in Windows.  You can't install without this one.

Personally, I only use a swap partition and a root (/) partition for my installs, then I have a second drive that I mount as data.

---

### Post by nzjethro on 2011-06-28
> **Ozymandias_117 said:**
> Personally, I only use a swap partition and a root (/) partition for my installs

Personally, I just have /, with a swap file contained inside (I hear this isn't fantastic for performance, but I haven't noticed the system to be laggy at all). OP could consider that option.
I do have a ntfs partition mounted which has my shared Docs, Pictures, and Movies with my Win 7 install.

---

### Post by crispy_420 on 2011-06-28
The only two partitions really needed, as others mentioned, are / and a swap partition. Some people like the /home option and I had an instructor that pushed the /boot as its own partition. But these over complicate the issue, just do a simple install.

You mentioned free space on drive, just tell installer to use that area and let it auto setup the space. When it ends you have three partitions on the drive: Windows, / and swap.

---

### Post by Ozymandias_117 on 2011-06-28
> **nzjethro said:**
> Personally, I just have /, with a swap file contained inside (I hear this isn't fantastic for performance, but I haven't noticed the system to be laggy at all). OP could consider that option.
I do have a ntfs partition mounted which has my shared Docs, Pictures, and Movies with my Win 7 install.

I've never actually seen my computer touch the swap space ;P I just have it for the ability to hibernate.

---

### Post by E-Tramp on 2011-06-28
OK, here's a question then.  If you create a home partition is it accessable in windows? Because I was never able to access any files on 7.10 in windows, unless I put them in a file on my windows operating system because I don't have access to the partitions that Ubuntu is installed on, in windows xp.  All of my files on windows however were accessable to ubuntu.  I have my windows program set up so that it will keep several files on hard disk partitions that aren't rewritten by my backup drive so when I do have to rewrite my hard drive I lose a minimum of files and information.  Usually my favorites files and my e-mail files if I forget to back them up.  All of my more important files are on the secondary drive, which is why I am nervous about trying to install Ubuntu again after losing one secondary hard drive doing it.  Those files were recovered, but, only because I could still access them through a file recovery program I already had on my system, and Ubuntu that was able to access the drive.  It occurs to me that if I could install my old hard drive with the other two that my windows system needs to operate properly, I could use it for the Ubuntu drive since those partitions are never visible in windows anyway.  I can't, however, hook up a fifth IDE/ATA item on my computer I would have to lose one of the CD drives.  Not an impossible situation, but, not prefered either.

---

### Post by crispy_420 on 2011-06-28
Your /home will more than likely be inaccessible in Windows because the native Linux partitions can not be read. In fact I think they are seen as unformatted space. There is some third party tools to let Windows read ext2/3/4 but haven't used them in years so I can't comment on them.

---

### Post by beew on 2011-06-28
I am for /home partition, that makes updating OS very easy, just do a fresh install and use the same /home partition, all your data and settings are kept intact. Never do OS upgrade through the update-manager, not only that it takes hours, it will likely screw you up badly.
> 
 If you create a home partition is it accessable in windows?No, Windows can't read Linux file systems (there is a utility called Ext2IFS which allows WIndows to access Linux file systems but according to its website it supports Windows only up to Vista and Linux file systems up to only ext3, so it is kind of obsolete)

---

### Post by E-Tramp on 2011-06-29
OK, well I guess it isn't critical to have complete access to the Linux files in windows, but, because I have yet to find a way to access the internet with Linux, I have had to save internet pages on my computer for instructions on how to install things like dialup drivers.  So far though I can't get the modem to work in Linux.  I found the right drivers and 7.10 said they were installed properly, but, I still could not initiate an internet connection with Linux.  Since I have Firefox browser on my windows installation I can get whole web pages in Windows if I use it, and display them in Linux.  So I can sort of jump the fact that my internet connection isn't there until I figure out how to get the modem to work.  If I could access Linux with Windows the same way I can access windows with Linux I could put those interchangable files directly in a Linux folder.  It would just save picking up the files from a windows folder.  I can still do it the way I have before, but, I was just curious if there was a way to access at least some of the files in Linux.

---

### Post by Blasphemist on 2011-07-01
> **E-Tramp said:**
> OK, well I guess it isn't critical to have complete access to the Linux files in windows, but, because I have yet to find a way to access the internet with Linux, I have had to save internet pages on my computer for instructions on how to install things like dialup drivers.  So far though I can't get the modem to work in Linux.  I found the right drivers and 7.10 said they were installed properly, but, I still could not initiate an internet connection with Linux.  Since I have Firefox browser on my windows installation I can get whole web pages in Windows if I use it, and display them in Linux.  So I can sort of jump the fact that my internet connection isn't there until I figure out how to get the modem to work.  If I could access Linux with Windows the same way I can access windows with Linux I could put those interchangable files directly in a Linux folder.  It would just save picking up the files from a windows folder.  I can still do it the way I have before, but, I was just curious if there was a way to access at least some of the files in Linux.

I created an ntfs partion for shared files to be used by both windows and multiple linux distro's. I also created and deleted other partitions and for the moment I am having a boot issue. I have a thread on that that you could watch. [http://ubuntuforums.org/showthread.php?p=11003745#post11003745](http://ubuntuforums.org/showthread.php?p=11003745#post11003745)

I'm on my Ubuntu install right now and can boot windows and will get past the issue. NTFS can be seen by both windows and linux, as could FAT or FAT32 but NTFS is better to use.

---

### Post by E-Tramp on 2011-07-03
OK, I thought I would update my current status.  First I have yet to try to install 11.04 after my desasterous previous attempt.  I am being cautious because of what happened to my 250 GB harddrive.  The good news is that appearantly the failed Ubuntu 11.04 install caused the harddrive partition table to be corrupted.  The cause is uncertain and maybe some of you can answer the question as to why.  When I went to install on that drive, I used a logical drive setup so that I could have my harddrive divided into 5 instead of 4 parts, and because I thought that way the drives should be visible in windows.  The logical drive contained both the boot sector and the swap file, and the install self terminated and I wasn't able to delete the drives in Windows, when I rebooted.  What I think happened is, that Ubuntu will automatically make the partitions it uses undetectable for windows, and because of the logical drive, the program wasn't able to do that and it aborted causing the partition table in Windows to be left in a corrupted state.  After reboot, the harddrive didn't show in either My Computer, or in Disk Manager.  After hours of painstaking internet searches for information on repairing the problem, and finding nothing of much help, I remembered that I had the installation disk for the harddrive in my file cabnet.  I got it out and installed some troubleshooting software from the disk and found that the software refered to the drive as something like "unprepared".  So, it also occured to me that if that was the problem then the disk could probably do the installation preperation.  I inserted the disk and the first thing it did when it booted in the drive, was it flagged the fact that,"an unprepared drive has been located on your system, do you wish to prepare it now?"  I answered yes, and it gave me an interface that allowed me to choose the size of the partition to prepare, and I chose the full volume as it was a question to me how I would size the various partions with that particular itnerface and I could always repartition afterwards in the disk Manager.  

Wallah, the harddrive returned and is now back in business, though I did have to buy a new one to put the files on that were recovered earlier from it, all in all I was happy that nothing was permanantly broken.  I will make good use of the addition drive now. I do not reccommend using a logical drive created in widows to try and install Ubuntu in, even if it did only cost me a great deal of wasted time fixing everything I managed to break,(close to a week now, I think).

Next comes another attempt to install the 11.04 on the new drive, no logical drive this time, and will just let ubuntu install on an area of the drive where I will delete one of the partitions for both the boot partition and the swap file, and set them up in ubuntu in the free space left behind during the installation, and forget about trying to make the files accessable.  Maybe like Blasphemist I will create a shared file partition.  We will see.

One more question, and I don't know if I am saying this right here or not, part of the installation askes about what drive to install the boot sector(not the boot partition), and I think if my memory serves me right it defaults to the "a" drive, and I am installing the Ubuntu program on the "b" drive.  Am I correct in assuming that the boot sector which I assume is the grub, still has to be installed on the "a" drive with the boot sector for windows, and if I just leave it at the default location the program will install it in the appropriate place?

Hope things go better this time.

---

### Post by E-Tramp on 2011-07-03
You mentioned free space on drive, just tell installer to use that area and let it auto setup the space. When it ends you have three partitions on the drive: Windows, / and swap.[/QUOTE]

Actually this won't work.  If I did this,(because I have) the program installs at the back end of the windows partition, and on the front end of my Drive Image back up drive, and disables my backup drive because it is required that the back up and windows programming be right next to each other.

The Ubuntu program has to go on a space I put it in, on my secondary drive, and function from there.

---

### Post by wildmanne39 on 2011-07-03
> I do not reccommend using a logical drive created in widows to try and install Ubuntu in, even if it did only cost me a great deal of wasted time fixing everything I managed to break,(close to a week now, I think).Hi, you do not create partitions for ubuntu in windows,all you do from windows is resize your partition to make room for the ubuntu partition, then you fire up the livecd and create the partition from the livecd, using ext4 preferably. Here is a guide to help.
[http://ubuntuforums.org/showthread.php?t=1713649](http://ubuntuforums.org/showthread.php?t=1713649)
scroll down the page some and you will see pictures of how to partition for ubuntu.

---

### Post by E-Tramp on 2011-07-03
I am aware that you don't have to, doesn't mean you can't.  Unfortunatly, Ubuntu will delete the drives on the Windows side.  My objective at the time was to make both the files for Ubuntu and windows accessable from either side so files could be transfered both ways.  As it stands I have to transfer them only on the Ubuntu side because Ubuntu doesn't show on the Windows side.  I don't have access to the internet with Ubuntu yet, because I have yet to make my modem work with Ubuntu.  The las time I tried the system said the driver was installed properly, but, still no modem.  That means I have to get downloads from the internet with windows, and then take them from a windows folder and move it to the Ubuntu drive.  So, I am constantly moving files and switching from one system to the other.  In time if I finally get the hardware working I won't have to, but, this is the way it is now.  As I said above, I will be using free space next time because I have to, not because I want to.

---

### Post by Blasphemist on 2011-07-03
> **E-Tramp said:**
> I am aware that you don't have to, doesn't mean you can't.  Unfortunatly, Ubuntu will delete the drives on the Windows side.  My objective at the time was to make both the files for Ubuntu and windows accessable from either side so files could be transfered both ways.  As it stands I have to transfer them only on the Ubuntu side because Ubuntu doesn't show on the Windows side.  I don't have access to the internet with Ubuntu yet, because I have yet to make my modem work with Ubuntu.  The las time I tried the system said the driver was installed properly, but, still no modem.  That means I have to get downloads from the internet with windows, and then take them from a windows folder and move it to the Ubuntu drive.  So, I am constantly moving files and switching from one system to the other.  In time if I finally get the hardware working I won't have to, but, this is the way it is now.  As I said above, I will be using free space next time because I have to, not because I want to.
I recommend that you look in depth at this link. [http://members.iinet.net.au/~herman546/index.html](http://members.iinet.net.au/~herman546/index.html)

Herman has created a very descriptive and informative site on setting up dual boot. I will mention these things. There are primary and extended types of partitions. You can have up to 4 primary partitions, and an extended partition is counted as a primary partition. Ubuntu and other linux distros are installed within the extended partition. From the Ubuntu live cd or in Ubuntu you can review the partitions. To make changes, you need to run it from the live cd as any partition you are going to change can't be mounted. You should do your partition changes, and then go about using them in the installation.

Ubuntu give you options during install. Left to make the decisions itself, it will use unused space or if necessary shrink the windows partition to create root (/) and swap partitions. I recommend that you use Herman's documentation that includes screenshots, plan ahead and then handle the partitioning yourself in GParted or follow Herman screen by screen.

Windows can't read partitions formatted for a file system that linux uses, the EXT4, 3 or 2 journaling file systems. Linux can read and write to ntfs or fat formats that windows uses. That is why I created a ntfs partition that both linux and windows can use for my shared data files.

I know this is kind of complicated so let me know if you have any questions that this and Herman don't answer.

Jim

---

### Post by wildmanne39 on 2011-07-03
Hi, here is a link to read ubuntu files from windows.
[http://www.diskinternals.com/linux-reader/](http://www.diskinternals.com/linux-reader/)

---

### Post by E-Tramp on 2011-07-04
Thanks guys, I will look at these, in fact, I think that I have one of them on a saved web page so I could access it from the Ubuntu live disk.  That is the one with the step by step screen shots.  I saved it a few days ago before I managed to revive my 250gb harddrive.  I do feel a lot better about doing the install now that I got the other harddrive back.  Will be back after I do some reading.

---

### Post by E-Tramp on 2011-07-05
Windows can't read partitions formatted for a file system that linux uses, the EXT4, 3 or 2 journaling file systems. Linux can read and write to ntfs or fat formats that windows uses. That is why I created a ntfs partition that both linux and windows can use for my shared data files.Jim[/QUOTE]

So, EXT4,3 and 2 are the default formatting system used by Linux? I thought that if you select NTFS on the installation it creates the operating system on an NTFS file system.

---

### Post by E-Tramp on 2011-07-05
OK, I just got done reading this link,[http://ubuntuforums.org/showthread.php?t=497205](http://ubuntuforums.org/showthread.php?t=497205) and this is very similar to what happened to me.  I believe because I created partitions in Windows and then on the installation may have recreated them, that I got some confusing information for the computer in the partition table.  This caused the corruption of the partition table and the complete loss of linking information to the secondary harddrive when I tried to delete the partitions in Windows.  I think if I would have gone into the Ubuntu live disk and deleted the partitions there, then on the return to Windows if any still existed there, delete them there it might have saved me a lot of trouble.  As it stands, since I had GetDataBack already installed on my system, and like Djinn Effer, I had a PowerQuest DISE backup system, that protected my main drive,(which she used as the installation partition, thus, disabling her backup drive), and I also, like her, had PowerQuest Partition Magic for Partition manipulation, which like hers was giving an error when I tried to access it with the harddrive undetectable,(I later found that the Partition Magic program was installed on the drive that wasn't detected anymore).  The best scenario here is, if you have this problem and are in the it's too late to delete these partitions the right way, is use GetDataBack to recover your files back to your main harddrive available at MajorGeeks.com, and it is shareware which cost me 70 dollars as I recall, as many as you can each time, and put them on another drive, then use your installation disk from your harddrive,(mine was Western Digital), and re-write the partition table then replace all of the files back on the drive again. If you don't want to spend 70 dollars, you can also use the live disk of Ubuntu to move the files from your lost drive to your OS drive and then move them to a new drive you have to recover them to.  One way or the other, you should always have a backup drive for your data, both primary and secondary, and since hardrives have begun to get pretty cheap, this isn't a major outlay of cash.  In fact most cost less than 70 dollars.  I would have transfered the files to the new drive directly using Ubuntu live disk, but, found that I was unable to boot the live disk with the windows OS disconnected and the new drive and old drive connected.  Can't say why it wouldn't, seems like it should have.

If you can get a disk recovery program like Djinn did and get the drive back itself, that would be easier.  I was already done with my reclamation when I read this.

---

