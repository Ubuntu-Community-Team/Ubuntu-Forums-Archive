---
title: "Ubuntu/Win XP Dual Boot with Acronis"
date: 2009-04-08
forum: New to Ubuntu
---

### Post by TAllen013 on 2009-04-08
I'm completely new to Ubuntu, but I am trying to make the transition.  I'm currently planning a dual boot configuration with my current Win XP and Ubuntu 8.10.

I was thinking about purchasing Acronis Imaging Utility for the backup (of current Win XP) that it recommends you perform before the Ubuntu installation.  (And I would also like to use it in the future dual boot system as well.)

I'm wondering if anyone currently uses this setup?  Is it great?  Horrible?  Hell, does it even work?  Any feedback would be appreciated.

I'm particularly worried about a recovery feature that Acronis has (which I believe involves the computer's boot-up), does this cause any problems with the (?)GRUB(?) boot loader that Ubuntu uses?

Thanks in advance for any responses.

---

### Post by fabricator4 on 2009-04-09
> **TAllen013 said:**
> I'm completely new to Ubuntu, but I am trying to make the transition.  I'm currently planning a dual boot configuration with my current Win XP and Ubuntu 8.10.

I was thinking about purchasing Acronis Imaging Utility for the backup (of current Win XP) that it recommends you perform before the Ubuntu installation.  (And I would also like to use it in the future dual boot system as well.)

I'm wondering if anyone currently uses this setup?  Is it great?  Horrible?  Hell, does it even work?  Any feedback would be appreciated.

I'm particularly worried about a recovery feature that Acronis has (which I believe involves the computer's boot-up), does this cause any problems with the (?)GRUB(?) boot loader that Ubuntu uses?

Thanks in advance for any responses.

You can download the PDF instruction manuals for Acronis products, which should help you decide if the product will do what you want.  Two things stand out like searchlights when I skimmed the True Image Home 2009 document: The software runs under windows, and it does not include support for ext4 partitions.

ext4 will be available in Jaunty.  It's a worthwhile upgrade because it's up to two times faster on some operations, and generally much faster overall.

There's also nothing you cant do yourself that this package provides.  Personally, I prefer to take control of my own backups, rather than rely on a piece of Windows software that may or may not know where my most important data is kept (on my (currently) ext3 partition of course).  Also, I like to make sure all those conf files in etc and .gconf are backed up.  I've spent too long configuring this thing to go through all that again.  :-)

Chris.

---

### Post by kaibob on 2009-04-09
I use True Image, and it works fine for me. I use it to backup a drive with WinXP (NTFS) and Hardy (EXT3) dual-boot installs. I've restored the drive and individual partitions on hundreds of occasions without incident.

There was a problem with the inode size that is used in a clean install of Intrepid, but Acronis has reported that this has been fixed. Do a search of this forum on the words, acronis inode, to get more information on this.

I did not install the automatic recovery and backup options.

You can download a trial version from the Acronis site. This may be a good idea, as some people do have significant problems with True Image, and the latest version has been even more problematic than other new versions. 

Have a look at the True Image forum:

[http://www.wilderssecurity.com/forumdisplay.php?f=65](http://www.wilderssecurity.com/forumdisplay.php?f=65)

To learn more, review the True Image manual at:

[http://www.acronis.com/homecomputing/download/docs/](http://www.acronis.com/homecomputing/download/docs/)

BTW, the manual shows support for the following file systems: FAT16/32, NTFS; Ext2/Ext3, ReiserFS, Linux SWAP. So, it would appear that EXT4 is not presently supported.

---

### Post by Dazed_75 on 2009-04-09
It is also very interesting to note that Acronis can not just save images of partitions, but can also mount those images so one can retrieve individual files from within a saved and compressed image.  This may not be so surprising in itself since Acronis also lets you make a bootable recovery CD and it turns out the recovery CD boots into linux and runs a Linux version of Acronis True Image with some (unidentified) limitations.  I have not had time to explore this yet.

---

### Post by kaibob on 2009-04-09
> **Dazed_75 said:**
> It is also very interesting to note that Acronis can not just save images of partitions, but can also mount those images so one can retrieve individual files from within a saved and compressed image....

I didn't mention this, but I agree that the ability to restore individual files or folders is a nice option. I separately backup my home directory, but a  while back I had to get a copy of a configuration file from the /etc directory and got it from my last true image backup image. Only a few saves like this make the software worthwhile.

---

