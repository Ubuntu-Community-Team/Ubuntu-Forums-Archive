---
title: "stuck booting 9.10"
date: 2010-01-07
forum: New to Ubuntu
---

### Post by bnhrobotics on 2010-01-07
My desktop running Ubuntu 9.10 is stuck booting. The last thing it says is:

Verifying DMI Pool Data..........
Boot from CD/DVD :
_

There is no CD/DVD in the drive. Not sure why it says CD/DVD.. but it has said that on boot and booted fine several times after I upgraded earlier this week. Any idea whats going on and what I should do to fix it? Thanks

---

### Post by Buuntu on 2010-01-07
It shouldn't be doing this, but I think changing the BIOS settings should fix it.  Just set it so your hard drive boot priority is above the CD priority.  To enter the BIOS, you usually have to press a key like <Del>, <F1>, <F2>, <F12>, etc when you first power on the computer (it will usually tell you what key to press).  After changing the priority, save and exit and restart - hopefully your error goes away :).

---

### Post by bnhrobotics on 2010-01-07
Thanks for the suggestion. All that does is removes the "booting from CD/DVD" line. Still hanging when trying to access the hard drive boot records.

---

### Post by bnhrobotics on 2010-01-07
Well, for some reason it was trying to boot from my RAID1 array in BIOS, which is not where the OS is installed. I fixed that and now I am getting GRUB error 15.

---

### Post by Buuntu on 2010-01-07
You will need to reinstall Grub 2, error 15 means that the file your master boot record is pointing to is not there (in this case grub).
To reinstall it: [https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

---

### Post by kansasnoob on 2010-01-07
> **Buuntu said:**
> You will need to reinstall Grub 2, error 15 means that the file your master boot record is pointing to is not there (in this case grub).
To reinstall it: [https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

Good place to start but may need to see the ouput of the Boot Info script:

[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)

Grub2 is not fond of raid - PERIOD!

---

### Post by bnhrobotics on 2010-01-07
Thanks. I reinstalled grub and that seemed to take care of it. 

My concern is that it might happen again. Why did it happen in the first place?

I formatted my RAID drive. Thats the only thing out of the ordinary that I can recall happening. My OS is not on the RAID though. I am just using a RAID1 for data backup. Any idea what could have happened?

sda and sdb are the RAID drives
sdc is my OS drive which has / /home and a blank partition.

---

