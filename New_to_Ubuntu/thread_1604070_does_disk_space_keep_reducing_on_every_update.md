---
title: "does disk space keep reducing on every update?"
date: 2010-10-23
forum: New to Ubuntu
---

### Post by olderek on 2010-10-23
hi 
i just want to know if the my disk space keeps reducing every time i update my pc.
recently i installed 10.10 and when ever updates are available, (of 100MB plus),i install them. 
just want to know if i'm loosing my disk space?
any help....
olderek

---

### Post by Verbeck on 2010-10-23
try running **sudo apt-get clean** or [B]sudo apt-get autoclean
[/B]that should delete downloaded archive files

---

### Post by uRock on 2010-10-23
I do my updates via CLI. It tells me how much space will be used/free with the update. Sometimes the updates free up more space than they use. As the new files may be smaller or larger than the ones they are replacing.

---

### Post by A_M_S on 2010-10-23
try also

sudo apt-get autoremove

autoremove is used to remove packages that were automatically installed to satisfy dependencies for some package and that are no more needed.

---

### Post by AngusH on 2010-10-23
Just to extend on what's been said above, purely from personal experience, I find that most updates use some disk space, but it isn't much and occasionally some is actually freed. The reason this happens is that when you download a 100MB update, the files in that update REPLACE files that are already on your system, so only a few megabytes are actually added.
The cleaning commands above will also help to keep disk use as low as possible by deleting old files that APT no longer needs.
Angus

---

