---
title: "Guidance requested for moving out of XP and installing Ubuntu"
date: 2011-03-17
forum: New to Ubuntu
---

### Post by RLCGRN on 2011-03-17
Hello!
I'm only a computer user, like most people are only vehicle users - not much knowledge or ability to adjust what's going on "under the hood".  I'm ready to install Ubuntu for a full time shot after tiring of the weird behavior Windows can have and fear of malware.  I've run Ubuntu 10.04.01 using the Live CD to be sure I liked it.  I am scared of the learning curve because Ubuntu does things in a pattern differently than I have become accustomed to from using Windows for 22 years, but this forum, because of the people here, is a GREAT asset.  I've downloaded a copy of the "Ubuntu pocket guide" to get me started.  My specific questions I couldn't find by searching the  forum are these:

A)
Yesterday I bought a Seagate FreeAgent GoFlex 500Gb portable hard drive to back-up and save all my documents and some programs to.  Will this device be recognized by Ubuntu - that is, once my files are there and I wipe off XP and clean install Ubuntu, will I still have access to them when I plug the USB cable back into it's slot?  Will it need to be formatted to comply with the format necessary for Ubuntu (which I think is ntfs - right?)

B)
I have 3 programs that I will want to continue using (everything else seems to have a Linux counterpart for free):
Autocad 2002 (I use it for learning and practice - not productive output)
Google Sketch-up
National Geographic TOPO 4.0 mapping software
How can I best handle the continuing use of these programs? A Virtual machine? Wine? A Dual boot (I think I sort of understand this concept - how is it done?)?

C)
Where do I even begin to learn to understand what's going on "under the  hood" and become knowledgeable about using the command line?

D) I'm also thinking Mythbuntu seems like it may be a good way to go since I'd like to record from Comcast shows I miss because I have to go to bed or I'm out and about.  Your thoughts?

E)
In the rare event I decide to stick my tail between my legs and crawl  back to Windows, how do I back up programs to my portable hard drive  that I will want to resume using?

Thanks to all in advance!

---

### Post by charlie_b on 2011-03-17
Congratulations for taking the leap into a bigger and better software universe.

Regarding B):
CAD is one area where Linux users have missed out to an extent. AutoCAD isn't available for Linux, nor was Sketch-up last time I looked. However I'm pretty sure both of them would work just fine under WINE, and a virtual machine is also a valid option for them both. There is another CAD package called Draftsight which has some big raps on it, and a Linux version is supposed to be available sometime soon.

As regards the mapping software, I haven't heard of the package you mentioned, but there are a number of excellent GIS packages available for Ubuntu. The best one in my opinion is GRASS, which is available in the repositories. It is long established and very powerful; though there is a lot to learn before using it properly.

Hope this is useful to you.

---

### Post by TeoBigusGeekus on 2011-03-17
A) You can test it with the live cd. Most probably you won't have any problems. 
There isn't a "necessary format for ubuntu"; you can use any format you like, but ntfs is preferable so that the hd is recognized by both windows and ubuntu.

B) I think a virtual machine would be ideal in your case.

C) A good [book]("http://sourceforge.net/projects/linuxcommand/files/TLCL/09.12/TLCL-09.12.pdf/download") I always recommend.

D) Never used it; can't help you with that.

E) You wouldn't back up programs from ubuntu to use in windows cause windows cannot run linux software (and vice versa). You could though backup your important files (documents, songs, movies, etc.) with your hd and reuse them in windows.

Welcome aboard!!!

---

### Post by pricetech on 2011-03-17
I'd recommend dual boot to start with.

Defrag windows, boot to the Ubuntu live CD and use gparted to resize your windows partiton and reboot into windows, letting chkdisk run.  It may run more than once, so reboot as many times as necessary to make windows happy.

Boot to the Ubuntu CD and install on the space you made for it.

Have fun.

---

### Post by RLCGRN on 2011-03-17
> **pricetech said:**
> I'd recommend dual boot to start with.

Defrag windows, boot to the Ubuntu live CD and use gparted to resize your windows partiton and reboot into windows, letting chkdisk run.  It may run more than once, so reboot as many times as necessary to make windows happy.

Boot to the Ubuntu CD and install on the space you made for it.

Have fun.

How do I use this "gparted"?  I *think* i understand the rest.

---

### Post by RLCGRN on 2011-03-17
> **TeoBigusGeekus said:**
> A) You can test it with the live cd. Most probably you won't have any problems. 

See what I mean - Great board!  An elegant solution!

---

### Post by RLCGRN on 2011-03-17
> **TeoBigusGeekus said:**
> A)

C) A good [book]("http://sourceforge.net/projects/linuxcommand/files/TLCL/09.12/TLCL-09.12.pdf/download") I always recommend.

