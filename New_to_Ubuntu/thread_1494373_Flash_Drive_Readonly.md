---
title: "Flash Drive Readonly"
date: 2010-05-26
forum: New to Ubuntu
---

### Post by Manaan on 2010-05-26
I have been trying to copy some videos to my 8gb flash drive for over a week now. Every time I plug it into my Ubuntu 10.04 netbook it mounts as read only. I can't chmod it back to read-write so I'm stuck. I'm pretty new to Ubuntu so I'd appreciate it if people would explain what the commands they give me do. I don't mind if you don't but I want to learn more about bash commands.

---

### Post by TheUnwiseman on 2010-05-26
Is this a brand new flash drive?  If it is, you might have to format it first.

---

### Post by Manaan on 2010-05-26
No, it's about a year old. It's pretty beaten up, but I don't think it's a hardware problem because I can read the filesystem just fine.

---

### Post by TheUnwiseman on 2010-05-26
You said you weren't able to chmod it.  Why is that?

---

### Post by Manaan on 2010-05-26
When I type
```
chmod +rw 4998-4ECA/
```I get
```
chmod: changing permissions of `4998-4ECA/': Read-only file system
```

---

### Post by TheUnwiseman on 2010-05-26
I think you need root permission to chmod a file system.

---

### Post by Manaan on 2010-05-26
Nope, I tried sudo chmod and it gave me the same error.

---

### Post by TheUnwiseman on 2010-05-26
And it works in other computers just fine?

---

### Post by Manaan on 2010-05-26
Yup. I just tested it. On a windows vista machine I was able to delete and create a file.

---

### Post by 2hot6ft2 on 2010-05-26
I would just open gparted and delete the partition then create a new one. I've only had a few that went read only but that has always fixed them.
:popcorn:

---

### Post by Manaan on 2010-05-26
I'm trying that now. I'll edit this post with the results.

EDIT: Yup! It worked perfectly! Thanks for the help.

---

### Post by oldfred on 2010-05-26
If it is FAT or NTFS:

Ownership and permissions of vfat / ntfs are set at the time of mounting. This is often a source of confusion.

[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)


Also if it is FAT you cannot copy files that are more than 4GB (less one byte).

---

