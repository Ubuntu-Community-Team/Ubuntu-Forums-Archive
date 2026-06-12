---
title: "possible file system types"
date: 2009-02-12
forum: New to Ubuntu
---

### Post by JMcKercher on 2009-02-12
I just started using linux 3 days ago and I'm trying to get an external hard drive that is 80 GB to work with Ubuntu.  What is the best file system to format the hard drive with?

Thanks for helping a complete beginner.

Also I need help mounting the drive so that it can see it.

---

### Post by hyper_ch on 2009-02-12
do you want to use that external disk with linux only? also with windows? also with mac OS?

---

### Post by logos34 on 2009-02-12
ext3 is a good all-round choice...Or maybe reiserfs if you will be storing a lot of smaller files.  

mounting:

[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

---

### Post by JMcKercher on 2009-02-12
Just for linux, I have a solid state drive that I don't want to waste the writes on.

---

### Post by hyper_ch on 2009-02-12
well, if you have mostly large files then I'd go for XFS... if it's mostly small files then ReiserFS and if it's mixed or you have no clue then Ext3

---

