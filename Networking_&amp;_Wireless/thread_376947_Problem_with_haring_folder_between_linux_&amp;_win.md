---
title: "Problem with haring folder between linux &amp; windows"
date: 2007-03-05
forum: Networking &amp; Wireless
---

### Post by tiptip on 2007-03-05
Hello,

I'm trying to set a folder sharing between windows & linux, i entered to system->administration->shared folders , and chose the folder i'm sharing and the workgroup. (i did the same in windows).

Now, when i work on linux i can see all windows shared files. but when i enter from windows and try to see the shared files on linux i see the link to the linux computer as seen in the picture :
[[IMG]http://img111.imageshack.us/img111/286/sharedph8.th.jpg[/IMG]](http://img111.imageshack.us/my.php?image=sharedph8.jpg)
but when i try to enter the computer asks me for a login/pass , which login/pass do i need to enter ? my normal linux account user/pass doesnt work for it.

(i'm using Ubuntu 6.10 and Win XP).

---

### Post by tiptip on 2007-03-05
I found the problem, i didn't set the the SAMBA user/pass
```
sudo smbpasswd -a username
```

---

