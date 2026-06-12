---
title: "video editing (stitching)"
date: 2009-03-09
forum: New to Ubuntu
---

### Post by powel212 on 2009-03-09
Anyone know what program can repackage video files without recoding them.

For example I have 2 .vob files that I want to combine into one video file, let's say into an mpg file as .vob is already mpg. 

As it is I use kdenlive which works great but I want to know if I can basically just stitch 2 or 3 files together in a linear fashion without having to re-encode the whole project. 

Any help is appreciated. 

Powel

---

### Post by FakeOutdoorsman on 2009-03-09
Some container formats, such as MPEG-2 PS, allow you to concatenate video files.  Try this:
```
cat first.vob second.vob > combined.vob
```

---

### Post by powel212 on 2009-03-10
Yes it worked! Awesome!

I tried 

$cat first.vob second.vob > combined.mpg

changing combined file extension to mpg and it worked like a charm. 

Thank you very much.

Powel

---

