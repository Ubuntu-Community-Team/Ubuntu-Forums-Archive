---
title: "[SOLVED] error 18: cylinders exceeds maximum supported bios"
date: 2008-12-15
forum: New to Ubuntu
---

### Post by brojard on 2008-12-15
Back ground: 
My old  20 gb hd (ide) on which the OS resided crashed. I have 6 other 120 gb harddrives running raid5. These raided drives do *not* have the OS on them.  The previous OS was debian so I thought I'd try ubuntu 10.4 server. I installed a new 80 gig (also ide) harddrive, formated and installed ubuntu 10.4.

I've been setting up services. Raid5 came back fine. Didn't lose anything! Everything is almost completely back to normal. When I left for the day on Friday I shut down. This morning, when I powered it back up it couldn't find the boot image and asked me to insert a disk and hit any key to proceed. 

I fiddled around with the bios, changing from *auto* detect to *user* and back several times.... and after a while, grub offered some images to select but: I still get the following: 

error 18: cylinders exceeds maximum supported bios. 

I fiddled with bios settings again, back to user then to auto, several times... leaving it blank on one occasion and finally   it found the boot image. 

I shutdown again and rebooted, and same thing again only this time, I had to mess with bios for 2 hours - I don't know why it accepts the changes one time and not another. This seems to be a weird intermittent problem. 

Found a thread that says I should copy the partition info C/H/S to bios. How do I do that? What is S? is S Start or is S system? 


Results of sfdisk for this device as follows. 


sudo sfdisk /dev/sda  -l 
(I've omitted the end info intentionally) 

Device   Boot Start End        Cyl Blocks      ID System
/dev/sda1 *     0+  (omitting) 1870 15020743+  83  Linux
/dev/sda2       1870           7858 63127417+  5   extended
/dev/sda3       0               0   
/dev/sda4       0               0    
/dev/sda5       9636            93- 746991     82  Linux Swap
/dev/sda6       1870           7673 61633309+  83  Linux
/dev/sda7       9543           93-  746991     82

This problem only occurs when I shutdown -h if I restart, I'm ok. 

Here is what is in grub too:

root (hd0,0)
kernel /boot/vmlinuz-2.6.24.19-server root=UUID=44056814-1515-4c7c-aa5c-f060c720e0c7 ro quiet splash
initrd /boot/intrd.img.2.6.24-19-server
savedefault
boot

I  found a hit that said I need 384 ram for ubuntu - i only have 256. I will fix that, but before I shutdown, I was hoping someone could help me with this boot problem - since I'm not sure why/how I get it back up, - I'm afraid I may not be so lucky next time.

Thanks

---

### Post by bodhi.zazen on 2008-12-15
See this page :

[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

Scroll down to error 18 :twisted:

---

### Post by nhasian on 2008-12-15
C/H/S stands for Cylinders, Heads, Sectors.  This information used to be printed on hard disks, but that was years ago i dont know if they still do that.

Is the boot partition at the beginning of the hard disk?  (in the first 1023 cylinders of the harddrive)

---

### Post by brojard on 2008-12-15
Problem resolved. Changed bios to AUTO and ensured that all the head,cylinder and sector entries were cleared before I proceeded. Last time when I set it to AUTO, I hit enter - which populated those fields from (defaults or previously stored info?) Anyway, leaving the fields cleared seemed to do the trick. Boots fine now.  
Sorry if I wasted anyone's time.

---

### Post by Malalo on 2008-12-15
I had the same error the first time I installed Ubuntu on my server. It's a very old machine (dual P2-700MHz) and apparently the BIOS didn't appreciate having a boot sector farther than the first 8 Gigs (I think) of the disk. So I had to manually set partitions with gParted during the installation, to make sure that the /boot partition was the first on the disk. Having done that, I never had any problems with error 18 since then.

---

### Post by oilchangeguy on 2008-12-15
also see this thread:
[http://ubuntuforums.org/showthread.php?t=1009967](http://ubuntuforums.org/showthread.php?t=1009967)

---

### Post by oilchangeguy on 2008-12-15
> **brojard said:**
> Problem resolved. Changed bios to AUTO and ensured that all the head,cylinder and sector entries were cleared before I proceeded. Last time when I set it to AUTO, I hit enter - which populated those fields from (defaults or previously stored info?) Anyway, leaving the fields cleared seemed to do the trick. Boots fine now.  
Sorry if I wasted anyone's time.

please use the thread tools to mark your problem as solved.

---

