---
title: "wifi, mounting, permanent USB,..."
date: 2010-01-29
forum: New to Ubuntu
---

### Post by AndresM on 2010-01-29
Hello All, just to say that before I posted this I have tried googling and several ubuntu forum links. It's really impressive on how commited I am with this, i would have normally given up several weeks ago.

Details of my machine: it&#347; an laptop ACER aspire 1360. I installed ubuntu 9.10 but I then considered since it was an old machine it would run smoother with xubuntu so I wrote ```
sudo aptitude install xubuntu-desktop 
``` on the terminal to change. after some tweaking with the display I'm basically in the same place I started with UBUNTU


[LIST=1]
[*]How would I go around and have ubuntu (or xubuntu) remember my wireless password and connect automatically to my preffered network without asking?
[*]Wifi seems to work at random sometimes I just need to turn on the PC, it will ask for the pass and it will connect, other times It will ask me around 5 times, it will disconect, I will then choose my network from the list (it always detects all the networks around) and then attempt to connect another 5 times and then again disconnect... I sometimes go through this 1 time or 5 times and it will connect but it will then randomly disconnect.
[*]I had a USBstick plugged in once but I forgot to unmount it before unplugging. This then resulted that I couldn't use the USBstick. I then had to go and use windows xp to format the stick to get it to work.
[*]OK, this last one if for extra points: I finally know the name for it I want to have a persistant usb thumb drive (usb stick). Basically a customizable live cd on a usb stick. I found several guides and several pages as to how to get this going the best option I found was [http://rudd-o.com/new-projects/portablelinux](http://rudd-o.com/new-projects/portablelinux) though some people told me that my best option is to plug in the USB at startup and using the instalation CD install it on the USB drive and then install some sort of WUBI? there is another web page [http://www.pendrivelinux.com/](http://www.pendrivelinux.com/) that does something similar to Rudd-o. I'll go now to explain what I want from this portable linux:
[LIST=1]
[*]I want to use it with my work laptop that runs on XP
[*]I want to be able to access the XP files read and copy at least (added problem, HDD is encripted I do hold the password, I didn't steal it :) )
[*]I want to be able to write on the XP files
[*]If the above doesn't work at least I want the USB stick to be available both on Ubuntu and XP
[*]I want USB stick to remember all the configurations and new files I did the next time I use UBUNTU. (this is what I think means for it to be persitant)
[/LIST]
 
[/LIST]
Thank you for your patience. My work computer is a Dell latitude laptop.

---

### Post by Cheezespread on 2010-01-29
(Ubuntu)1. When you click the network icon on the panel available  , you will have option to " edit connections" where you can specify the wifi connection and password for the same . I assume you meant this.

---

### Post by anaconda on 2010-01-29
1. In the edit connections (from above post) there is a uncheked place "allow all users to use the connection" (or something like it.
Just check that, and it wont ask the password again. (yeah. I know not logical place for it)

But I solved that and some other problems by installing wicd. (it replaces and  uninstalls networkmanager)

2. wicd would probably solve this too

PS. if you dont like wicd, then you can just reinstall networkmanager..

---

### Post by AndresM on 2010-01-29
Thanks for the help! I did the edit coniguration but it now attempts to connect at the beginning but then seems to quit entirely. I try to un tick the box but its now shaded away. I'll try some more tomorrow. specially that wicd you mentioned. Is it in the repos? 

Anybody got ansers on the other issues?

---

### Post by AndresM on 2010-01-30
OK, I'm trying out what darkod proposed here:

funny i didn't see this one before it seems exactly what I need.

[http://ubuntuforums.org/showthread.php?t=1373046](http://ubuntuforums.org/showthread.php?t=1373046)

It is a bit scary so I triple checked that I had sdb chosen and not sda. (my wife would kill me if I lost all the family photos and more...)

---

### Post by AndresM on 2010-01-30
OK, it seems to work, I just did the victory dance. yay! I have read there where some issues regarding the flashdrive eventually breaking, something to do with writting and rewritting information to it. I don't quite understand it. 

I'm now looking for a way to be able to read files of the USB on windows as well. I'm guessing it will have to do with doing a fat32 partition on the usb. I don't know how to do it yet. any help would be great on that. My USB is about 7GB big 1GB of FAT32 should be more than enough.

BTW, wifi is still on, I did not need to install wicd. thanks for the tips above!

---

### Post by sgosnell on 2010-01-30
Windows is a little retarded in the filesystem department.  Linux will read Windows filesystems fine, but Microsoft can't be bothered to work with open-source filesystems.

Start up gparted, by System/Administration/Partition Editor, and in the top right corner of the window, select your USB drive.  The initial drive indicated there will be sda, but use the triangle and select the proper drive, probably sdb, but maybe not, depending on what else you have connected at the time.  Just make sure you get the correct drive.  You'll need to resize one of the existing partitions, so decide which one.  I suspect you only have two logical partitions - one for the OS, plus a swap.  Don't bother trying to do anything with the swap, just select the main partition, unmount it, then right-click and select resize/move.  Drag the right end to the left, to make enough room for what you need.  Then right-click on the resulting unallocated space, and select to add a new partition.  Format it as FAT32, then click on Apply, and it will all be done at once.  Just be aware that Windows often can't even see partitions other than the first one, so this may all be a waste of time and effort.

---

### Post by AndresM on 2010-01-31
OK, wifi seems to be acting stubborn again so i went for wicd. It took 3 or 4 attempts but it finally connected.

---

### Post by AndresM on 2010-02-02
> **sgosnell said:**
> Windows is a little retarded in the filesystem department.  Linux will read Windows filesystems fine, but Microsoft can't be bothered to work with open-source filesystems.

Start up gparted, by System/Administration/Partition Editor, and in the top right corner of the window, select your USB drive.  The initial drive indicated there will be sda, but use the triangle and select the proper drive, probably sdb, but maybe not, depending on what else you have connected at the time.  Just make sure you get the correct drive.  You'll need to resize one of the existing partitions, so decide which one.  I suspect you only have two logical partitions - one for the OS, plus a swap.  Don't bother trying to do anything with the swap, just select the main partition, unmount it, then right-click and select resize/move.  Drag the right end to the left, to make enough room for what you need.  Then right-click on the resulting unallocated space, and select to add a new partition.  Format it as FAT32, then click on Apply, and it will all be done at once.  Just be aware that Windows often can't even see partitions other than the first one, so this may all be a waste of time and effort.

Thanks for the help! I'll try to give it a go this weekend. 

wicd failed on me, but silly me I uninstalled it thinking that the networkmanager package was downoaded. Now I don't have anything and it won't reach the wireless. I'm sure the files have to be in my computer somewhere? surely there is no need to download the package again? I made sure to remove and not permanently remove (or I thought I did)

---

### Post by niffcreature on 2010-02-02
> **anaconda said:**
> 

2. wicd would probably solve this too

PS. if you dont like wicd, then you can just reinstall networkmanager..

i dont know where you guys are finding wicd. its not really in synaptic for me.

andresm, are you still working on those other issues?
-the thing about flash drives is that they can wear out faster than hard drives i think... im not sure. but theyre all rated to a certain number of rewrites.
-to be honest im not sure what you guys are talking about with accessing files on the usb drive with windows:
sgonsell you describe how to make a new partition that will be accessible from windows, but you describe how to do this while running from the flash drive, running in fact from the partition you need to unmount and resize, which is not possible...

the usb drive is int the EXT filesystem, whether its ext2,3,4. its NOT impossible for windows to read it, just look around for some software. i had a dual boot system where this worked flawlessly. im not going to point you to any specific software because i dont remember what i used... but its out there. 

as far as linux being able to access the windows files, did that just work out for you? i have inadvertently run into more than a few never ending threads about linux (not) working with windows disk encryption and network drives. i dunno what to tell you about that.

all in all sgonsel was trying to make things easier. you could forget all of what i recommend and just get an additional drive. would solve all your problems.

---

### Post by sgosnell on 2010-02-02
Remove is permanent.  Completely remove means removing configuration files in addition to program files.  I doubt network manager is still on your computer, but it might be in the apt cache.  You'll probably need to use ethernet to do the download, or you can download it via another computer and use a flash drive or similar to transfer the files.  Removing network manager is not a good idea.  Wicd is a poor substitute, IMO.

---

### Post by AndresM on 2010-02-04
I am able to run ubuntu on the work pc that is encripted but i didn't try to see the hard drive. As a newbie i opened places and didn't see the hdd so i googled some help. Found loads of stuff, im begining to see the problem: i have too much information and too many ways to solve it.

I think i didn't get wicd through snaptic i googled it and downloaded 

About damaging flash drive: my wifes pc is solid state, thats basically the same right? I've read around that v9.10 is ext4 and is safe for hdd. 

For future reference how can i uninstall a program without deleting?
Sorry i have ubuntu projects for weekends so feedback i give is slow.

---

### Post by sgosnell on 2010-02-05
sudo apt-get remove appname will uninstall programs, and sudo apt-get purge appname will get rid of config files also.  When you uninstall a package, you delete it.  If you don't want to delete it, don't remove it.

You can use any filesystem with any version.  9.10 works with ext4, but you can also install any other filesystem, including ext2, ext3, and whatever else you like.  You choose at install time, and it's also possible to convert after installation, but you have to be careful with that.  I doubt the drive was damaged by the filesystem, though.

@niffcreature:  No, I didn't mean to resize/repartition when booting from the USB drive.  You have to boot from another drive before you can unmount any drive and play with the partitions.

---

### Post by AndresM on 2010-02-06
Thanks for that sgnosnell. 
So if uninstalling it removes it how can i save the package if i want to recover it? Wicd and network manager cannot coexist for example.

Oh one thing i noticed but it might have been a glitch in my imagination. On my persistant usb instalation i was unable to install a program called gwyddion. Its on the snaptic pakages.
Again, thanks for the help.

EDIT:

> Oh one thing i noticed but it might have been a glitch in my imagination. On my persistant usb instalation i was unable to install a program called gwyddion. Its on the snaptic pakages.

OK, I was imagining things. I was able to install Gwyddion.

---

### Post by AndresM on 2010-02-06
Ok connecting a cable directly doesn't do the trick: i can't install nwtwork manager because i can't down load the package. Above was mentioned that i could download the pakage in amother cpmputer and copy it to this one how do i download without installing?

EDIT: I Found where I could download it from [http://ftp.gnome.org/pub/GNOME/sources/NetworkManager/](http://ftp.gnome.org/pub/GNOME/sources/NetworkManager/) but the folder 0.7 (the latest to date) has several files, I don't know which one to down load. Plus I've seen that it has something like a dependency (?) file so I'm guessing I need to down load two packages. 

ADDED Question: Once I've downloaded it, do I just right click and say run with... what? or does a double click do the trick. I guess I can wait and see for this one.

---

### Post by AndresM on 2010-02-06
> **sgosnell said:**
> Windows is a little retarded in the filesystem department.  Linux will read Windows filesystems fine, but Microsoft can't be bothered to work with open-source filesystems.

Start up gparted, by System/Administration/Partition Editor, and in the top right corner of the window, select your USB drive.  The initial drive indicated there will be sda, but use the triangle and select the proper drive, probably sdb, but maybe not, depending on what else you have connected at the time.  Just make sure you get the correct drive.  You'll need to resize one of the existing partitions, so decide which one.  I suspect you only have two logical partitions - one for the OS, plus a swap.  Don't bother trying to do anything with the swap, just select the main partition, unmount it, then right-click and select resize/move.  Drag the right end to the left, to make enough room for what you need.  Then right-click on the resulting unallocated space, and select to add a new partition.  Format it as FAT32, then click on Apply, and it will all be done at once.  Just be aware that Windows often can't even see partitions other than the first one, so this may all be a waste of time and effort.

OK, I'll leave my old laptop (the acer with now network manager) in stand by for now.

I'm now picking up on what sgosnell mentioned above. Since the thumb drive is working nicely I don't want to mess with it. So I bought one of those nice seagate external portable harddrives (500Gb) and I'll give it a go. 
OK, gparted wasn't installed by default but I found it via the Ubuntu software centre. I opened it up checked some of the things sgosnell said above and realized that it finds my 3 drives: first finds the sda (windows Hdd) it's encrypted so the file systems is unknown, sdb (the thumb drive with ubuntu on it) ex4, extended (no idea what this is) and linux-swap (no idea what this exactly is but it's a known unknown: something like paging drive) and lastly sdc of the external HDD this I found is ntfs. it seems that Gpartition seems to not support ntfs by default (seen in view> file system support) and said it needed ntfsprogs. I looked it up the ubuntu software centre and I didn't find it, googled it and it seems it's on the synaptic package manager (system>administration synaptic package manager). After this ntfsprogs is installed it seems to be updated on the Gparted. 

[short break] Wow. I've never had so much fun with an operating system. Who needs games when I can mess with this?[/short break]

....
will continue on an edit.

OK, Really nice program that Gparted. I took the 500Gb ntfs extrernal drive I reduced the ntfs, thought this would be the best option so that windows recognizes it as sgosnell mentioned i might have problems. Then I created a fat32, ext2 and ext4. Why? as everbody here might say: because I can! So I reboot using windows and much to my surprise windows XP only recognizes drive H (the hard drive) as a fat32. I knew it wouldn't know what ext2 or ext4... but I was kinda hoping it would take the ntfs and maybe the fat32. 
BTW, the external hdd had some things installed from the shop. some stuff about registering... nothing useful but I left it. when I shrinked the ntfs drive and added the others everything was still there! I wouldn't take this for granted because it does give you warning saying you might loose data. 
Anyway. windows xp detected the fat32 that was on the sdc2 and completely ignored the ntfs that was on the sdc1. So I went back to ubuntu, changed the fat32 drive to ntfs and went back to windows. after windows going a bit crazy (like before but a little more) I was able to see the H drive empty, so again: it went directly to sdc2. By the way again: this coming and going from windows to linux is done by rebooting and going through the usb grub. really nice stuff! So I gave up and left it as fat32. I'll try with a desktop XP to see what that finds.

I hope the above helps people wanting to do similar things in the future. 

in other lines: I found out that the encription is done by becrypt [http://www.becrypt.com/emea/Downloads/encryption](http://www.becrypt.com/emea/Downloads/encryption) I innocently sent them an email asking them how to get access. It seems they have experience with linux. Let's see if they answer next week. 

So thank you guys for everything. I think most of my questions where solved. The only really important bit I want to understand is how to download an installer e.g. network-manager with one computer so that I can install is in another computer.

---

### Post by sgosnell on 2010-02-06
The network manager .deb file might still be in the cache.  Look in /var/cache/apt/archives and see what you can find.  If the package is there, you can install it with gdebi.  You can right-click on it in Nautilus and select open with gdebi package installer.  The cache may have been emptied, but it's worth a try.  If it's not there, download it with another computer and transfer it with a USB drive.  You can do it by installing it on the other computer and then copying the package from its /var/cache/apt/archives folder, or find and download the package.  You can find it [here](http://packages.ubuntu.com/karmic/i386/network-manager-pptp/download).

---

### Post by AndresM on 2010-02-07
i cannot be thankful enough. It seems that it's not on the computer anymore so I downloaded. I'll give it a go in a few minutes. 

As I mentioned before I tried the external hdd on the xp desktop at home and it detects with no problem the two drives (the ntfs and FAT32). I think it's an issue as how the shared drives work at the company I work for. 

I now have an new issue. before customizing my thumbdrive I actually tried it first on my desktop: it has a USB load option on the BIOS (most be something standard on new computers now, not only laptops?) The problem is i tried it today but i keeps loading windows I don't even get a glipse at the grub.... last night i did notice that the grub was attempting to update, since I was happy as how it was working I thought I didn't change anything but it seems I have. How do I correct this?

---

### Post by AndresM on 2010-02-08
> **sgosnell said:**
> The network manager .deb file might still be in the cache. Look in /var/cache/apt/archives and see what you can find. If the package is there, you can install it with gdebi. You can right-click on it in Nautilus and select open with gdebi package installer. The cache may have been emptied, but it's worth a try. If it's not there, download it with another computer and transfer it with a USB drive. You can do it by installing it on the other computer and then copying the package from its /var/cache/apt/archives folder, or find and download the package. You can find it [here]("http://packages.ubuntu.com/karmic/i386/network-manager-pptp/download").
 
OK I downloaded the package wanted but it then attempts to go to the internet to find another package it needs. No harm done: I have downloaded that package with the other computer, I didn't have time to do it but I intend to run/install that pagage first and then re-attempt to install the network manager (hopefully it will see that it's already installed. Sadly I ran out of time yesterday will try again today.

---

### Post by AndresM on 2010-02-09
OK, I downloaded and installed the pptp-linux package that network manager was fetching. (Ignoring the messages that said the same package was available online) 

I then installed the network manager. It finished installing but nothing happend. No internet, no link on the aplication> network menu, nothing after reboot. 

I have managed to make it work with my ubuntu thumbdrive using it now. and using an old SMC PCMCIA wireless card I had laying around. So it seems that if I reinstall the whole thing it just might work. But as some of you might have taken the hint by now I didn't want to get to that. I'd rather find out how to get it to work the hard way.

---

### Post by AndresM on 2010-02-09
Victory! slightly confusing but a victory none the less!

I feel like such a fool! On the package manager I can select a checkbox that says "download the pakage only" I download the network manager and the gnome networkmanager using my thumbdrive,
 I copy it to the computers hardrive, reboot, remove the thumbdrive. 
Let xubuntu start up. execute both packeges (first the network-manager then the network-manager-gnome). 
Make sure I have the PCMCIA plugged it. Restart. and viola! I'm posting in my favourte forum!

Now there was a slight hickup... the networkmanager takes it&#347; time to find the network and then pops up the message saying network disconected. But it is connected! the first time round I mendled with it and then it definately was disconected (applet changed). I then rebooted and there it was! I don't know if I should report it as a bug as I've been having such problems I don't know how much is my fault.

YES! I would consider this SOLVED. I don't know how to change it though...

---

### Post by AndresM on 2010-02-10
One last thing! before rebooting the last time I remembered to make network manager available at startup. That's changed on system or something startup aplications. Pretty self-explanitory.

---

