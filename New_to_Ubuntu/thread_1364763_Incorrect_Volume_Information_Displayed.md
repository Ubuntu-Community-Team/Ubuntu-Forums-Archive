---
title: "Incorrect Volume Information Displayed"
date: 2009-12-26
forum: New to Ubuntu
---

### Post by I[AM]SMRT on 2009-12-26
I woke up this morning to find that I had 64 MB left on my external ext3 backup drive. When I left it last night I had ~30 GB left! Some relevant output:

```
df -h /media/Seagate500/
Filesystem            Size  Used Avail Use% Mounted on
/dev/sdc1             459G  436G     0 100% /media/Seagate500

```

```
sudo du -h --max-depth=1
354G	./Videos
16K	./lost+found
82G	./Backups
436G	.
```

I know I have the space because I can copy files onto the drive albeit using sudo. Gparted displays the information correctly ([http://imgur.com/BfbRf.png](http://imgur.com/BfbRf.png)). What the hell is going on?

EDIT: Figured out my issue, accidentally backed up files in the trash that were taking up a lot of space. For some reason, they weren't being included in the du counts.

---

