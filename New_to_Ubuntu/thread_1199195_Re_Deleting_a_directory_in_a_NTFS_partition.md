---
title: "Re: Deleting a directory in a NTFS partition"
date: 2009-06-28
forum: New to Ubuntu
---

### Post by thanhbv on 2009-06-28
I want to delete a directory in NTFS partition.
In windows xp, when delete -> error ''The filename, directory name, or volume label syntax is incorrect''.
I think it's because in the directory, i have some file with vietnamese characters in the name. (if i delete any directory which hasn't vietnamese named file -> success)

Then, i try to delete in ubuntu, because don't like windows, linux use utf-8 to encode file name. But:
when delete some but not all vietnamese named file -> error. 
When delete its parent directory =>  "failed to remove `xxx': Directory not empty". 
When go inside that directory -> there is no file (normal or hidden file).
when i try to remove xxx again (remove as root user) -> "failed to remove `xxx': Directory not empty"!!!!!!!!!

---

### Post by thanhbv on 2009-06-28
Oh, after delete some files & the directory in ubuntu as describing above, I reboot into windows -> windows warn me that the partition that the files belong to should be check. Then windows use CHKDSK to check the partition -> inform that "correcting index 0 in file 25" (or some thing like that). But after very long time, it don't finish.

:D ha ha.
finally, my solution is: copy all necessary file into other partition and then format the error partition!

---