I downloaded it. If number of pages alone is an indication of usefulness, its superb.  I have mucho reading to do, it seems.  Thank you!

---

### Post by chrinabuntu on 2011-03-17
I also think instead of wiping Windows out completely right away, go ahead and dual boot for a while. The partitioning thing is pretty easy...the Ubuntu installation screens will guide you thru it. It will ask you if you want to have Ubuntu wipe out everything and install on the whole hard disk...or do you want to run it alongside Windows and select between the two at startup. You tell it you want to run it alongside and it does everything for you. 

Like someone else said, you could also try it from the live CD, but nothing you do will be saved or anything...so I think it would be good to dual-boot. That way you can also boot to Windows when you want to use those Windows programs you like. This is what I still do...just because I need Windows for certain stuff like DreamWeaver, Flash and mainly PhotoShop. I finally ventured into the world of Wine to try it that way, but it isn't quite the same for me. Easier to just boot to Windows on PhotoShop days...and use Ubuntu for everything else.  ;O)

You can pretty much find everything you need here too...regarding command line stuff. So much information!!  Welcome!  

Chris in the Q

---

### Post by waynefoutz on 2011-03-17
Autocad clone...Draftsight

[http://www.omgubuntu.co.uk/2010/09/free-autocad-clone-draftsight-coming-to-linux/]("http://www.omgubuntu.co.uk/2010/09/free-autocad-clone-draftsight-coming-to-linux/")

Instructions on how to install on 64bit are on the linked page, but I couldn't get it going on 64 bit Lucid. 32 bit version it will work fine.

---

### Post by Ditchdoc7893 on 2011-03-17
I also have to agree with the recommendation to use a dual boot configuration to get yourself started and somewhat comfortable with Ubuntu, as this was the way I started to begin with on my monster desktop and then took the plunge to do a full install on my netbook that I use daily.  I have to say that I love it.  The learning curve is not bad and ifs really fun to learn so many new things.

To address E) of your post, if you were to decide to go back to the dark side (I'm going to bet on highly unlikely if you're really interested in learning Ubuntu and Linux), the best way I can tell you to go about backing up your stuff is to save ALL the files you need to absolutely keep on either a separate hard drive, flash drive, or usb drive.  As for programs, what I have always done in the past when I've done reinstall jobs is to know each program that I need (write it down, make a note, whatever) because trust me, if you just try to remember, you'll forget all of them.  Most of the things I use are programs that are free to download or that I have a license key that can be easily re-downloaded and re-installed.  So if you have license keys, write them down as well so that you can easily reload all your stuff.  The all important part of going back would be to make sure that you have system restore disks or an OEM disk for the version of the dark side that you ascribe to.  

So, have fun learning Ubuntu!  Its a really fun system to work with.  Best of luck to you!

Ryan

---

### Post by RLCGRN on 2011-03-19
Had a problem during install.
The install had an error with partitioning the drive for dual boot.  I also learned that I already have two operating systems on my hard drive: Windows Media Center edition XP and Windows NT/2000/XP.
I had previously thought they were one and the same.  Is this why I had an error?  After being alerted to the error, Ubuntu only gave me the option of a full Ubuntu install, wiping out XP.  I quit the install and am currently running on the Live CD.  What's my next step  to get this dual booted?  Wipe the Media Center off?  How?
Thanks!

---

