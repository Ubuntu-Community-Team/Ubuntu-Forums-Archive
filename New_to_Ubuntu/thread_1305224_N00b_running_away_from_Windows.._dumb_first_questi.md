---
title: "N00b running away from Windows.. dumb first question."
date: 2009-10-29
forum: New to Ubuntu
---

### Post by Captain Kremmen on 2009-10-29
First off, Hello everyone..

I've decided to make the plunge and dump Windows (except for some gaming :/), tired of the control being wrestled away from me and being given to Redmond.. so I have finally got off my bum and downloaded 9.10... and my Linux adventures begin.

However having never used it before I have a couple of noob questions before I hit the 'install' button.

Firstly, I want to dual boot and do not want to harm my current install of XP (yeah, the gaming thing :/), can I just install from the booted Linux disc as per normal or do I have to do anything else in order not to harm my current OS?. 

Also I notice that Ubuntu (among others) now also reads and writes to an ntfs drive (nice).. however I was wondering if this is the best file system to use on an installation, or whether I should set a side another drive and give that a specific file system to work with?

Ok thx for now....obviously I'll be searching for my own answers first but I think there are going to be loads of other questions posted by me.. I've still to get my usb dsl modem working :/ lol.

---

### Post by hotmail@yahoo.com on 2009-10-29
Hi Captain,

               I am new here as well and I hope my response will help you.

a) Yes you can install dual boot. I have a laptop with win vista and ubuntu 8.10 installed. I had windows first then installed Ubuntu. It automatically recognizes your that you have windows installed in your another drive and it will appear as a dual boot when you restart your pc.

b) Yes you should partition your drive. Create a new partition and install ubuntu in that one.

---

### Post by phillw on 2009-10-29
> **Captain Kremmen said:**
> First off, Hello everyone..

I've decided to make the plunge and dump Windows (except for some gaming :/), tired of the control being wrestled away from me and being given to Redmond.. so I have finally got off my bum and downloaded 9.10... and my Linux adventures begin.

However having never used it before I have a couple of noob questions before I hit the 'install' button.

Firstly, I want to dual boot and do not want to harm my current install of XP (yeah, the gaming thing :/), can I just install from the booted Linux disc as per normal or do I have to do anything else in order not to harm my current OS?. 

Also I notice that Ubuntu (among others) now also reads and writes to an ntfs drive (nice).. however I was wondering if this is the best file system to use on an installation, or whether I should set a side another drive and give that a specific file system to work with?

Ok thx for now....obviously I'll be searching for my own answers first but I think there are going to be loads of other questions posted by me.. I've still to get my usb dsl modem working :/ lol.

Hi, welcome.
There's no such thing as a dumb question.

For dual booting .....

[http://apcmag.com/the_definitive_dualbooting_guide_linux_vista_and_xp_stepbystep.htm](http://apcmag.com/the_definitive_dualbooting_guide_linux_vista_and_xp_stepbystep.htm)

An excellent tutorial

Regards,

Phill.

---

### Post by Rocket2DMn on 2009-10-29
Welcome Captain!  Yes, you can install from the LiveCD.  First you will need to make room on your hard drive for Ubuntu though, so in Windows you should defragment your hard drive.  Then when you are in the Ubuntu LiveCD, during the install, you can resize the Windows NTFS partition to make room for Ubuntu.  You don't need a ton of space for Ubuntu, esp. if you plan on keeping your data on Windows for now.  As you said, Ubuntu and read and write NTFS just fine.  Windows doesn't read linux file systems as well (you need a third party driver for this), so I recommend keeping your data on the NTFS partition for now.  It shouldn't be needed, but I always recommend backing up your important data before resizing the drive and installing (not so much in case the installer messes up, but in case you do!).

If you have another hard drive, you can install Ubuntu there without needing to resize your NTFS partition.  Ubuntu will use an ext4 filesystem by default.

As always, if you have any questions or feel uncomfortable proceeding, don't hesitate to ask!

---

### Post by Captain Kremmen on 2009-10-29
Hey :)

