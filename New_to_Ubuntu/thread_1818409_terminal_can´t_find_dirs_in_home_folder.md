---
title: "terminal can´t find dirs in home folder"
date: 2011-08-04
forum: New to Ubuntu
---

### Post by gronater on 2011-08-04
Hi,

I´m using Ubuntu 11.04 and when i try to change, copy, move and other commands dirs in the terminal It says No such file or directory.

```
philip@philip-pc:~$ pwd
/home/philip
philip@philip-pc:~$ ls
Bureaublad  Documents  examples.desktop       Music     Public     Ubuntu One
Desktop     Downloads  Firefox_wallpaper.png  Pictures  Templates  Videos
philip@philip-pc:~$ cd ~/pictures
bash: cd: /home/philip/pictures: No such file or directory
philip@philip-pc:~$ cd /home/philip/downloads
bash: cd: /home/philip/downloads: No such file or directory
philip@philip-pc:~$ 

```

Hope you can help,

Gronater

---

### Post by spiky001 on 2011-08-04
Try with a capital Downloads , Pictures etc

---

### Post by gronater on 2011-08-04
> **spiky001 said:**
> Try with a capital Downloads , Pictures etc

Yup that works, stupid of me :P
Thank you very much!

---

