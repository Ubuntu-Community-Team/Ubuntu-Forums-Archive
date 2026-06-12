---
title: "i cant change permissions"
date: 2009-05-26
forum: New to Ubuntu
---

### Post by BeyondMe on 2009-05-26
Hello, at first, excuse me for my unpracticed english hehe

i have a trouble with ubuntu folder and file permissions

the last week i installed ubuntu for my first time, and i can change perfectly file and folder permission, but in the last 2 days, there are some folders that i cant change

i change them but after doing it the permissions were still the same :-S

i try to change it with "sudo nautilus" but it happens again

i try to change it by chmod in a terminal, but the same ...

i change the propietary, and try to change it again, but the same ....

what i have to do to change this permission folders ???

---

### Post by BeyondMe on 2009-05-26
ive installed xampp for linux, and the folder i want to change permissions is in htdocs folder

---

### Post by Lampi on 2009-05-26
maybe you must be root to change them:

sudo su

chmod xyz </path/to/folder>

---

### Post by taavikko on 2009-05-26
Please read the following pieces for information:

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

never ever use chown or chmod on / (root)!

---

### Post by BeyondMe on 2009-05-26
i use chmod and sudo before posting this trouble

is the same, the folder and files have the same permissions .. they dont changeeeee

---

### Post by mcduck on 2009-05-26
> **BeyondMe said:**
> i use chmod and sudo before posting this trouble

is the same, the folder and files have the same permissions .. they dont changeeeee

Are those files/folders on FAT or NTFS partitions? Those file systems don't support file ownerships and permissions as they are used in Linux/Unix systems. The only way to set their permissions is to do it when mounting the drive.

And I feel it should be mentioned here that _you never, ever, should change ownership or permissions of any system directory unless you really know what you are doing_!

---

### Post by BeyondMe on 2009-05-27
no, they arent in a fat partition. they are in opt/lampp/htdocs

---