Thx for the reply.. ok, I'll install to a clean drive. would you recommend any particular file system or just go with ntfs?

I know Ubuntu uses Ext3/4, are there any advantages/disadvantages to using one of these (I was considering Ext3 simply because it has matured a bit over Ext4, which I understand is still slightly less stable) over ntfs.

Ta.

---

### Post by sloggerkhan on 2009-10-29
> **Captain Kremmen said:**
> Hey :)

Thx for the reply.. ok, I'll install to a clean drive. would you recommend any particular file system or just go with ntfs?

I know Ubuntu uses Ext3/4, are there any advantages/disadvantages to using one of these (I was considering Ext3 simply because it has matured a bit over Ext4, which I understand is still slightly less stable) over ntfs.

Ta.

You do not want to use an ntfs filesystem for a linux install unless you use wubi. I don't really recommend wubi, but it can be an easy way to ease into things comfortably.

---

### Post by Captain Kremmen on 2009-10-29
OK.. thx all.. off to install :)

I will return :/

---

### Post by Rocket2DMn on 2009-10-29
I would use ext4, it has been around for awhile and has proven stable, with some improvements over ext3.  If you are really interested, ext4 can be tweaked for even better performance.  I don't have material on that, but it is out there.

NTFS is fine for sharing your data between Windows and Ubuntu.  Some people don't like it because it isn't FOSS in nature, but we live in a world where we have to play nicely with others.  Some people recommended FAT32 over NTFS, but I don't think it's better, and it has the 4GB file size limit.

---

### Post by twright on 2009-10-29
Ext4 is the fastest and it has some nice features to prevent corruption - for all intents and purposes it is the best option. If you go for Ext3 you might have a tough job upgrading sometime in the future.

I would not recommend you create many new partitions in Ntfs as it will be slower and more prone to corruption than the other options. Even fat is probably a better option for shared storage. You cannot install ubuntu on these less capable file systems in any case (only native linux ones including ext4/ext3/ext2/xfs/jfs and reiserfs).> **Captain Kremmen said:**
> Hey :)

Thx for the reply.. ok, I'll install to a clean drive. would you recommend any particular file system or just go with ntfs?

I know Ubuntu uses Ext3/4, are there any advantages/disadvantages to using one of these (I was considering Ext3 simply because it has matured a bit over Ext4, which I understand is still slightly less stable) over ntfs.

Ta.

---

### Post by paynek716 on 2009-10-29
Good step by step here as well
[https://help.ubuntu.com/9.04/switching/index.html]("https://help.ubuntu.com/9.04/switching/index.html")

You won't regret it.

---

### Post by amjjawad on 2009-10-31
[U]NOTE: I'll be talking about Dual booting (Vista installed first then Ubuntu 9.10).
[/U]


Hello everyone,

I'm very new here, just registered and today is my 1st day with Ubuntu. One of my friends advised me to install Linux/Ubuntu and keep Windows (Vista) for gaming and stuff so I can get the best of the two worlds. I have 10 years experience with Windows and I was trying to find something better but honestly was too lazy to change until I made my mind to go for Ubuntu.

I'll start with my problem and will try to explain in details (Note that whatever I've done is based on what my friend has told me coz he's been using Ubuntu for years):

a) I have a PC (P4) with Windows Vista (SP2)and 2 HDDs (2 physical discs). Windows Vista installed on the 1st HD (150GB) and the 2nd HD (500GB) is for movies, games, etc. Each HD has partitions already.

b) Before starting with Ubuntu's installation, I tried to play around with my partitions. My 2nd HD has 3 partitions (122GB,122GB,250GB). I deleted the 1st and the 2nd partition so I got 2 partitions, each is 250GB in size. My friend told me I do need 4 partitions for Ubuntu (Root, Swap, Home, Date) and I understood why I do need 4. I read somewhere that under windows, I can't create more than 4 partitions in **"ONE Primary Partition"** and that was true coz Windows didn't allow me to have 4 partition (note that I'm talking about partition 1 (250GB) in HD2 (500GB)- I didn't touch partition 2 (250GB) coz it's for Windows and has lots of games). So tried to play around and created a logical partition (after many times of deleting and creating partitions) and at the end I was able to have 4 partitions (on partition 1 - HD2) + another untouched partition (partition 2 - HD2) coz it's for Windows as I said and I don't want to use it at all. Forget about any partition that related to windows and let's talk about my partitions that are related to Ubuntu, deal?

