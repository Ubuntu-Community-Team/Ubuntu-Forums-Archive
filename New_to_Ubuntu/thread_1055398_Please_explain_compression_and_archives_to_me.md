---
title: "Please explain compression and archives to me"
date: 2009-01-30
forum: New to Ubuntu
---

### Post by ricardisimo on 2009-01-30
There's something that I'm not understanding about them. I had a group of folders that I was trying to fit onto a data CD, and they were just a tad too large - 706.2 MB. Fine, I'll try compressing them into a 7z, a zip, rar... whatever. I don't need it to work miracles, just squeeze it in.

No luck. All of the resulting archives were ***larger*** than the sum of the original files and folders. What's up with that? What's the point of compressing files, if you're effectively expanding them into a larger archive? Thanks for any insight.

---

### Post by Gulyan on 2009-01-30
Some files (ig media files) are already compressed so you won't have too much luck if you try to shrink them. ;)

---

### Post by Mud.Knee.Havoc on 2009-01-30
Gulyan's probably hit the nail on the head.  Were you trying to compress mp3 or avi files, or something along those lines?

---

### Post by ricardisimo on 2009-01-30
Yeah, it was five folders' worth of the best music Zimbabwe has to offer, and yes they were already compressed (.ogg, etc.) It still seems odd to me... there's some part of the logic I might never get without knowledge of programming, but c'est la vie. Thanks for the replies.

---

### Post by snova on 2009-01-30
> **ricardisimo said:**
> Yeah, it was five folders' worth of the best music Zimbabwe has to offer, and yes they were already compressed (.ogg, etc.) It still seems odd to me... there's some part of the logic I might never get without knowledge of programming, but c'est la vie. Thanks for the replies.

Compressed files are notoriously incompressible. :)

Compression works by eliminating redundancies, finding patterns. A good algorithm can find more ways to reduce it than a bad algorithm, so that the output is essentially completely random- and random data *is* incompressible.

You could try forgoing archivers and using straight Gzip/Bzip2/LZMA, by the way. It probably won't do much good, but you never know...

---

