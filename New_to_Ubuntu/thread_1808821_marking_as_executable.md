---
title: "marking as executable"
date: 2011-07-20
forum: New to Ubuntu
---

### Post by yea678 on 2011-07-20
how do i mark a folder/ file as executable?

---

### Post by izbm on 2011-07-20
Right click, go to permissons, should say allow excuting file as a program check the box and click ok :)

---

### Post by skatinjj on 2011-07-20
Open terminal and cd to the directory of the file then run:

```
chmod +x 'filename'
```

---

### Post by izbm on 2011-07-20
sorry ment to add to right click hit PROPRITES Then go to Permissons sorry

---

### Post by skatinjj on 2011-07-20
> **izbm said:**
> Right click, go to permissons, should say allow excuting file as a program check the box and click ok :)

Beat me to it :D

I prefer CLI =P

---

### Post by yea678 on 2011-07-20
> **skatinjj said:**
> Open terminal and cd to the directory of the file then run:

```
chmod +x 'filename'
```

kind new to ubuntu and dont quite get what this means

also i clicked that box and it didnt work

---

### Post by skatinjj on 2011-07-20
chmod is used tochange the permissions of a file i.e read, write, hidden.

+x adds the executable bit making the file executable.

'filename' should be replace with the name of the file your trying to execute i.e execute_me

---

### Post by skatinjj on 2011-07-20
also check out:

```
man chmod
```

---

### Post by mcduck on 2011-07-21
> **yea678 said:**
> 
also i clicked that box and it didnt work
Make sure you aren't trying to change permissions of a file that's located on a FAT or NTFS file system (they are Windows file systems and aren't able to handle Linux permissions) or on any optical media like CD or DVD (which are by design read-only filesystems).

---

### Post by wep940 on 2011-07-21
You'll also need to own the file - if not, you need to use sudo ......, but I believe the chmod syntax changes at that time as you have to decide who besides the owner is to have that permission. I believe it would be something along the way of 
 
sudo chmod -o+x filename  for others not the owner and not in the owners group
 
or for everyone to have execute access:
 
sudo chmod -a+x filename
 
Since you are new to this, you may want to see this web page for a little more information:
 
[http://ss64.com/bash/chmod.html](http://ss64.com/bash/chmod.html)

---