c) Started the installation and followed my friend's instructions.

d) I chose "Specify partitions manually (advanced)"

e) Started to assign a function to each partition (sorry if I'm using the wrong terms) and that means I was trying to set a "root (/)" partition, a "swap (swap area)" partition, a "home(/home)" partition and a date partition. Also to mount and format them.

>> Problems started from here ...

f) Before installation, ALL my HDs were NTFS and I came to know that Ubuntu can't read/write NTFS file system but maybe I was wrong, not sure yet :S. I chose ext4 for "/" which is the root partition where Ubuntu's system files will be installed. There was no options for "swap area", I mean couldn't choose what file system to be used and there was no option to format that partition if I'm not wrong. I choose ext4 (if I'm not mistaken" for "/home" partition. >> (HERE IT COMES) Finally, tried to choose FAT32 for the largest partition (partition 4 for Ubuntu) so I can store my date there + I can access that partition from Windows as well BUT Ubuntu never allowed to go on with the installation :( and it took me back to the partitions table. Chose "/windows" but it didn't let me do it as well. Finally, I chose "/usr" and format as FAT32 or something else, can't remember and only then it proceed with the installation.

g) After installation was done, guess what? I was unable to access the 4th partition (198GB) neither from Ubuntu nor from Vista so basically I lost around 200GB and can't access it whatsoever.

I have two Qs here:
1- HOW to fix that?
2- How to uninstall Ubuntu and get back to Vista without getting that booting list anymore?

Thank you so much and so sorry for writing too much!

AJ

P.S.
I did not touch HD1 along with its partitions bcoz Vista installed there so during Ubuntu installation, I didn't touch/choose anything related to HD1 along with its partition and maybe that's why I can't access them from Ubuntu.

---

### Post by mapes12 on 2009-10-31
[http://members.iinet.net.au/~herman546/index.html](http://members.iinet.net.au/~herman546/index.html)

---

### Post by yanceypd on 2009-10-31
With Vista first do a defrag to compact the windows system. Use the live Cd boot to it and select either side by side, there is a white slider you can move to adjust the partition size if on a single drive or a pulldown tab on the right to select the other drive if multi drive system and you want to use the entire disk.  Should go smoothly from there.  Defraging Vista is the key to smooth dual boot setup.

---

### Post by yeats on 2009-10-31
@amjjawad - it's a good idea to start your own thread so people realize you're not just responding to this one :-)

> I have two Qs here:
1- HOW to fix that?

Sounds like you have several issues to fix.  I recommend reverting to Vista (which I see you're asking how to do), and if you're still interested, follow one of the links in this thread to the useful dual-booting guides people have posted.  TIP:  Don't create the partitions in Windows - Ubuntu can and should do this.  Also, let it create your partitions automatically.

> 2- How to uninstall Ubuntu and get back to Vista without getting that booting list anymore?

If you have the Vista CD/DVD, there is an option to restore the Master Boot Record, this will re-load Vista's bootloader.  Once in Windows, you may delete the Ubuntu partitions if you feel the need.

---

### Post by amjjawad on 2009-10-31
> **chrissharp123 said:**
> @amjjawad - it's a good idea to start your own thread so people realize you're not just responding to this one :-)



