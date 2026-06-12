---
title: "Backing Up in Ubuntu 9.10"
date: 2010-12-01
forum: New to Ubuntu
---

### Post by daniell59 on 2010-12-01
Backing Up in ubuntu 9.10
I am planning to do a clean install to Ubnutu 10.10.
There a few things that I would like to back up.

Address Book

Bookmarks

Photos

I would appreciate it if someone could explain to me the best way of doing this.

Thanks

---

### Post by ibizatunes on 2010-12-01
[https://help.ubuntu.com/community/BackupYourSystem/TAR](https://help.ubuntu.com/community/BackupYourSystem/TAR)
create a separate /home in the next install and then you don't need to worry about it in the future!

---

### Post by AngusH on 2010-12-01
A tarball of your home partition would do the trick,
Not at a linux box right now so I can't test this but I think the commands your after would be```
cd / 
sudo tar -xavf home.tar.gz home
```
(the cd is because we can't create the file in a dir we're in)
Then you can just copy that to a USB stick, and restore it on the new install.
Angus

---

### Post by daniell59 on 2010-12-01
> **AngusH said:**
> A tarball of your home partition would do the trick,
Not at a linux box right now so I can't test this but I think the commands your after would be```
cd / 
sudo tar -xavf home.tar.gz home
```
(the cd is because we can't create the file in a dir we're in)
Then you can just copy that to a USB stick, and restore it on the new install.
Angus

Tried it an got the following.

No such file or directory
tar: Error is not recoverable: exiting now

Thanks the same

---

### Post by AngusH on 2010-12-01
I'm an idiot.
Same thing, but change the start of the second line to ```
sudo tar -cavf home.tar.gz home
``` and give that a whirl. Hopefully I've got it right this time :).
Angus

---

