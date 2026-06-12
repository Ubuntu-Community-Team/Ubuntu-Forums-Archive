---
title: "How to copy or move a folder to another location using terminal?"
date: 2009-12-28
forum: New to Ubuntu
---

### Post by WestCity on 2009-12-28
Hi, "cp" or "mv" commands works only for files, but how to copy (or move) a folder to another location?..

---

### Post by mjitkop on 2009-12-28
To copy a folder, try:

```
cp -r Folder CopiedFolder
```To move a folder, try:

```
mv Folder NewPath
```

I just tried and it seemed to work for me.

Example:

```
basement@BASEMENT-UBUNTU:~$ ls
Desktop           fix_citrix_cert_v0.2.sh~  Pictures  Share       Videos
Documents         Music                     PkgId     Templates
examples.desktop  nls                       Public    Ubuntu One

basement@BASEMENT-UBUNTU:~$ ls Pictures
Dektop Backgrounds  Photos

basement@BASEMENT-UBUNTU:~$ cp -r Pictures Pics
basement@BASEMENT-UBUNTU:~$ ls
Desktop           fix_citrix_cert_v0.2.sh~  Pics      Public     Ubuntu One
Documents         Music                     Pictures  Share      Videos
examples.desktop  nls                       PkgId     Templates
basement@BASEMENT-UBUNTU:~$ cd Pics
basement@BASEMENT-UBUNTU:~/Pics$ ls
Dektop Backgrounds  Photos

basement@BASEMENT-UBUNTU:~$ mv Pics Documents
basement@BASEMENT-UBUNTU:~$ ls
Desktop           fix_citrix_cert_v0.2.sh~  Pictures  Share       Videos
Documents         Music                     PkgId     Templates
examples.desktop  nls                       Public    Ubuntu One
basement@BASEMENT-UBUNTU:~$ cd Documents
basement@BASEMENT-UBUNTU:~/Documents$ ls
Pics
basement@BASEMENT-UBUNTU:~/Documents$ cd Pics
basement@BASEMENT-UBUNTU:~/Documents/Pics$ ls
Dektop Backgrounds  Photos
```

---

### Post by phillw on 2009-12-28
> **WestCity said:**
> Hi, "cp" or "mv" commands works only for files, but how to copy (or move) a folder to another location?..

Hi the -a, or the -r option in cp will look after directories. Using -a ....

```
 ~home/phillw/directory_to_copy
```
wanting to go to 
```
 ~home/phillw/backups
```
would be 

```
 cp -a /home/phillw/directory_to_copy /home/phillw/backups/ 
```

That would place directory_to_copy as a directory under ....backups/

mv can be dangerous - as you lose the initial file, and if you're moving a large file & your system dies (power cut) then you could well wave good bye to the file.

Regards,

Phill.

---

### Post by phillw on 2009-12-28
BTW, the intro to CLI stuff is over here --> [https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)

Phill.

---

### Post by WestCity on 2009-12-28
Thanks! :)

---

