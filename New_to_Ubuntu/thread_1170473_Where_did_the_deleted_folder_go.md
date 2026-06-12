---
title: "Where did the deleted folder go?"
date: 2009-05-26
forum: New to Ubuntu
---

### Post by resander on 2009-05-26
I wanted to delete a directory named GameX that was adorned with a lock. I did sudo nautilus (which started the Filebrowser GUI), right-clicked on the directory and selected 'Move to Deleted items folder'. The directory disappeared from the Filebrowser view, but it did not go into the recyclebin.

I rebooted and issued 'locate GameX' from commandline:
ken@ken-desktop:~$ locate GameX
/home/ken/.local/share/Trash/info/GameX.trashinfo

Going to Trash directory shows directory files which contains deleted files and directory info which holds info such as time of deletion of the deleted files. 

ken@ken-desktop:~$ cd .local/share/Trash
[email]ken@ken-desktop:~/.local[/email]/share/Trash$ ls -l
drwx------ 2 ken ken 12288 2009-05-26 14:35 files
drwx------ 2 ken ken 12288 2009-05-26 14:35 info

[email]ken@ken-desktop:~/.local[/email]/share/Trash$ ls -l files
[email]ken@ken-desktop:~/.local[/email]/share/Trash$ ls -l info
-rw-r--r-- 1 ken ken  0 2009-05-26 13:26 GameX.trashinfo

The files directory is empty and the GameX.trashinfo file is empty.

I need the freed space, but where did it go? OR what can I do to find out?

---

### Post by drs305 on 2009-05-26
Root's deleted trash goes to /root/.local/share/Trash/files. Take a look there:
```

gksudo nautilus /root/.local/share/Trash/files

```

Note: When running graphical apps with admin privileges, it is preferred to use "gksudo" or "gksu" rather than "sudo". It is explained here:
[http://www.psychocats.net/ubuntu/graphicalsudo]("http://www.psychocats.net/ubuntu/graphicalsudo")

---

### Post by resander on 2009-05-26
Many thanks.

Just what I needed and more!

110% brilliant.

---