### Post by RLCGRN on 2011-03-19
Well, I just shut down the computer and tried installing Ubuntu again.  The setup went ok, however i am getting no option to choose Ubuntu at computer start.  I get the Compaq title screen (it's a Compaq computer), then windows begins loading.  Nothing about being given the option of choosing which OS I want to use.  As an aside, my brand new 500GB usb hard drive is only registering as 245GB total capacity under "my computer".  What the ??
Your input, please!

---

### Post by YfoMp5QBh2 on 2011-03-19
So does it just boot straight into Ubuntu now? Sounds like half of the drive is partitioned still to one of the Window's OS and the 240gb partitioned to Ubuntu. Thats prob why it only shows half of the full HDD capacity.
 
Check to make sure nothing is on the other partition.

---

### Post by RLCGRN on 2011-03-19
> **spadge_2356 said:**
> So does it just boot straight into Ubuntu now? Sounds like half of the drive is partitioned still to one of the Window's OS and the 240gb partitioned to Ubuntu. Thats prob why it only shows half of the full HDD capacity.
 
Check to make sure nothing is on the other partition.

No, it only boots up Windows.  I only installed Ubuntu onto my C: drive - during install the process divided half of the drive for Windows, half for Ubuntu.  My portable USB drive only contains my copies of needed files as a backup; it's the one that registers as only 245GB when it's suppesed to be 500GB.

---

### Post by Ditchdoc7893 on 2011-03-19
This is the exact reason that I chose to install each OS on a separate HD and then choose which I wanted to boot up through the boot menu.

---

### Post by RLCGRN on 2011-03-19
How can I even get started learning this os when I can't even get it booted?
I've searched "dual boot" and I come across a bunch of stuff about gparted and MBR, but I'm clueless to follow those directions.

---

### Post by kroq-gar78 on 2011-03-19
I'm no expert, but I think GRUB didn't install correctly. Maybe somebody can help you there. Rather not mislead you by giving some possibly false directions as I'm not to familiar as to how to install, update, etc., but I think GRUB didn't install.

---

### Post by RLCGRN on 2011-03-19
> **kroq-gar78 said:**
> I'm no expert, but I think GRUB didn't install correctly. Maybe somebody can help you there. Rather not mislead you by giving some possibly false directions as I'm not to familiar as to how to install, update, etc., but I think GRUB didn't install.

That's kinda' what I thought, but I'm not versed in these matters.  Now I am just waiting for someone who can identify this problem and guide me to a solution.
I may make a new post with my issue as title to be sure I am seen by the experts.

---

### Post by Dutch70 on 2011-03-19
First thing is to take your time & not to freak out when something doesn't go perfectly. I know from experience that's easier said than done, but it's also very important. Sometimes it's to be expected when installing a new OS. These are usually just bumps in the road. 

Please boot into the live cd, open Gparted and take a screenshot of your partitions. attach it to your next post using the paper clip in the toolbar. 

Along with the pic. Please post the output of the following command between code tags. Using "#" in the toolbar.
That's a lower case L in the command.
```
sudo fdisk -l
```

---

### Post by Dutch70 on 2011-03-19
I just realized you started the other thread, so just post what I requested above in the other thread.

---

### Post by n4pgw on 2011-03-19
> **RLCGRN said:**
> Hello!
I'm only a computer user, like most people are only vehicle users - not much knowledge or ability to adjust what's going on "under the hood".  I'm ready to install Ubuntu for a full time shot after tiring of the weird behavior Windows can have and fear of malware.  I've run Ubuntu 10.04.01 using the Live CD to be sure I liked it.  I am scared of the learning curve because Ubuntu does things in a pattern differently than I have become accustomed to from using Windows for 22 years, but this forum, because of the people here, is a GREAT asset.  I've downloaded a copy of the "Ubuntu pocket guide" to get me started.  My specific questions I couldn't find by searching the  forum are these:
Been there - Done that!!  Congratulations!  I started exactly the same way.  (two years ago)
> 
A) 
Yesterday I bought a Seagate FreeAgent GoFlex 500Gb portable hard drive to back-up and save all my documents and some programs to.  Will this device be recognized by Ubuntu - that is, once my files are there and I wipe off XP and clean install Ubuntu, will I still have access to them when I plug the USB cable back into it's slot?  Will it need to be formatted to comply with the format necessary for Ubuntu (which I think is ntfs - right?)
That is the drive I started with, and still use today.  I just formatted it and installed it on my server as additional storage. 

When I started, I removed the drive cables to my internal drives and installed Ubuntu 8.x onto the USB drive.  I configured my system to boot off the USB device first.  Later, when it upgraded, GRUB found my local drives and added them to the list. For several months, I booted from my USB drive.  Later, I installed a drive in my desktop and moved the system over with no complications.

B)
Sorry, I don't use these products, but I have been testing virtualbox and it seems to run windows programs very much better than Wine.  
> 
C)
Where do I even begin to learn to understand what's going on "under the  hood" and become knowledgeable about using the command line?
I am learning that right now.  I installed Server last weekend and have been using the command line from my workstation to configure and control it.  Since I haven't learned how to use vi, I use gnome/gedit to edit my files until I learn the other editor.
I downloaded the pdf manual and print out sections I am learning at any given time.  I also created a check list of things I want the server to do.  Then I choose one item and learn how to do it, or stop when I can't (as in booting to the command prompt instead of gnome.)  I either check it off or move it to a second list where I will seek help later.
> 
D) I'm also thinking Mythbuntu seems like it may be a good way to go since I'd like to record from Comcast shows I miss because I have to go to bed or I'm out and about.  Your thoughts?

Great product.  I just looked it up and it looks interesting.  I'll have to try a live version for a while and see how it works.  I am interested in adding an entertainment computer later this year anyway. Thanks.> 
E)
In the rare event I decide to stick my tail between my legs and crawl  back to Windows, how do I back up programs to my portable hard drive  that I will want to resume using?

Thanks to all in advance!

Check out clonezilla.  It is a linux package that can clone hard drives.  It doesn't like one of my internal drives with dings in it, but I have used it a lot in the past to move from one drive to another without problems.  

You are welcome.  This is my first opportunity to help, for what little help that might be.  ;)
buck

---

