---
title: "Ubuntu is corrupting my images"
date: 2009-04-22
forum: New to Ubuntu
---

### Post by munishvit on 2009-04-22
Around 6 months back I started using Ubuntu 8.04 as my OS. For last 3-4 months, I found that my pictures (some desktop snapshots and other from digi-cam) are getting corrupted. In most of the pictures, some part of the image is shifted bit left or right.
I am not getting reason behind this, can it be due to OS?

---

### Post by Peter09 on 2009-04-22
Most likely your video card, what card have you got?

```
lshw -C video
```

will give you some information

---

### Post by billgoldberg on 2009-04-22
> **munishvit said:**
> Around 6 months back I started using Ubuntu 8.04 as my OS. For last 3-4 months, I found that my pictures (some desktop snapshots and other from digi-cam) are getting corrupted. In most of the pictures, some part of the image is shifted bit left or right.
I am not getting reason behind this, **can it be due to OS?**

It sounds very unlikely.

---

### Post by munishvit on 2009-04-25
> **Peter09 said:**
> Most likely your video card, what card have you got?

```
lshw -C video
```

will give you some information


Do you really think...it could be because of video card...as I don't have any problem in system graphics. 
Right now I am not at my system...I shall give you the result later.
My root drive is the only drive formatted with ext3, all other drives, on which I use to keep all my documents including pictures, are formatted with NTFS. Is there any possibility that this might be the cause? For those drives, in /etc/fstab I have entry similar to following:
/dev/hda5 /mnt/media ntfs-3g defaults 0 0ted 
[IMG]http://ubuntuforums.org/picture.php?albumid=1059&pictureid=3732[/IMG]

---

