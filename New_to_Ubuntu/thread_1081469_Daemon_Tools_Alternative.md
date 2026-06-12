---
title: "Daemon Tools Alternative?"
date: 2009-02-26
forum: New to Ubuntu
---

### Post by Testrum on 2009-02-26
Are there any open source applications that work like Daemon Tools?

---

### Post by 4Orbs on 2009-02-26
gmountiso in the repositories.

---

### Post by soxs on 2009-02-26
```
sudo mount -o loop /path/to/your/dvd-image.iso /target/mount/point
```thats all you actually need

sometimes you need to append this to the said command:
```
-t iso9660

```

---

### Post by kanikilu on 2009-02-26
[http://www.ubuntugeek.com/mount-and-unmount-isomdfnrg-images-using-acetoneiso-gui-tool.html](http://www.ubuntugeek.com/mount-and-unmount-isomdfnrg-images-using-acetoneiso-gui-tool.html)

Just another option if you're not particularly keen on doing it on the CLI - although knowing how to do so can be useful.

---

### Post by cb951303 on 2009-02-26
there is also archive mounter. right click an *.iso, it should be there.

---

### Post by Ptero-4 on 2009-03-04
> **soxs said:**
> ```
sudo mount -o loop /path/to/your/dvd-image.iso /target/mount/point
```thats all you actually need

sometimes you need to append this to the said command:
```
-t iso9660

```

You might need
```
-t udf
```
instead if it's a DVD.

---

