---
title: "Chmod"
date: 2010-01-26
forum: New to Ubuntu
---

### Post by thgthg on 2010-01-26
Hi, I have a folder called /mnt/media owned by root. The group "mediagroup" shall have wr-rights in the folder and all subfolders. I have tried the CHMOD-comand, but can't get it right. Grateful for some help in this matter.

---

### Post by Morbius1 on 2010-01-26
Actually, what you're asking for is more complicated than it looks.

[B]*First the easy part: Ownership.*
[/B] 
If you want the directory and everything in it to be owned by root and accessible by mediagroup:

```
sudo chown -R root:mediagroup /mnt/media

```[B][I]Second the complicated part: Permissions
[/I][/B] 
> The group "mediagroup" shall have wr-rights in the folder and all subfolders.You can't set a directory to "rw-" A directory has to have the execute bit set or else you'll never be able to open it. So the problem becomes how do I recursively set all directories to rwx and all files to rw- for group.

I think this does it. But it must be done in two steps:

```
sudo find /mnt/media -type f -print0 | xargs -0 sudo chmod 660
sudo find /mnt/media -type d -print0 | xargs -0 sudo chmod 770

```All files will be "-rw-rw----"
All directories will be "drwxrwx---"

I think that's what you wanted anyway ;)

---

### Post by bodhi.zazen on 2010-01-26
Ownership and permissions are dependent on the file system.

Is the file system ext4 ? fat ? ntfs ?

---

### Post by thgthg on 2010-01-27
Tnx Morbius1, I´l test this as soon as possible 

Filesystem is EXT3

---

### Post by Diametric on 2010-01-27
I just used my disk utility and disk usage analyzer and can't seem to ffigure out how to determine the type of file system i'm using.  Pretty sure it's ext4, but if someone wanted to check, how would they?

---

### Post by thgthg on 2010-01-27
Thank you for the CHMOD advise, it works perfect.

To Diametric, you can use GParted to check the filesystem

---

### Post by Morbius1 on 2010-01-27
You might want to mark this "Solved" 

(To mark your thread solved, go to **Thread Tools** and select [B]Mark this thread as solved) 

[/B]Because I'm pretty sure I'll forget how to do this myself and may have to search the forms to find it again.[B] :lol:
[/B]

---

### Post by thgthg on 2010-01-29
Tnx for the remark.
I looked for the "SOLVED-tool" but could not find it.
I'l do it right away

---

