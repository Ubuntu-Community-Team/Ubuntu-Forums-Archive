---
title: "Locate and updatedb commands question"
date: 2009-02-09
forum: New to Ubuntu
---

### Post by Miguellint on 2009-02-09
Hi all...I have a two-partition external hard drive which mounts as /media/sdb1 and /media/sdb2

This from /etc/mtab......

/dev/sdb1  /media/sdb1 ext2 rw 0 0
/dev/sdb2  /media/sdb2 ext2 rw 0 0


At the moment the locate command only searches through the partitions on /dev/sda. 

How can I get the updatedb command and the locate command to include /dev/sdb in their search path.

Many thanks
Miguel

---

### Post by NT4usB on 2009-02-09
iirc, updatedb and/or locate ignore the /media directory.
Someone pointed this out a while back and I'll have to do some digging to find the info.
I do recall looking at the updadedb file and seeing the structure, exclusions, etc. Not in front of my Ubuntu box atm. I'll have a look again tonight.
In the meantime, did you look at the man pages for these?

ed: [here it is.]("http://www.google.com/search?hl=en&q=site%3Aubuntuforums.org+updatedb+locate+%2Fmedia+folder&btnG=Google+Search&aq=f&oq=") Read the second result.

---

### Post by Miguellint on 2009-02-09
NT4usB....you da man (as all the cool kids say).

Edit as root /etc/updatedb.conf 
Remove /media from PRUNEPATHS
Exit and save
sudo updatedb

Job done

100 penguin points to you.

Many thanks
Miguel

---

### Post by NT4usB on 2009-02-10
Glad you got it working.
Be sure to mark the thread 'Solved' using the thread tools top right.
...and save that link. You can put your own search words after ubuntuforums.org and search all these forums for whatever.
Way better than the boards search engine...

---

