---
title: "To improve my ubuntu inside windows XP"
date: 2009-06-12
forum: New to Ubuntu
---

### Post by ram_ark on 2009-06-12
Hi,
I initially tried dualbooting my system which failed as my RAM was insufficient for Ubuntu.
Then using Sun virtual box, I successfully installed Ubuntu 9.04 inside my Windows XP 2002 Service pack 3 in the partition D of my hard disk which has in total 4 partitions.

C: FAT32 - Windows XP installed - 19.1GB Total size - 2.17 GB Freespace
D: NTFS - 19.1GB Total size - 12.00 GB Freespace
E: FAT32 - MP3 files - 19.1GB Total size - 5.02 GB Freespace
F: FAT32 - MP3 files and JPEG photos - 19.1GB Total size - 7.20 GB Freespace

My system config:
Intel Pentium 4 
2.93GHZ
504MB RAM
80GB Hard disk
DVD Drive: ASUS DRW-2014S1

Guidance needed:
1. How to change my ubuntu o.s settings to 32 bit instead of 16 bit
2. How to make my ubuntu read the other partitions so that i can import and hear music from E: or F: or view my photos from F:
3. How to make my ubuntu read or play or import from any DVD or CD from my DVD drive
4. Why is my mozilla speed slow in ubuntu inside windows

Once i am able to do all the above successfully, i would like to migrate totally from Win XP to Ubuntu or interested in dualbooting. Should i increase my RAM or are there alternate ways.
Thanks and Regards,
Ram

---

### Post by keplerspeed on 2009-06-12
I am very impressed that you could run xp with ubuntu in virtaulbox with half a gig of ram.. I did that with 1gig of ram and it was... slow!

Guidance:
1) Your ubuntu should be 32bit if you installed within virtualbox. I dont believe there is a 16bit ubuntu of current release.

2) You can share folders from the host OS (ie xp) with the guest OS (ubuntu). This can get tricky, so dual boot.

3) Once again, with virtualbox we need to mount the host cd drive. This can be done within virtualbox settings for the guest OS.

4) Everything will be slow in ubuntu within xp. Well, wont be very fast anyway.

You should have no trouble dual booting. I would highly recommend that you dual boot, and this shouldnt be any issue with the current RAM. 504MB ram is NOT insufficient for ubuntu. What issue did you have before with dual booting?

---

### Post by ram_ark on 2009-06-14
Hi Kepler,
Thanks for going through and being ready to help.
1. Attaching snapshots to better explain. (Pls refer the Zip file)
Where should i be making the necessary change so that the screen is full and not as shown.
2. 3.  4. Understand that dualbooting would be the best possible solution. 
.
I downloaded the iso for ubuntu 9.04 as given in the ubuntu home site. Checked winmd5sum and it was correct. Then i created my installation live cd as per the instructions given in the home site. Then i booted from this cd after restarting my computer. It worked fine till the screen that states the 5 options  (Try ubuntu without making changes, Install ubuntu, Check disc for defects, Test memory, Boot from first hard disk)
.
I chose the Install ubuntu option and the yellow curson ran from left to right suggesting installation from the cd. But at the end of it, it became a black screen with the white cursor blinking at the leftmost end of my monitor. I waited for 2 hours and then decided to take action. Only action i could take next was ctrl+alt+del
.
Could the problem be that my C, E and F partitions are FAT32 instead of NTFS
Appreciate your assistance once again.
Regards,
Ram

---

### Post by twright on 2009-06-14
Hi,
just a suggestion but you would probably be better off going with wubi instead of installing in virtualbox. Wubi is a small program included on the Ubuntu CD (wubi.exe) which allows you to install Ubuntu inside windows but use it independantly. This would probably fix most of your issues and be much faster considering your amount of RAM.

Good luck and welcome to Ubuntu :-)

BTW. Did you mean harddrive space in the first post rather than RAM? RAM would be a much bigger issue in VirtualBox than in a Dual Boot.

---

### Post by ram_ark on 2009-06-14
Hi,
It is RAM that maintain as the issue in running Ubuntu slowly inside the virtualbox. Because i opted to give entire 19+ gb of my D: to this virtual disk.
Seriously i want to dual boot and not run ubuntu inside windows.
Only then i trust i can evaluate/understand ubuntu's power better
Would u be able to suggest what is restricting this.
Please see my previous post for knowing what i claimed as the problems while booting with the live CD.
Thanks,
Ram

---

### Post by sim-value on 2009-06-14
Choose the Try ubuntu option ... from there you can install ...

---

### Post by ram_ark on 2009-06-14
Thanks.
Yes i did try that option but same result.
Only the blank black screen with a white cursor blinking on the left corner.
At that point, i feel even the system stopped reading my DVD drive where i inserted the live CD

---

### Post by twright on 2009-06-14
> **ram_ark said:**
> Thanks.
Yes i did try that option but same result.
Only the blank black screen with a white cursor blinking on the left corner.
At that point, i feel even the system stopped reading my DVD drive where i inserted the live CD

Then you will probably be best off runing wubi.exe from the live cd or using the alternative install cd

---

### Post by halitech on 2009-06-14
what do you have for a video card? (guessing on-board since you are showing 504meg of ram and it would normally be 512) Depending on the type of ram you are using, it might be a good investment to get another 512 or 1gig if you can swing it.

---

### Post by camper365 on 2009-06-14
Try the check CD for defects option on the boot screen. The CD may be defective.

---

### Post by theozzlives on 2009-06-14
I'd say alternate install, could be a video problem.

---

### Post by Bradtek on 2009-06-14
> **theozzlives said:**
> I'd say alternate install, could be a video problem.

Finally some good advice


