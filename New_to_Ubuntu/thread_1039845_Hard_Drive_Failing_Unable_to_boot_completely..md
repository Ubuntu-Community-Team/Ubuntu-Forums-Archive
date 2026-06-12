---
title: "Hard Drive Failing/ Unable to boot completely."
date: 2009-01-14
forum: New to Ubuntu
---

### Post by hightemplar8 on 2009-01-14
Dear friends,

I need help! A few days ago my hard drive started to fail. Before I could backup anything. Unbuntu stop booting completely.
Every time it boots up I get this error. - 
"Could not start the X Server due to some internal error. Please contact your sysem adminstrator or check your syslog to diagnose. In the meantime this display will be disabled. Please restart GDM when the problem is corrected"

I tried running 'fsck' but it give me a long list of errors on the drive.

I was able to boot from the live cd to recover some information but there's just too much. example - Where would my firefox and opera bookmarks be located? Can I just reinstall Ubuntu without losing my data?

Any advice would be great. Thank You!

---

### Post by hightemplar8 on 2009-01-15
I have also tried using recover mode but that failed.
I got a error when I ran xfix

I'm also getting a 'UNEXPECTED INCONSISTENCY; run fsck manually.fsck died exit status 4.' when I boot up.


Any ideas?

---

### Post by cariboo on 2009-01-15
I would suggest putting your drive in the freezer for a couple  of hours, then run fsck from the live cd. Once it is finished you should be able to backup any important data.

Your Firefox bookmarks are located in ~/.mozilla. It is a hidden directory, once you start Nautilus (Places-->Home Folder) press Ctrl-h to reveal the hidden files and directories.

Jim

---

### Post by Vantrax on 2009-01-15
Simple answer is your disk is failing, id suggest trying the freezer trick, and putting it into a working machine (not booting off it) and copying your home as fast as possible.

---

### Post by hyper_ch on 2009-01-15
if it runs until it tries to start the xserver than it's not the harddisk that's failing. My suggestion is to:

(0) ALWAYS HAVE BACKUPS

------------------------------------

(1) get another drive
(2) boot from a live cd
(3) clone the orginial to the new one using dd

---

### Post by hightemplar8 on 2009-01-15
Can I reinstall Ubuntu without losing my data?
Where would my Opera bookmarks/Speed Dial be located?
How do I run fsck from the livecd? what syntax would i use?

I found my firefox bookmark but it's blank!!! HELP!


Thanks for all the replies!

---

### Post by hightemplar8 on 2009-01-15
I was able to backup most of my data. :P

but still blank bookmark :confused:

---

### Post by crjackson on 2009-01-15
> **hightemplar8 said:**
> Dear friends,

I need help! A few days ago my hard drive started to fail. Before I could backup anything. Unbuntu stop booting completely.
Every time it boots up I get this error. - 
"Could not start the X Server due to some internal error. Please contact your sysem adminstrator or check your syslog to diagnose. In the meantime this display will be disabled. Please restart GDM when the problem is corrected"

I tried running 'fsck' but it give me a long list of errors on the drive.

I was able to boot from the live cd to recover some information but there's just too much. example - Where would my firefox and opera bookmarks be located? Can I just reinstall Ubuntu without losing my data?

Any advice would be great. Thank You!

Boot from a LiveCD, mount the drive in question, back-up your personal data.

Then address the drive issue.

---

### Post by crjackson on 2009-01-15
> **hightemplar8 said:**
> Can I reinstall Ubuntu without losing my data?
Where would my Opera bookmarks/Speed Dial be located?
How do I run fsck from the livecd? what syntax would i use?

I found my firefox bookmark but it's blank!!! HELP!


Thanks for all the replies!

make an archive of the important parts of your home forler.  i.e.  .opera .firefox etc...

When you get the drive sorted out you can restore from the archive and your missing bookmarks should be there. Don't forget to back up your emails too...

---