Sounds like you have several issues to fix.  I recommend reverting to Vista (which I see you're asking how to do), and if you're still interested, follow one of the links in this thread to the useful dual-booting guides people have posted.  TIP:  Don't create the partitions in Windows - Ubuntu can and should do this.  Also, let it create your partitions automatically.



If you have the Vista CD/DVD, there is an option to restore the Master Boot Record, this will re-load Vista's bootloader.  Once in Windows, you may delete the Ubuntu partitions if you feel the need.
I know that, sorry :P

1- I'm guessing that was my problem, I shouldn't have created the partitions under Windows! I blame my friend :P

2- One of the users has posted this: [http://members.iinet.net.au/~herman546/p18.html#If_you_are_about_to_uninstall_Ubuntu](http://members.iinet.net.au/~herman546/p18.html#If_you_are_about_to_uninstall_Ubuntu) and I'm reading it now. Do you recommend to read that or use my Vista's CD?
I don't want to lose my Windows's partitions coz I have lots of date, movies, games, etc.

To make life easier: In order to fix problem 1, I need to uninstall Ubuntu and install it again and to uninstall Ubuntu, shall I use my Vista's CD or that link ([http://members.iinet.net.au/~herman546/p18.html#If_you_are_about_to_uninstall_Ubuntu)?](http://members.iinet.net.au/~herman546/p18.html#If_you_are_about_to_uninstall_Ubuntu)?)

Thank you :)

---

### Post by yeats on 2009-10-31
> 2- One of the users has posted this: [http://members.iinet.net.au/~herman5...install_Ubuntu](http://members.iinet.net.au/~herman5...install_Ubuntu) and I'm reading it now. Do you recommend to read that or use my Vista's CD?

That sounds unnecessarily complicated to me... The Vista CD has a "recovery" option of some sort and one of those options is to restore the MBR automatically.


> To make life easier: In order to fix problem 1, I need to uninstall Ubuntu and install it again and to uninstall Ubuntu, shall I use my Vista's CD or that link ([http://members.iinet.net.au/~herman5...stall_Ubuntu)?](http://members.iinet.net.au/~herman5...stall_Ubuntu)?)

Focus on getting Vista running, then worry about Ubuntu.  You can't do more than one thing at a time! :-)

---

### Post by amjjawad on 2009-10-31
> **chrissharp123 said:**
> That sounds unnecessarily complicated to me... The Vista CD has a "recovery" option of some sort and one of those options is to restore the MBR automatically.




Focus on getting Vista running, then worry about Ubuntu.  You can't do more than one thing at a time! :-)
Hahaha, that's me :P I always want to do many things at one time ;)

Okay, I'll fix MBR first then uninstall Ubuntu.

Can I just delete the partitions where Ubuntu is installed after I fix my MBR or that's so bad solution? or that would create more troubles?

Thanks a lot :)

---

### Post by yeats on 2009-10-31
> Can I just delete the partitions where Ubuntu is installed after I fix my MBR or that's so bad solution? or that would create more troubles?

No, that will be fine to do, just as long as you don't accidentally delete something you need.  (Meaning, be sure to back up your files and settings before you do).

---

### Post by amjjawad on 2009-10-31
> **chrissharp123 said:**
> No, that will be fine to do, just as long as you don't accidentally delete something you need.  (Meaning, be sure to back up your files and settings before you do).

Don't worry, ALL my data on HD1 and I checked Disk Management (Windows) last night and made sure it can read the other partitions but I can't access them from My Computer, of course coz it's ext4 and I know that :)
I just want to make sure there's no problem to "delete" the partitions where Ubuntu is installed using Windows Disk Management?

BTW, I just fixed my MBR :D thanks a lot.
I just want to know HOW to get rid of the booting list? not a big deal but I'll be so happy to start my machine without pressing anything or choosing between Vista and Ubuntu :)

Thanks a lot!

---

### Post by Scott M. Sanders on 2009-10-31
I think just System > Administration > StartUp-Manager > Misc. > Uncheck "Show bootloader menu" should work.

---

### Post by amjjawad on 2009-10-31
> **Scott M. Sanders said:**
> I think just System > Administration > StartUp-Manager > Misc. > Uncheck "Show bootloader menu" should work.
That's under Ubuntu if I'm not mistaken, right?
But I need to get rid of Ubuntu (either by uninstall it or just delete the partitions using Disk Manager (Vista)) so can I still do that using Ubuntu?
I think it should be done using Windows but I forgot how to edit the booting list :S

---

