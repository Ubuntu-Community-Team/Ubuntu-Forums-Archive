---
title: "[SOLVED] /root/.local/share/Trash  issue?"
date: 2008-12-17
forum: New to Ubuntu
---

### Post by mapes12 on 2008-12-17
I've been using ```
gksu nautilus
```as a quick way to delete some files that need root access. Then recently noticed that the size of my Filesystem has been getting bigger and bigger to the extent that I have no room left on my / partition. So I did some digging around and found that the files that I had deleted using gksu nautilus are still in my system at /root/.local/share/Trash inside two directories, on called files and the other called info. Would it be safe to get rid of them with command line ```
sudo rm -rf /root.local/share/Trash/*
```

---

### Post by drs305 on 2008-12-17
Yes, you can. Using "sudo rm" anything always involves some risk if you get the command wrong but the command you posted is correct. 

There are other ways to delete root's trash as well. See this howto:
[http://ubuntuforums.org/showthread.php?t=898573]("http://ubuntuforums.org/showthread.php?t=898573")

If you use 'gksudo nautilus', the deleted files end up in root's trash and cannot be deleted by normal users. And use SHIFT-DELETE to delete the actual Trash files or the files might just be deleted to ... the trash folder!  ;-)

---

### Post by PartisanEntity on 2008-12-17
See also here:

[http://ubuntuforums.org/showpost.php?p=6378607&postcount=2](http://ubuntuforums.org/showpost.php?p=6378607&postcount=2)

---

