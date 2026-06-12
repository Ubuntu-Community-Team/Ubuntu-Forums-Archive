---
title: "shared files, partitions and migrating from Windows"
date: 2011-08-02
forum: New to Ubuntu
---

### Post by GSD4ME on 2011-08-02
Dear UbuntuLand,

As a complete newbie to the world of Linux/Ubuntu, I would like some confirmation, guidance and help as to what I am trying to achieve, and my apologies if this question has been answered many times before on forums (fora?) such as this, as no doubt it has.

As with others, I wish to eventually rid myself of Windows and have decided that Ubuntu is the Linux variant that I wish to use in the future.

I am no slouch with computers - (been a software engineer for 25 years) - but I am not 100% sure as to what choices I need to implement in my conversion when it comes to sharing files between Windows and Ubuntu.

I have purchased a very good book to help me - "Ubuntu for Non-Geeks" by Grant + Bull - and this is aiding me well in my progress. Nevertheless, there is one area that the book falls down on and I am surprised that my sort of question is not covered in more depth there, as I am sure that 99% of people wishing to convert to Linux are doing so from a Windows environment and would have the same queries and concerns that I have.

I wish to dual-boot using Windows and Ubuntu - purely in case my wife doesn't _want_ to become involved in Ubuntu and just in case there is something that I still need on the Windows side of things that I may have forgotten about. To this end I have come to the conclusion that I require to manually specify and create partitions during the installation sequence, rather than using the whole disk or simply letting the installer create some partitions for me for use 'side by side' with Windows.

I have no problems about understanding what needs to be done (I have played about with Ubuntu after installing it 'inside' Windows via Wubi) but the disk partitioning section worries and confuses me slightly so I need some verification from you, dear reader, that my thinking and logic is sound.

I _think_ that I need to create and specify :
- A Root partition to hold the Ubuntu software - approx 15G in size.
- A Swap partition - size of my RAM + a delta amount
- A shared partition so that I can access all my files from both Ubuntu and Windows easily. (I know that Ubuntu can access the Windows files via the 'host' folder but I need things to be nice and easy for myself and my wife, for ease of sharing, ease of data retention if I ever need to re-install Ubuntu whilst leaving my files alone). Let's reference this partition as "mysharedpartition". The book I have has told me how to do this creation but it is the nomenclature, organisation and accessibility areas that I am not 100% sure of.

Q: What will Windows see "mysharedpartition" as? Will it be a drive letter such as Q: or Z: or S: or whatever? If not, should I make Windows see this partition as a separate drive so that our files are separate from the Windows drive (C:) so when I eventually come to removing Windows, I simply 'empty' drive C:, leaving all my files on the partition/drive that is the shared portion of the HDD? This I think would also require me to copy all of our files to this new drive to enable the sharing between the two OSs, but that is no real problem.

