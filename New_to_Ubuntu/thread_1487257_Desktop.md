---
title: "Desktop"
date: 2010-05-18
forum: New to Ubuntu
---

### Post by bigal1932flying on 2010-05-18
Since upgrading to 10.04 my GNOME Desktop works fine (apart from some minor glitches) my KDE Desktop however appears to be broken.
How can I fix this?

---

### Post by DangerOnTheRanger on 2010-05-18
Maybe try:
```

sudo apt-get purge kubuntu-desktop
sudo apt-get install kubuntu-desktop

```Doing the same with ubuntu-desktop might fix GNOME.

---

### Post by sandyd on 2010-05-18
> **bigal1932flying said:**
> Since upgrading to 10.04 my GNOME Desktop works fine (apart from some minor glitches) my KDE Desktop however appears to be broken.
How can I fix this?

try ```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by bigal1932flying on 2010-05-18
Response from sudo apt-get purge Kubuntu-desktop "nothing to remove".
From sudo apt-get update && sudo apt-get upgrade. No change in situation.
I also tried "sudo apt-get install kubuntu-desktop" with no real change.

---

### Post by Ozymandias_117 on 2010-05-18
> **bigal1932flying said:**
> Response from sudo apt-get purge Kubuntu-desktop "nothing to remove".
From sudo apt-get update && sudo apt-get upgrade. No change in situation.

It's all lowercase. ```
sudo aptitude purge kubuntu-desktop
```
If it still says nothing to remove, well, you don't have KDE installed :D just type ```
sudo aptitude install kubuntu-desktop
```

---

### Post by bigal1932flying on 2010-05-19
Tried #5 Kubuntu is now working.
Thanks for your help.

---

