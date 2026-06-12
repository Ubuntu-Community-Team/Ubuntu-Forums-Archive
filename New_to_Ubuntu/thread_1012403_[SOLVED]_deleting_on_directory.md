---
title: "[SOLVED] deleting on directory /"
date: 2008-12-15
forum: New to Ubuntu
---

### Post by capnthommo on 2008-12-15
hi all.  when i enter [sudo fdisk -l] i get the following:

nigel@nigel-laptop:~$ sudo fdisk -l
[sudo] password for nigel: 

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x939aab47

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            6238       12525    50508360   83  Linux
/dev/sda2               1        6237    50098671   83  Linux
/dev/sda4           12526       19457    55681290    5  Extended
/dev/sda5           12526       19168    53359866   83  Linux
/dev/sda6           19169       19457     2321361   82  Linux swap/Solaris

this represents my partitions at present (no windows at all).  when i go to system monitor the partitions are used up as follows:
Device     Directory     Type    Total   Free     Availble  Used    %used
/dev/sda5  /             ext3    50.1GB   9.4GB    6.8GB   40.7GB  85%
/dev/sda1  /backup       ext3    47.4GB  45.8GB   45.8GB    1.6GB   3%
/dev/sda2  /data         ext3    47.0GB  44.2GB   44.2GB    2.8GB   5%
(im sorry, but i cant preserve the format here - if you need it clarifying ask me and i will try again)
this is what i am left with after the earlier thread.  now, i am happy with this but would like to know how i can go about clearing some of the 85% used up space on /dev/sda5.  is it even necessary? or will it eventually fill up?  if anyone can help with this i would be grateful
cheers
nigel

---

### Post by drs305 on 2008-12-15
Section 8 of the following tutorial offers techniques to free up space. Don't forget to refer to the major part of the tutorial as well, which deals with finding trash scattered throughout your system:
[How To: Disk Full? - Check Your Trash]("http://ubuntuforums.org/showthread.php?t=898573")

Among the items referenced:
apt-get clean/autoclean/autoremove
localepurge
deborphan
tune2fs
finding large files

---

### Post by Paqman on 2008-12-15
The disk usage analyser is a handy tool too. To see all the files mkae sure you run it as root:
```
gksu baobab
```

Something is using up a huge amount of space on your / partition, as it really should be well under 10GB. Do you have any Windows apps installed through Wine? These would have been installed into your /home/username/.wine folder, and can be quite large. Another thing to watch out for is old backup files, or automated backups that have ended up in the wrong place.

---

### Post by capnthommo on 2008-12-16
hi, thanks to both drs305 and paqman.  i will check out the advice link.  and thanks for the code for disk usage.
"Something is using up a huge amount of space on your / partition"  something certainly is - probably the previous attempts to backup.  i watched as my directory got fuller with each try.  if i can use one or other of the apps to clear out .  just so long as i can identify what is unnecessary and not clear out stuff i need.  thanks again
nigel

---

### Post by Zack McCool on 2008-12-16
You can always do a ```
 du -H / 
``` (be prepared for a TON of information to scroll, you may want to direct the output to a file for browsing: ```
 du -H / > usage.txt 
```

OR, install gnome-utils if it isn't already there, and run the disk usage analyzer found in your Applications | Accessories menu.  Once it opens, select "scan filesystem", and give it some time.  It will give you a graphical representation of your disks, and let you drill down through to find the biggest offenders...

---

### Post by capnthommo on 2008-12-16
thanks once more, everybody.  with a few tactical deletes and trash empties i now am only using8.6 GB of the 50.1GB available on directory /.  it was mainly old backups which i have now cleared.  thanks for pointing out where to find them.  things look a whole lot less worrying now.
cheers
nigel
):P

---

