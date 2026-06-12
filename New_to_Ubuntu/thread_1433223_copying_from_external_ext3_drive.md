---
title: "copying from external ext3 drive"
date: 2010-03-18
forum: New to Ubuntu
---

### Post by carbon13 on 2010-03-18
I had to swap out my hard drive, so I copied all my data to an external drive that I formated as ext3 (since some files were larger than 4 GB and I read NTFS wasn't linux friendly). I had problems writing to the drive initially so I used: 'gksudo nautilus' to open a browser that allowed me to write to the drive. I then swapped out my hard drive, reinstalled ubuntu 9.10 and now want to copy my data back to the new drive. Problem is, some files will not allow me even read access, even using the gksudo nautilus window.

So, I'm guessing that I need to change permissions on this drive, I've read a couple threads on this but I'm still a bit unsure. My drive is called /media/backup. Any help would be appreciated.

-Carbon13

---

### Post by undecim on 2010-03-18
using gksudo nautilus should allow you to read anything. Is it just a few files, many files, an entire folder?

It may be a drive error. What output do you get when you run "dmesg | tail" in a terminal?

---

### Post by carbon13 on 2010-03-18
It's quite a few files, many are pictures which I would like to get back.

dmesg I tail gives the following outpuy:

[  464.220314] end_request: I/O error, dev fd0, sector 0
[  476.299780] end_request: I/O error, dev fd0, sector 0
[  480.055283] kjournald starting.  Commit interval 5 seconds
[  480.055873] EXT3 FS on sdg1, internal journal
[  480.055878] EXT3-fs: mounted filesystem with writeback data mode.
[  488.380408] end_request: I/O error, dev fd0, sector 0
[  488.380413] Buffer I/O error on device fd0, logical block 0
[  500.460025] end_request: I/O error, dev fd0, sector 0
[  500.460030] Buffer I/O error on device fd0, logical block 0
[  512.538802] end_request: I/O error, dev fd0, sector 0

---

### Post by carbon13 on 2010-03-18
Correction: Nautilus allows me to see the files but I can't copy them over to the new hard drive. Again, it's not all files but some important ones.

---

### Post by carbon13 on 2010-03-18
OK, I think I figured it out.

So, I checked the file properties, permissions for the files I couldn't copy and they didn't have read and write enabled. I have no idea why these specific files were that way and others weren't.

I opened nautilus and selected all and changed permissions to read and write and then copied over. So far no error message. I'll post as solved once I verify everything was copied over.

Thanks for replying to my question.

Cheers,

-Carbon13

---

### Post by carbon13 on 2010-03-19
As above, here is what I did to solve the problem:

1. Open terminal. type 'gksudo nautilus'. New browser pops open.
2. browse to external drive
3. select all, right click and select properties - permissions
4. check that 'owner', 'group' and 'others' have both 'access' and 'read and write' permissions. Apply.
5. using same nautilus window, copy all files to desktop, from there I cut and pasted to where ever I wanted them on my desktop filesystem.


NOTE: I'm not sure about security implications of changing these permissions, so use at your own risk. Alternatively, change the permissions after you copy the data over.

---

