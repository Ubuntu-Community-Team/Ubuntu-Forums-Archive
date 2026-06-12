---
title: "zcat boot.img.gz"
date: 2011-07-11
forum: New to Ubuntu
---

### Post by YOUWERENTKIDDING on 2011-07-11
I ran zcat boot.img.gz > /dev/sda when I meant to run zcat boot.img.gz > /dev/sdb
I then ran zcat boot.img.gz > /dev/sdb

Now I cannot reformat or modify the usb ( sbd ) partition through gparted and my main computer ( sba ) is booting boot.img.gz

How can I fix both of these issues.
I originally had grub with 3 operating systems installed.
The USB stick through gparted says that it cannot read disklabel H:
:guitar:

---

### Post by jtarin on 2011-07-11
> **YOUWERENTKIDDING said:**
> Now I cannot reformat or modify the usb ( sbd ) partition through gparted and my main computer  ( sba ) is booting boot.img.gzDo you mean to say (**sdb**)and (**sda**)??? /dev/sda being your hard driv and /dev/sdb your USB?

---

### Post by YOUWERENTKIDDING on 2011-07-11
good bye linux, I'll miss your lessons in english and typing

---

### Post by jtarin on 2011-07-11
> **YOUWERENTKIDDING said:**
> good bye linux, I'll miss your lessons in english and typing
I'm just trying to clarify the situation before proceeding with directions.

---