But before going to the trouble of downloading/burning the alternate cd

Fire up the live cd again and when you get the menu (install etc)
Press F4 (I think) and you should be able to choose "Safe Graphics Mode"

Then try the install

IF that also fails, there ARE other options like adding parameters to the install command

With Wubi, the problem will still be there if/when the user wants to ditch windoze
so rather than offering wubi as a miracle cure for all problems, try to find the ACTUAL problem and fix it.

---

### Post by twright on 2009-06-15
> **Bradtek said:**
> 
With Wubi, the problem will still be there if/when the user wants to ditch windoze
so rather than offering wubi as a miracle cure for all problems, try to find the ACTUAL problem and fix it.
Except most problems of these nature seem to only affect the live cd (due to some graphical stuff and how it is booted).

---

### Post by Bradtek on 2009-06-15
> **twright said:**
> Except most problems of these nature seem to only affect the live cd (due to some graphical stuff and how it is booted).

So as I said, either try safe graphics mode, some parameter like vga=791
(cant think of others right now)
Or use the Alternate Install CD which even managed to install Xubuntu on my old Pentium 200 MMX

There is way too much fear mongering about partitioning and dual booting
Only those who don't back up and or can not follow simple instructions are in danger of losing anything.

If someone can't follow simple instructions then maybe they should reconsider installing a new and completely alien to them Operating System.

There is so much help available here, but when the first thing some noob suggests is Wubi, I groan and think about how even after using Wubi Ubuntu for a year or more, these people still can't partition a hard drive, which is a pretty basic operation.

---

### Post by twright on 2009-06-15
> **Bradtek said:**
> So as I said, either try safe graphics mode, some parameter like vga=791
(cant think of others right now)
Or use the Alternate Install CD which even managed to install Xubuntu on my old Pentium 200 MMX

There is way too much fear mongering about partitioning and dual booting
Only those who don't back up and or can not follow simple instructions are in danger of losing anything.

If someone can't follow simple instructions then maybe they should reconsider installing a new and completely alien to them Operating System.

There is so much help available here, but when the first thing some noob suggests is Wubi, I groan and think about how even after using Wubi Ubuntu for a year or more, these people still can't partition a hard drive, which is a pretty basic operation.
I do not use wubi myself (I have at least 8 computers of varying age setup and partitioned :-) . I also don't think there is much overlap between the programmer and noob communities) but it is simply the easiest and lowest risk way to install Ubuntu. Partitioning is very easy with Ubuntu and I did also suggest the alternative CD, but wubi is still a good option as it would not require another download and on a smaller harddrive putting Ubuntu in an existing partition helps managing space. Partitioning with the alternative is also a slightly more daunting task than wubi or the live cd.

Anyway, it is too early to start a flame war... hopefully either option is a good one

---

### Post by ram_ark on 2009-06-18
Thanks all for your suggestions and it seems i need more of them

1. I tried the F4 and Safe Graphics mode but it did not assist
2. I also checked the CD for errors and it said "Errors found in 14 files". Dont know how i can prevent these errors but whenever i burn a cd/dvd which i do using my ASUS DRW-2014S1 there is always unable to verify errors. Well this is not the thread to discuss that.
3. I checked my video card adapter which says Intel(R) 82915G/GV/910GL Express Chipset Family. 
Do i need to install some drivers

Thanks,
Ram

---

### Post by BandD on 2009-06-18
Try lowering the burn speed of the CDs you are creating.  Go for like x2 or even x1.  The slower the safer and less chance of data corruption.  If it still doesn't work, then try a different burning program with a low speed again.

Let us know.

---

### Post by twright on 2009-06-18
Hi,
the corrupted CD is probably the problem - try this to check the downloaded file (not just the CDs made from it):
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

you can also try installing from a usb via unetbootin if the CD installer keeps failing. There is much less chance of corruption this way. Also make sure it is a new disk you are using, old ones have a higher chance of failing.

---

### Post by xeticus on 2009-06-18
I'm running Ubuntu 9.04 in XP using wubi and it works great for me with only 512 ram. Wubi is much better if you can use that.

---

### Post by ram_ark on 2009-06-19
Hi,
Seems the problem might be because of below contributors:
1. Bad Live CD - Already did [HowToMD5SUM]("https://help.ubuntu.com/community/HowToMD5SUM") and it matched perfect. Also had burnt it at the lowest speed in my DVD writer but yet errors
2. Video card
3. Hard disk errors
This weekend will try to build the alternate cd and will try and let you all know.
Meanwhile the community has given me more hope to try ubuntu and realise its true potential. Hats off to you guys for the same.
Regards,
Ram

---

### Post by ram_ark on 2009-06-20
All,
Today i downloaded and created the alternate cd and checked the md5sum which was also correct
Then i burnt the iso and created the alternate cd
When i tried booting using the same it said
./dists/jaunty/main/binary-i386/packages.gz file failed the md5checksum verification. Your Cd-rom or this file may have been corrupted
.
Any suggestions on how to proceed now. Think the problem is with burning the iso to cd using my ASUS writer.
Thanks,
Ram

---

### Post by BandD on 2009-06-21
Does your machine support booting from USB devices?  If so, you could try creating a live USB stick and booting from that...

---

### Post by twright on 2009-06-22
Yes, if the CD is burned incorrectly then regardless of what version you use it won't work. I suggest you either borrow another computer to burn it from (as yours does not seem to be burning correctly) or use the installer from usb.

---

### Post by Miljet on 2009-06-22
If the problem is a bad CD drive, as I suspect, burning the CD on another machine won't entirely cure the problem. While that will give him a good disk, the installed drive will probably introduce read errors also. That said, it is still a good suggestion just to get a known good disk to work from.

---

