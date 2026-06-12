---
title: "File Transfer Problem"
date: 2011-01-10
forum: New to Ubuntu
---

### Post by Steelfan555 on 2011-01-10
A friend has recently moved to Ubuntu, and is having trouble (aka can't) transferring files from is USB HD (NTFS) to his Ubuntu partition (EXT4). He has 2 GB of swap, which was what I thought it was at first. 

He says it freezes around 150 and 500 mb.

I had him open GParted and look, to double check the Formats and sizes. He has a red ! point in front of the HD, and it mentions : (see attachment)


Any Ideas?

---

### Post by blind2314 on 2011-01-10
Silly question, as it should be there, but does he have the package it mentions? "ntfsprogs"?

---

### Post by Steelfan555 on 2011-01-10
Yes, sorry, I should have mentioned it.

---

### Post by Steelfan555 on 2011-01-11
Bump.

---

### Post by bodhi.zazen on 2011-01-11
Open a terminal and try to manually mount the device.

```
sudo mount /dev/sdb1 /mnt
```

---

### Post by Steelfan555 on 2011-01-11
Thanks. He got it to work after he reinstalled and got 64bit, used gksu nautilus and mounted it manually. 
So it may be anyone of those things.

---

