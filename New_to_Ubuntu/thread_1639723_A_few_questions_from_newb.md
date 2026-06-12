---
title: "A few questions from newb"
date: 2010-12-07
forum: New to Ubuntu
---

### Post by ULAMSS5 on 2010-12-07
Good day to all, I plan to Install Ubuntu onto my laptop(currently a Vista), but as the saying goes,"measure twice, cut once", I shall clear up any newb doubts before I take action.

Firstly, I can't download Ubuntu from [http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download) DAP will simply not download it, and leave it as a 0kb file which it claims to be completed. After disabling DAP, using Firefox's default download, it managed to download 636kb, subsequently 138mb before getting cut off. I seem to get randomly disconnected from the server.(Grr stupid Microsoft and its bugs):( What alternatives do I have?

Secondly, I plan to move about 100GB of videos(mostly .mkv) into the Ubuntu OS from Vista. Will I be able to do that internally(without a external hard disk + rebooting into different OS)?

Thirdly, I plan to replace Vista with XP in a few weeks, after moving of personal files into Ubuntu. XP shall be for games that don't work in Ubuntu. Will that be troublesome/doable(e.g. will it affect the Ubuntu side of my hard disk?)

Fourthly... just kidding there is no fourth, just some chatter. Is it just me or does windows computers seem to have some sort of virtual decomposition process going on that causes the computer to just randomly inherit bugs, laziness and stupidity after a few months of use?

[IMG]http://www.hollow-hill.com/sabina/images/serious-cat.jpg[/IMG]
...nah jk. No, really.

---

### Post by sikander3786 on 2010-12-07
I think that might be a problem with your ISP or your connection is dropping (??). Anyhow, grab a torrent here.

[http://www.ubuntu.com/desktop/get-ubuntu/alternative-download#bt](http://www.ubuntu.com/desktop/get-ubuntu/alternative-download#bt)

You'll need a bittorrent client like utorrent or bittorrent to download it.

I hope you know how to burn that image to disc or USB drive. If not, post back.

If you leave Vista as it is and install Ubuntu to another partition, you'll definitely be able to mount Vista partition under Ubuntu and then extract data from that (Linux supports NTFS partitions).

Later, when you plan to install XP, it would override Grub (Ubuntu bootloader) and you'll need to re-install Grub in order to dual boot both the OS. We'll definitely guide you then :-)

At the moment, I would just recommend to download Ubuntu, burn it to disc and keep this thread open. Keep posting and we'll keep trying to help ;-)

---

### Post by clhsharky on 2010-12-07
ULAMSS5

All ways backup personal data before working on partitions and installing OS.

Sharky

---

### Post by mastablasta on 2010-12-07
and don't forget to defrag the disk before resizing partitions.
 
and i suggest you first try a live session that won't make any changes ot your current system to see if your computer is actually ubuntu compatible.

---

### Post by julio_cortez on 2010-12-07
> **clhsharky said:**
> ULAMSS5
All ways backup personal data before working on partitions and installing OS.
SharkyI have to agree on this. In the 99% of the cases nothing will happen to your data if you install Ubuntu in a dual boot side by side with Windows.. But better safe than sorry: I'd rather spend an unnecessary hour copying data to an external drive before installing Ubuntu than feel sorry for the data if something goes wrong and I didn't make a backup.

Other than that, Windows partitions can be seen and mounted within Ubuntu but I'd rather avoid messing with the Windows filesystem with Ubuntu. I much prefer a shared "Data" partition (of course it has to be either FAT32 or NTFS but I'd go for the latter) to keep mounted 24/7 and to use as data sharing between the OS's, and avoid mounting the Windows filesystem (the C:\ disk) at all.

---

### Post by ULAMSS5 on 2010-12-08
Ah thanks for all the replies. I think it was a firefox problem since i managed to download ubuntu safely and quickly using google chrome and its default download manager. To be on the safe side, I'll wait another 2 weeks to get my hands on some external hard drives to backup my files. I'll leave Ubuntu empty for now. Re-installing Grub doesn't sound too troublesome, so I'll go ahead with my plan of switching Vista to XP, then re-installing Grub
[IMG]http://encefalus.com/wp-content/uploads/2009/02/happy_lolcat.jpg[/IMG]

---

### Post by ULAMSS5 on 2010-12-09
DISASTER STRIKES! Well not really a disaster. I downloaded the Ubuntu 10.10 AMD64(yes, my laptop has the AMD64x2 labels on it). I used USB installer to put it into my empty 2gb thumbdrive, everything went fine and etc, no errors. then i ran "wubi.exe", again all went smoothly with no errors, then i have tried both manually and automatically restarting(i omitted the "help me boot from disk" option because i was using a thumbdrive). In both cases, after choosing to boot from my USB drive, i get the message "No operating system found" or something like that. What should I do?

---

### Post by sikander3786 on 2010-12-09
> **ULAMSS5 said:**
> DISASTER STRIKES! Well not really a disaster. I downloaded the Ubuntu 10.10 AMD64(yes, my laptop has the AMD64x2 labels on it). I used USB installer to put it into my empty 2gb thumbdrive, everything went fine and etc, no errors. then i ran "wubi.exe", again all went smoothly with no errors, then i have tried both manually and automatically restarting(i omitted the "help me boot from disk" option because i was using a thumbdrive). In both cases, after choosing to boot from my USB drive, i get the message "No operating system found" or something like that. What should I do?
Make sure you've selected proper boot device under Bios menu. Sometimes, USB drives seem to appear under HDD menu in Bios. If so, bring your USB to the top of that list.

If that doesn't work, check the downloaded image for defects.

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

If ok, burn it using unetbootin.

[http://unetbootin.sourceforge.net](http://unetbootin.sourceforge.net)

---

