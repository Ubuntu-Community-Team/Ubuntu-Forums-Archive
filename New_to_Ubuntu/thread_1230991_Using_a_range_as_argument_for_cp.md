---
title: "Using a range as argument for cp"
date: 2009-08-04
forum: New to Ubuntu
---

### Post by ozzyprv on 2009-08-04
I have a lot of files within a folder. I would like to copy only a certain group.

Let's say that all the files are named like IMG_12345 where "12345" is a consecutive numbering system.
For example:
IMG_00111
IMG_00112
IMG_00113
..
IMG_00198
IMG_00199
IMG_00200

If I wanted to copy from IMG_00120 to IMG_00194, from folder1 to folder2, how can I write the argument for the cp command?

Thanks.

---

### Post by lvleph on 2009-08-04
> If I wanted to copy from IMG_00120 to IMG_00194, from folder1 to folder2, how can I write the argument for the cp command?

You can use
```
cp folder1/IMG_00[120-194] folder2/
```

---

### Post by Jeff250 on 2009-08-04
In bash?  This should work:

```
cp folder1/IMG_00{111..200} folder2/
```

For any bourne-compatible shell, including bash but also such as sh, a for loop will work:

```
for i in `seq 111 200`; do cp folder1/IMG_00$i folder2/; done
```

---

### Post by ozzyprv on 2009-08-04
Files are actually named IMG_xyzj.JPG

So I tried 
```
cp IMG_[2070-2182].JPG /media/folder2/
```
And did not work. I got:
```
IMG_[2070-2182].JPG: No such file or directory

```

This worked:

```
cp IMG_{2070..2182}.JPG /media/folder2/
```

---

### Post by ghostdog74 on 2009-08-04
> **lvleph said:**
> You can use
```
cp folder1/IMG_00[120-194] folder2/
```

check your command next time before you post. the range operator [ ] is not used this way. as others have posted, use { } instead.

---

