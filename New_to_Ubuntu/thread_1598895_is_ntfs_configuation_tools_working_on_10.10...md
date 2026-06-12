---
title: "is ntfs configuation tools working on 10.10.."
date: 2010-10-17
forum: New to Ubuntu
---

### Post by amitvn on 2010-10-17
i recently upgraded my ubuntu from 10.04 to 10.10 and found all other things working properly....but the tool i used for automounting my ntfs is not working on 10.10...any help :)

---

### Post by amjjawad on 2010-10-17
> **amitvn said:**
> i recently upgraded my ubuntu from 10.04 to 10.10 and found all other things working properly....but the tool i used for automounting my ntfs is not working on 10.10...any help :)

First of all, what tool are you using? 
I assume you downloaded/installed it on 10.04 but it doesn't work anymore, right?

Can you mount your NTFS partition(s) **now** without that tool?

---

### Post by amitvn on 2010-10-17
yeah i can mount my ntfs normally...i used that tool for automunting my ntfs on startup..

---

### Post by amjjawad on 2010-10-17
> **amitvn said:**
> yeah i can mount my ntfs normally...i used that tool for automunting my ntfs on startup..

Sometimes when you upgrade, some settings might be lost.
How about you re-install that tool again?

If you're able to mount that NTFS partition, then it shouldn't be a problem but I understand you want to auto-mount it on startup.

---

### Post by sikander3786 on 2010-10-17
It would be better to purge the ntfs-config with all its config.

```
sudo apt-get remove --purge ntfs-config
```

Then take a look at your /etc/fstab so that it doesn't contain anything wierd. ntfs-config tool is knows to cause some problems there. Your NTFS partitions should not be listed in fstab before install ntfs-config.

And then reinstall.

```
sudo apt-get install ntfs-config
```

---

