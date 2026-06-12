---
title: "dual boot 2 HDDs"
date: 2010-01-28
forum: New to Ubuntu
---

### Post by albert s on 2010-01-28
I would like to dual boot ubuntu 9.10 and XP, both OS are on different hard drives.
is this possible? ubuntu is on the master HDD, at the minute ubuntu just boots normally and I can see my windoze drive in my folders, but I dont have an option to boot to it on start up.
I would like to keep XP for running my scanner/printer etc as it doesnt work brilliantly from ubuntu just yet, and a few other bits and bobs, though the rest of the XP disc will be used for ubuntu files.
do I need to re-install ubuntu? I have backed up all my data just in case.
thanks.

---

### Post by phidia on 2010-01-28
It should or could be just a matter of reinstalling grub. Usually the ubunbtu installer searches for other OSes and will add them to grub's boot menu but perhaps you elected not to do that or the XP drive wasn't connected when you installed ubuntu? Search for reinstall grub and you should have a howto.
Ubuntu grub docs [here]("https://help.ubuntu.com/community/GrubHowto").

---

### Post by undecim on 2010-01-28
I simple grub update should fix this. Just open up a terminal and type```
sudo update-grub
```and the script will automatically find any OSs on any attached hard drives and add them to the grub list.

---

### Post by albert s on 2010-01-28
ah, sorry folks,
I think Im using Grub2,
I assume that makes a difference.

---

### Post by phidia on 2010-01-28
There's a link from the link I provided previously for grub2 or just go [here]("https://help.ubuntu.com/community/Grub2").

---

### Post by Paqman on 2010-01-28
> **albert s said:**
> ah, sorry folks,
I think Im using Grub2,
I assume that makes a difference.

If you're using Grub2 then the update-grub command above should work. It's Grub Legacy that you'd have to mess about with adding Windows manually.

---

