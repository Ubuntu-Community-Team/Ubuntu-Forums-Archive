---
title: "dissapearing hard drive space"
date: 2011-03-19
forum: New to Ubuntu
---

### Post by PermNoob on 2011-03-19
So I started running out of room on my / partition as I had been accidently saving videos to my home directory, which is on the 10 gig / parition.  I have a 90 gig partition for data, so i copied them over there, then when I deleted them off the home I continued getting a system warning that I had only 800 megs of space left.  I deleted some more stuff, and i didn't seem to have any more space, even after emptying the trash.  a disk usage scan turned up all the deleted files, approx 2 gigs iirc, in a folder called expunged.  I then opened nautlius w/ sudo privlages to delete this folder, and it whent away but I still have no space, and I can't turn up the files anywhere, it's as if my hard drive has shrunk, deleteing stuff only makes more space sometimes and I am out of things I can trash.   Please can someone help me figure out what is going on?  here is ascreen cap of the disk usage analyzer, showing that I have a 9.2 gig partition, and up top it says 8.2 used, and in the analyzer it says / is only 4.2 gigs??

anyone have a light they can shine?

---

### Post by papibe on 2011-03-19
Could you post the result of:
```
$ df -h
```
Regards.

---

### Post by drs305 on 2011-03-19
When you delete something as root it goes into root's trash bin and isn't emptied when you empty your own trashbin.

To empty the root trash bin and free up space, open a browser as root and remove the files from /root/.local/share/Trash. Use SHIFT-DEL to remove them. Using just the DEL key will just move them back to .... Trash!

More info:  [_http://ubuntuforums.org/showthread.php?t=898573_]("http://ubuntuforums.org/showthread.php?t=898573")

---

### Post by PermNoob on 2011-03-19
ok thank you! the icon for the trash when i opened nautilus w/ root was empty, and when i tried to open it i would get an error.  I had forgotten all about this.  I found 3.6 gigs worth of stuff in there.  now there are two folders, one labelled files the other labeled info.  do i delete both folders, or only their content?

---

### Post by PermNoob on 2011-03-19
that link was super informative, thank you!

---

