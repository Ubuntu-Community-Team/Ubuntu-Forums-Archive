---
title: "NTFS to ext4"
date: 2010-08-08
forum: New to Ubuntu
---

### Post by ohlawd on 2010-08-08
Is there no way to convert to ext4 without data loss?
I was going to go the resize route, but gparted is painfully slow, is there any other way to do this?

---

### Post by Ozymandias_117 on 2010-08-09
> **ohlawd said:**
> Is there no way to convert to ext4 without data loss?
I was going to go the resize route, but gparted is painfully slow, is there any other way to do this?

Only thing you can do is back up your data and reformat. Sorry.

---

### Post by PASAf on 2013-01-08
Actually there is way.

At first, you need convert ntfs to ext2 or ext3 with **anyconvertfs** from anyfs-tools: [http://anyfs-tools.sf.net/](http://anyfs-tools.sf.net/)

Then you just need to convert it to ext4 with *tune2fs*.

That's all.

---

### Post by howefield on 2013-01-08
Old thread clsoed.

Please desist in spamming old threads.

---

