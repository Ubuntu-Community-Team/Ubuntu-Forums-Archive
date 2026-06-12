---
title: "Slow video file operations"
date: 2009-04-01
forum: New to Ubuntu
---

### Post by User548 on 2009-04-01
I am having an interesting issue.
When I try to copy/move video files (.avi) from one place to another the file transfer speed is slow (around 4 mb/sec and sometimes slower). However, when it is not a video file, the transfer speed is around 30 mb/sec.
It is not based on the size of the file as I can move the ISO image of Ubuntu (around 700 mb) at the high speed, while a 150 mb video file is still 4 mb/sec.

Any suggestions? 
I tried searching for this issue but cannot find one that is for slow file operation speed for just one file "type".

Details: 
Ubuntu V8.10
Sata hard disks
Does not make a difference if it is on the same disk or different disks or the file system type.

---

### Post by ibuclaw on 2009-04-01
I'm not suggesting at all that my words are golden or true - but - as far as I know, this is how it works:

The process of moving a file from one hard drive/filesystem to another happens like this:
[LIST]
[*]The file gets read from the Hard drive.
[*]A copy of the file is moved into memory, buffer, or a dirty writeback cache (whatever you want to call it, it is just RAM), and the data is kept there until it is flushed.
Since writing/allocating/reallocating memory to RAM is by far quicker, this speeds up the apparent "speed of transaction"
[*]The original file is unlinked once the copy is complete (but only if you **moving** the file, instead of copying it).
[*]After a set period of time, the buffer is flushed, and the data in cache gets written fully back to the new hard drive/filsystem.
[/LIST]
The point I'm getting at is, when transferring smaller files from one filesystem to another, it is likely that they will just be copied to cache and kept there for a brief period of time. This is transparent to the user, as far as you know, all files have been copied to the new filesystem (ever wondered why you need to safely unmount a USB pendrive before removing it? That's because not all data may have been flushed/written to the disk yet).

Whereas with larger files, say 2GBs, this is not an ideal amount of data to keep in RAM all at once, it will cause an overall sluggishness, high activity and instability of the system, so it get written back to the new hard drive/filesystem immediately, rather than later.

That said, I do believe the default settings of ext3 are to flush the writeback cache once every 5 seconds. But that evidently is enough to make a notable difference.

Regards
Iain

---

