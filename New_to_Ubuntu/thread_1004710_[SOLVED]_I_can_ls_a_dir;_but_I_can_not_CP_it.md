---
title: "[SOLVED] I can ls a dir; but I can not CP it?"
date: 2008-12-07
forum: New to Ubuntu
---

### Post by gmgj on 2008-12-07
I do not understand why I can ls a location, but cp cannot find it

I try this
gmgj@myUbuntu:~/Public$ cp -R /media/CB/CookBook  /home/gmgj/Public/CB2
cp: cannot stat `/media/CB/CookBook': No such file or directory

media/CB is there:

gmgj@myUbuntu:~/Public$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
....
/dev/sda7            188883572    303760 178984996   1% /home
/dev/sda3             52436156   3810440  48625716   8% /media/Volatile
/dev/sda2            209720540    770164 208950376   1% /media/CB

ls /media/CB/Cookbook is there

gmgj@myUbuntu:~/Public$ ls /media/CB/Cookbook

Beverages                    hello.php                sitemap.txt
BrucetoVOX.html              KitchenEquipment         TermsDictionaryGlossary
...

FSTAB entries

/dev/sda3 /media/Volatile ntfs-3g  auto,users,uid=1000,gid=100,dmask=027,fmask=137,utf8  0  0
/dev/sda2 /media/CB ntfs user,ro,noexec,nls=utf8,umask=0222 0 0

---

### Post by taurus on 2008-12-07
Maybe

```
cp -R /media/CB/CookBook/*  /home/gmgj/Public/CB2
```

---

### Post by gmgj on 2008-12-07
if only, that was the case, I tried it, it says, "Gary you still are a chump", opps i mean, "cannot stat"

cp -R /media/CB/CookBook/*  /home/gmgj/Public/CB2
cp: cannot stat `/media/CB/CookBook/*': No such file or directory

---

### Post by vanadium on 2008-12-07
CookBook is not the same as Cookbook.

---

### Post by newbee70 on 2008-12-07
What happens if you.


sudo cp -R /media/CB/CookBook/*  /home/gmgj/Public/CB2

---

### Post by Idefix82 on 2008-12-07
Edit: Vanadium spotted the mistake.

Just a tip: if you hit the tab key while typing a folder name, this name will be completed if it is identified uniquely by what you have typed. If you haven't typed in enough of the name to identify it then hitting the tab key twice you will see all possibilities to complete the word. This make working with the terminal much faster and much less error prone.

---

### Post by lovelyvik293 on 2008-12-07
@newbee70 It will copy the containts of CookBook folder to CB2 folder.'*' means all containt.

---

### Post by lovelyvik293 on 2008-12-07
@vanadium is right there is problem with case in CookBook.

---

### Post by newbee70 on 2008-12-07
> **lovelyvik293 said:**
> @vanadium is right there is problem with case in CookBook.

Yeah I finally reread the first post and saw it.

thats what working with windows does to ya---you forget about case.

---

