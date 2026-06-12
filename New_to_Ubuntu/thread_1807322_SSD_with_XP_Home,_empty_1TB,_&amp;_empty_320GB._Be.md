---
title: "SSD with XP Home, empty 1TB, &amp; empty 320GB. Best setup for dual Boot?"
date: 2011-07-18
forum: New to Ubuntu
---

### Post by Tuberocity on 2011-07-18
First off, I've looked for my answers here & elsewhere, but have not found anything 
relating to my particular setup. Here goes, and thanks so much for any help you may 
give.
I have XP Home on a Samsung 64GB SSD as my primary drive. I have 2 WD 
drives, one 320GB 5200rpm, and a 1TB 7200rpm-(SATA III set by jumper to 
SATAII as motherboard supports only SATA II) all are SATA II. The 1TB drive is a 
brand new refurb as the one I had took a dive, WD replaced it under warranty. It has 
not been formatted yet, but I intend to use this as storage for XP programs, video, 
music, and everything else to do with XP. Plan to format NTSC with 3 equal 
partitions, one for my wife, one for me, one for XP programs, etc.
I intend to do my first, & extremely newb install of 10.4 Lucid Lynx on the WD 
320GB drive with 2 partitions of 30-60gb for Ubuntu, and the rest for Ubuntu's 
programs, addons, storage etc.
Are my ideas on this sound? What other options would you suggest? I would like 
to fool around with some of the more technical programs for video, and music editing 
available on the Ubuntu platform. I realize the 5200rpm drive is not as fast, but I 
think it a better idea to seperate the two opperating systems for the least amount of 
future problems?
If the above sounds good, how should I begin? full Format the 1 tb NTSC, 
making sure the drive is good, then dismount the drive, leaving the SSD XP Home, 
and the 320GB empty, and also freshly formatted to make sure it is in top shape, 
then install Ubuntu, reconnect the 1 TB, and be on my way?
Any advice on this would be greatly appreciated as I have no idea where to start 
with this setup other than my logical ideas above, but my logic being that of a 
complete newb to Ubuntu, and for the most part dual booting in general, I could be 
way, way off? lol Thanks again
 
An Afterthought, should I try a 64bit install of Ubuntu? My xp is 32bit.
Also, as it seems there are problems with using ASUS boards, mine is an ASUS P5KPL-AM with an Intel E2200 processsor. again, thanks
 
P.S. My bios also supports booting from USB Flash drives, and I have a 4GB drive on hand if this is of any use?

---

### Post by wildmanne39 on 2011-07-19
Hi in regards to this.
> I intend to use this as storage for XP programs, video,
music, and everything else to do with XP. Plan to format NTSC with 3 equal
partitions, one for my wife, one for me, one for XP programs, etc.
I intend to do my first, & extremely newb install of 10.4 Lucid Linux on the WD
320GB drive with 2 partitions of 30-60gb for Ubuntu, and the rest for Ubuntus
programs, addons, storage etc.
This is what I recommend.
1. root 20 gigs in case you like to install a lot of programs.
2. home as large as you want it
3. swap about 2 gigs even if you have enough ram you will need about this much or more to suspend or hibernate ubuntu.
4. You can make a ntfs partition to put files on to share between windows and ubuntu.

If your system can run 64 bit then I would run 64 bit,I have for a few years now and I have never had a problem because of it.

Here is a guise on partitioning, and installing dual boot.
[http://members.iinet.net.au/~herman546/p22.html](http://members.iinet.net.au/~herman546/p22.html)

---

### Post by Mark Phelps on 2011-07-19
Personally, I have found you have less problems after Ubuntu installs, in multi-drive scenarios, if you have ONLY the Ubuntu drive connected during the installation.  This prevents such accidents as writing GRUB to the wrong MBR, overwriting MS Windows MBRs, etc.

After that, reconnect the other drives -- but continue to boot from the Ubuntu drive.  Then, open a terminal in Ubuntu and enter "sudo update-grub".  That will regenerate the GRUB menu and add entries for the other OS(s).

---

### Post by Tuberocity on 2011-07-19
Yes, I certainly don't want to damage the MBR of XP. lol Thanks for that advice. I will read more on GRUB, and backing up the MBR of xp before I begin. I knew from previous experience not to have all drives mounted, but hadn't thought about disconnecting the main (SSD w/XP) drive as well. Sounds logical to me.
     I edited above to add that I do have the ability to boot from a flash drive, checked last night to make sure, and I do have a 4GB flash drive if this is beneficial? I may do one of the live installs on this flash drive just to get a feel for Ubuntu.

---

### Post by wildmanne39 on 2011-07-19
> **Tuberocity said:**
> Yes, I certainly don't want to damage the MBR of XP. lol Thanks for that advice. I will read more on GRUB, and backing up the MBR of xp before I begin. I knew from previous experience not to have all drives mounted, but hadn't thought about disconnecting the main (SSD w/XP) drive as well. Sounds logical to me.
     I edited above to add that I do have the ability to boot from a flash drive, checked last night to make sure, and I do have a 4GB flash drive if this is beneficial? I may do one of the live installs on this flash drive just to get a feel for Ubuntu.
Hi, I like the flash drive method, I have used it and it run almost as fast as having ubuntu installed on the hard drive and it is a great way to test ubuntu before you install it.

---

