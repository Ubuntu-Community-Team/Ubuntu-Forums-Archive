---
title: "What command line tools are used to label an ext4  partition ?"
date: 2010-05-01
forum: New to Ubuntu
---

### Post by mikodo on 2010-05-01
I am following an Ubuntu community documentation guide, to mount a data partition. In it states for labeling  an ext4 partition via the command line, to use the e2label package. I can't find it, so can anyone please tell me which to use for this?

Thank you.

---

### Post by kaibob on 2010-05-01
The e2label utility is a part of the e2fsprogs  package, which is in the repositories.

An easier alternative that you might want to consider is the Disk Utility included in Lucid. It has an easily used GUI. I believe you have to run it as root:

```
gksudo palimpsest
```

Then select the drive and click on "Edit Filesystem Label." I used this utility to rename an NTFS storage partition, and it worked fine.

---

### Post by durand on 2010-05-01
> **kaibob said:**
> I think you can do that with the Disk Utility included in Lucid. I believe you have to run it as root:

```
sudo palimpsest
```

Then select the drive and click on "Edit Filesystem Label." I used this utility to rename an NTFS storage partition, and it worked fine.

Or just go to Applications > System Tools > Disk Utility.

---

### Post by kaibob on 2010-05-01
> **durand said:**
> Or just go to Applications > System Tools > Disk Utility.
I tried that when I renamed the storage partition on my primary drive, but I received an error message that the operation had to be done as root. I then ran the disk utility from the command line with sudo, and I was able to perform the operation. Perhaps I missed something.

---

### Post by durand on 2010-05-01
> **kaibob said:**
> I tried that when I renamed the storage partition on my primary drive, but I received an error message that the operation had to be done as root. I then ran the disk utility from the command line with sudo, and I was able to perform the operation. Perhaps I missed something.

Well, Disk Utility should ask you to enter your password before changing the label. Something must have gone wrong.

---

### Post by mikodo on 2010-05-01
> **kaibob said:**
> The e2label utility is a part of the e2fsprogs  package, which is in the repositories.

An easier alternative that you might want to consider is the Disk Utility included in Lucid. It has an easily used GUI. I believe you have to run it as root:

```
gksudo palimpsest
```Then select the drive and click on "Edit Filesystem Label." I used this utility to rename an NTFS storage partition, and it worked fine.
Thank you. I found e2label is **indeed,** one of the files in the e2fsprogs package, after reading your post. e2label does have to be run as sudo.

Mike

---