(Note that my wife and I have separate login ID's for Windows and wish to keep that for Ubuntu, so I shall create two logon IDs on the new system)

Q: Do I also need a Windows partition or will the Ubuntu HDD setup already cope with that as the disk is formatted and running Windows anyway?

Q: Given the above setup, I _believe_ that I do not require a /home partition to hold the /home folder for us both.

Q: Is there a way of specifying the /home folder (or equivalent if /home is not needed) on "mysharedpartition" that keeps our files apart from each other? Or would it be better to have (say) three separate, new and shared partitions called "myfiles", "wifesfiles", "publicfiles", all akin to the "mysharedpartition" discussed above and mimicking the current Windows setup?

So basically what I require is for all our files to be accessible by both Windows and Ubuntu; to be private between users; to have a 'public' area so that we can share files between ourselves BOTH on Windows and Ubuntu.
As I said, the book was not clear on how to progress this sort of setup (apart from that, it is recommended reading for me) and any guidance, help and suggestions would be gratefully received.

I fear for my physical being if I manage to mess this up as my wife will beat me senseless over a period of years for losing all her data!!!!!
Many thanks
ADB

---

### Post by oldfred on 2011-08-02
I was where you are in 2006. I intially did not create a shared partition and in trying to learn Ubuntu my wife would want to check email or go on Internet with her standard bookmarks. Reboot into windows ( and 5 minutes later she could use it).

So I created a shared partition and put Firefox profiles & Thunderbird profiles into the shared and all photos. I installed the windows version of Picassa in Wine and now my wife only complains a little about it was "better" in Windows (not really as I has to to tons of maintainance to keep XP going).

I did create a separate /home for all of 5 minutes but had most of my data in the shared and decided to move my Linux data into a data partition so the folders with data (only) are separate, but the hidden folders and settings are still in / (root) and on same drive. Data is on several drives.

Originally I used FAT32 for shared but 2 years ago converted to NTFS and do not recommend FAT except for flash drives or other devices that require FAT32 to work.

The main issue on most Win7 computers is that Microsoft and the vendor have configured it in a way to make it difficult to install any thing else. Microsoft does not want you using Linux and Vendors do not want to have the cost of users calling with issues they may not be able to script to a call center. (Part of why forum is as good as it is - we try to help on just about anything).

Windows will see your NTFS partition as a D: drive or whatever is next. NTFS does not support Linux ownership and permissions which both simplifies some thing and makes it a bit more complex to initally set up.

I prefer to have an operating system on each drive and have multiple drives. Windows just does not like sharing, but many dual boot on one drive.

Heman has lots of detail. I think most of his screens are still 10.10 but procedures are the same, just some screens have changed slightly.
Install 11.04
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
Ubuntu Install steps - then choose guide, close to what you want.
[http://members.iinet.net/~herman546/index.html]("http://members.iinet.net/%7Eherman546/index.html")
Installs with good screenshots/examples:
[http://members.iinet.net.au/~herman546/p22.html]("http://members.iinet.net.au/%7Eherman546/p22.html")

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Basics of partitions:
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)


Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)
[B]Be sure to create recovery DVD(s) first. And a Windows repair CD.

[/B]Backups ---------
The vendor recovery DVDs are just an image of your drive as purchased. If you have housecleaned a lot of cruft normally included, run many updates with many reboots, and added software you may want a full back up.
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=1626990](http://ubuntuforums.org/showthread.php?t=1626990)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

Make your own Windows recoveryCD/repair:
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Windows 7 repair USB
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

---

### Post by oldfred on 2011-08-02
I do not know how to separate users. My wife & I just sign on as me. Ubuntu is a multi-user system so you can totally separate usrs, but then sharing has to also be configured. Others can help you more when you get to that point and have specific questions:

But these are some links to similar questions.
[http://content.hccfl.edu/pollock/aunix1/filepermissions.htm](http://content.hccfl.edu/pollock/aunix1/filepermissions.htm)
Two users to share music folder - group & permissions -BoneKracker:
[http://ubuntuforums.org/showthread.php?t=1484221](http://ubuntuforums.org/showthread.php?t=1484221)
[http://ubuntuforums.org/showthread.php?t=1488065](http://ubuntuforums.org/showthread.php?t=1488065)
All users read/write shared folder - morbius1
[http://ubuntuforums.org/showthread.php?t=1727396](http://ubuntuforums.org/showthread.php?t=1727396)

---

### Post by coffeecat on 2011-08-02
Welcome to the forum.

I've picked out a few points for comment.

> **GSD4ME said:**
> 
I wish to dual-boot using Windows and Ubuntu - purely in case my wife doesn't _want_ to become involved in Ubuntu and just in case there is something that I still need on the Windows side of things that I may have forgotten about. To this end I have come to the conclusion that I require to manually specify and create partitions during the installation sequence, rather than using the whole disk or simply letting the installer create some partitions for me for use 'side by side' with Windows.

<snip>

(I know that Ubuntu can access the Windows files via the 'host' folder

There's a contradiction here - I think your experience of wubi has slightly misled you. Your first paragraph implies that you want to set up a conventional dual-boot with Ubuntu on its own partitions with Linux filesystems. If so, you won't have a "host" folder to access the files on your Windows C: partition. The host folder is specific to wubi. Instead you will be able to mount the Windows partition from the Places left pane of a Nautilus (file browser) window.

> **GSD4ME said:**
> 
Q: What will Windows see "mysharedpartition" as? Will it be a drive letter such as Q: or Z: or S: or whatever?

Yes - if your format it NTFS. A shared data partition to be accessible by both Ubuntu and Windows is a common solution. Windows will see it as D:/E:/Z:/whatever. If you make the partition label "mysharedpartition" you will see that label in the left pane of Nautilus and will be able to mount it by clicking on it. Easy!

> **GSD4ME said:**
> 
Q: Given the above setup, I _believe_ that I do not require a /home partition to hold the /home folder for us both.

I would agree with you. Some people prefer a separate /home partition. But if you have a separate data partition, you might as well keep all your personal files on that and your /home folder relatively empty.

> **GSD4ME said:**
> 

Q: Is there a way of specifying the /home folder (or equivalent if /home is not needed) on "mysharedpartition" that keeps our files apart from each other? Or would it be better to have (say) three separate, new and shared partitions called "myfiles", "wifesfiles", "publicfiles", all akin to the "mysharedpartition" discussed above and mimicking the current Windows setup?

So basically what I require is for all our files to be accessible by both Windows and Ubuntu; to be private between users; to have a 'public' area so that we can share files between ourselves BOTH on Windows and Ubuntu.
As I said, the book was not clear on how to progress this sort of setup (apart from that, it is recommended reading for me) and any guidance, help and suggestions would be gratefully received.

This is where you're going to come unstuck. Basically, Ubuntu (Linux) does not recognise Windows permissions on NTFS-formatted filesystems, and NTFS does not support Linux permissions. There are some 3rd party drivers for Windows that can read (some) Linux filesystems, but they get around the Linux permissions with a kludge. Long story short - you're not going to be able to use file permissions to keep private files private if you share data between operating systems. One OS will not respect the other's permissions.

---

