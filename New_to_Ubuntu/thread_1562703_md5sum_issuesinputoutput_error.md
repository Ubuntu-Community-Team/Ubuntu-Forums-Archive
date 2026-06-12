---
title: "md5sum issues/input/output error"
date: 2010-08-28
forum: New to Ubuntu
---

### Post by vivek40 on 2010-08-28
Hi.. I just downloaded an iso image of Linux mint  , did an md5sum check on it and there was no issue. 
Then I burnt the iso image on a cd using brasero. However when i do an md5sum check on the cd using:
md5sum /dev/cdrom
I get the below error. The output is the same even if I use sudo md5sum.
md5sum: /dev/cdrom: Input/output error

However I am able to access the contents of the cd... can someone please help.
AM using Lucid

---

### Post by Ozymandias_117 on 2010-08-28
> **vivek40 said:**
> Hi.. I just downloaded an iso image of Linux mint  , did an md5sum check on it and there was no issue. 
Then I burnt the iso image on a cd using brasero. However when i do an md5sum check on the cd using:
md5sum /dev/cdrom
I get the below error. The output is the same even if I use sudo md5sum.
md5sum: /dev/cdrom: Input/output error

However I am able to access the contents of the cd... can someone please help.
AM using Lucid

1. Find out the exact size of your .iso with (While in the directory of the .iso)```
ls -l
```
2. Divide that number by 2048 You should get a whole number. If not, go to 4

3. Type ```
sudo dd if=/dev/cdrom bs=2048 count=*number_you_got_from_step_2* | md5sum
```This WILL take a while, when it's done, you should have your md5sum!

4. ONLY DO THIS IF YOU DIDN'T GET A WHOLE NUMBER ON 2! ```
dd if=/dev/cdrom bs=1 count=*number_you_got_from_ls_command* | md5sum
``` This will take a lot longer than the other option, so only do it if you don't get a whole number (Which would usually mean there was a problem with the .iso to start with.)

---

