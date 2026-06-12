---
title: "bad blocks?"
date: 2009-07-08
forum: New to Ubuntu
---

### Post by EvilBro on 2009-07-08
How do I scan my harddisk for bad blocks in Ubuntu?

---

### Post by nhasian on 2009-07-08
actually i recommend using the diagnostic tools provided by the hard drive manufacturer on their website.

---

### Post by EvilBro on 2009-07-08
> **nhasian said:**
> actually i recommend using the diagnostic tools provided by the hard drive manufacturer on their website.

Is there a way to determine who that would be without opening my computer (Yes, I am lazy :) )?

---

### Post by mkrahmeh on 2009-07-08
there is a command for checking ext2/ext3 filesystem, but you need to unmount the drive you want to check 
```
e2fsck /dev/*drive*
```

---

### Post by Ocxic on 2009-07-08
> **mkrahmeh said:**
> there is a command for checking ext2/ext3 filesystem, but you need to unmount the drive you want to check 
```
e2fsck /dev/*drive*
```

That will only check the filesystem and won't give a good reading for the harddrive itself.
try installing smartmontools to check the smart status of your hard drive. that will give a true indication of the status of your HD

---

### Post by nhasian on 2009-07-09
```
sudo hdparm -i /dev/sda
```

or

```
sudo hdparm -i /dev/hda
```

Depending on whether its a SATA or IDE drive.

> **EvilBro said:**
> Is there a way to determine who that would be without opening my computer (Yes, I am lazy :) )?

---

