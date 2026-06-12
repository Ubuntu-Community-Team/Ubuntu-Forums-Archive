---
title: "Wine problems with Ubuntu 10.10"
date: 2010-10-24
forum: New to Ubuntu
---

### Post by Beinlaus on 2010-10-24
Hey,

I'm having problems when i try to install windows games or other programs using wine, it says something like the program/file isn't executable. I'm a new Ubuntu user and i use Ubuntu 10.10.

---

### Post by Elfy on 2010-10-24
make the file executable

Wherever it is - right click - properties - permissions tab - enable the exec flag at the bottom

---

### Post by Anutesyn on 2010-10-24
> **forestpiskie said:**
> make the file executable

Wherever it is - right click - properties - permissions tab - enable the exec flag at the bottom

[IMG]http://img529.imageshack.us/img529/5971/screenshot1ly.png[/IMG]

---

### Post by avinaba on 2010-11-22
I tried to make the file executable but it switches back back to being non-executable the moment I click the check box (the check vanishes), also tried to chmod 777 with sudo has no effect, btw I'm trying to run the utorrent.exe

---

### Post by sandyd on 2010-11-22
> **avinaba said:**
> I tried to make the file executable but it switches back back to being non-executable the moment I click the check box (the check vanishes), also tried to chmod 777 with sudo has no effect, btw I'm trying to run the utorrent.exe

```

wget -c http://winezeug.googlecode.com/svn/trunk/winetricks
chmod 667 winetricks
./winetricks utorrent
```

---

