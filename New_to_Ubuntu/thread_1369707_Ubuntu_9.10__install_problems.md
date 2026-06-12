---
title: "Ubuntu 9.10  install problems"
date: 2010-01-01
forum: New to Ubuntu
---

### Post by bobmccleskey on 2010-01-01
I am trying to install Ubuntu 9.10 (64 bit) on an HP a6528p computer. I was successful in getting the 32 bit version to run for a few cycles then have been getting the following messages at start up and am not able to go any farther. Incidentally, I have run a disk check on the hard drive multiple times and gotten a "failed status value 7 (completed with the read e of the test failed) in one of the check disk runs. The messages I am getting are:
 
Mount of file system failed
A maintenance shell will now be started
Control-D will terminate the shell and retry
* starting init crypto disks...
Root@bosb-desktop: ~# [ok]
 
Can anyone suggest something that might solve the problem? 
 
I am really eager to try Ubuntu and am hoping to get it to run on the HP. I should also note that when I access the BIOS it reflects the disk device priority as Hard Disk being #1 and the CD/DVD being #2, even though I have reset the boot sequence to being the CD/DVD as #1 and the hard drive as #2.

---

### Post by tom.swartz07 on 2010-01-01
> **bobmccleskey said:**
> I am trying to install Ubuntu 9.10 (64 bit) on an HP a6528p computer. I was successful in getting the 32 bit version to run for a few cycles then have been getting the following messages at start up and am not able to go any farther. Incidentally, I have run a disk check on the hard drive multiple times and gotten a "failed status value 7 (completed with the read e of the test failed) in one of the check disk runs. The messages I am getting are:
 
Mount of file system failed
A maintenance shell will now be started
Control-D will terminate the shell and retry
* starting init crypto disks...
Root@bosb-desktop: ~# [ok]
 
Can anyone suggest something that might solve the problem? 
 
I am really eager to try Ubuntu and am hoping to get it to run on the HP. I should also note that when I access the BIOS it reflects the disk device priority as Hard Disk being #1 and the CD/DVD being #2, even though I have reset the boot sequence to being the CD/DVD as #1 and the hard drive as #2.

It sounds like you simply have a bad install. 

My suggested route of attack would be to 
1. Re-burn the .iso to a disk at a slow speed (this way it prevents errors)
2. Boot to your cd, and select 'test disk for defects'
then,
3. Re-install Ubuntu.


Sometimes, if there is a small error on the disk, the entire install of ubuntu could fail. Its not common, but its the most likely cause of problems.


Hope this helps!

---

### Post by tilixibr on 2010-01-02
It seems you used Wubi... I had this problem too.
Burn your .iso image and install from the CD, there should be no problems:)

---

