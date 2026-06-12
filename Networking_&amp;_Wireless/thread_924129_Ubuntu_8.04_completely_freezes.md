---
title: "Ubuntu 8.04 completely freezes"
date: 2008-09-19
forum: Networking &amp; Wireless
---

### Post by Alm4riC on 2008-09-19
Yesteday i opened this [this]("http://ubuntuforums.org/showthread.php?t=922629") topic. I think it's having to do with the following:

15 minutes ago i opened my laptop from standby and saw Ubuntu completely freezed with Num Lock blinking. I've searched Google, this forum, etc. and know i'm not the only one having this problem. But... i can't find any solution?

:(

---

### Post by mike1821 on 2008-09-19
It seems like a kernel panic condition... 

Maybe there is an error in your root file system. Try to boot the laptop with Ubuntu live-cd and perform a file system check.

```
fsck.ext3 [device_name]
```

In the above example I am using ext3 file system check, there is also fsck.reiserfs. Use the proper one.

---

