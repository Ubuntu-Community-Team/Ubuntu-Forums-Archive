---
title: "Is possible to bind differents folders in one?"
date: 2007-12-29
forum: Networking &amp; Wireless
---

### Post by germandt on 2007-12-29
hi, I've got my music in different folders like /disc1, /disc2,... in order to know in which dvd they are. But I'd like to mount all these discXX in one folder called /Music. Is this possible?

---

### Post by runris on 2008-01-07
I'm working om kinda the same thing now.
You kan mount them with "sudo mount --bind /somefolder/disk1 /home/you/Music" filling in the correct adresses. But the problem for me is that after a reboot, they are unmounted again.. Still working on that..

Anyone else?

---

### Post by Predator[23rd] on 2008-01-07
try **ln -s /disc1 /Music/disc1** (symbolic links: [http://en.wikipedia.org/wiki/Symbolic_link](http://en.wikipedia.org/wiki/Symbolic_link))

then mount **/Music**, all your discs will show as subdirectories ...

---

### Post by Predator[23rd] on 2008-01-07
> **runris said:**
> I'm working om kinda the same thing now.
You kan mount them with "sudo mount --bind /somefolder/disk1 /home/you/Music" filling in the correct adresses. But the problem for me is that after a reboot, they are unmounted again.. Still working on that..

Anyone else?

keyword: [B]fstab
[/B]
google for it ...

---

### Post by runris on 2008-01-07
got it after some (a hell of a lot) google'ing :)

---

