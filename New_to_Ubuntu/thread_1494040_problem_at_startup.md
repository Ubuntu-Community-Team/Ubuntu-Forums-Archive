---
title: "problem at startup"
date: 2010-05-26
forum: New to Ubuntu
---

### Post by oaridus on 2010-05-26
Hi, when I start up my ubuntu 10.04 system I get the following message.

The disk drive for /media/windows is not ready yet or not present.
Continue to wait or press s to skip or m for manual recovery.

Then when I skip it, it gives me the normal ubuntu desktop and I can mount windows partition from Places menu. How do I overcome this message? What does it mean? Please help

---

### Post by cariboo on 2010-05-26
It sounds like you are trying to auto mount your ntfs partition, could you paste the output of:

```
cat /etc/fstab
```

in your next post?

---

### Post by Ozymandias_117 on 2010-05-26
It may also be useful if you post the results of ```
sudo fdisk -l
```

---

