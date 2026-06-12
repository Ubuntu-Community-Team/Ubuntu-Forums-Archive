---
title: "File name too long? for ext4 10.04?"
date: 2010-09-23
forum: New to Ubuntu
---

### Post by qakiudldu on 2010-09-23
I have an external harddrive formatted in NTFS that I use in windows XP. Now I tried to make a copy of that drive on ext4 ubuntu hard drive, but I get error saying file name is too long... 

I am surprised that 1. ext4 does not support file name length that windows xp can, and 2. the lack of information of this problem. Am I the only one? 

I am using ubuntu 10.04.

Any suggestions or easy fix are welcomed. Thanks in advance!
Cheers, Q

---

### Post by aeiah on 2010-09-23
ext4 max is 255 bytes (usually equals 255 characters)
ntfs max is 255 characters, from what i can tell.

most characters take up 1 byte, but fancy foriegn ones can take up more, so i guess there's a chance that this is the issue. its more likely to be something else though i would suspect. does it say where it is failing? perhaps if you copied on the command line it would spit errors out for you, either using cp or rsync

---

### Post by aeiah on 2010-09-23
try
```

rsync -a -v --progress /path/to/source/ /path/to/destination/

```
-a means archive. it retains datestamps, permissions etc. -v is verbose output.

---

