---
title: "map of my drive..windows xp uninstallation"
date: 2011-02-10
forum: New to Ubuntu
---

### Post by dragon1111 on 2011-02-10
hi friends...i installed ubuntu 10.10 alongside windows xp but my computer boots directly into ubuntu..However,i'm in total love with ubuntu that i dont need windows xp anymore and wanna do away with it for good..i've attached the map of my drive as well just to make it easier...How do i uninstall Xp without having to reinstall ubuntu from scratch

---

### Post by Linyx on 2011-02-10
Post the output of :-

```
sudo fdisk -l
```

If you want to uninstall Win-Xp, just Format that Partition which Hold Xp, and type 

```
sudo update-grub
``` in Ubuntu.

---

### Post by searchfgold6789 on 2011-02-10
I saw the screenshot, and it looks like Windows is already gone! Have fun!

---

### Post by dragon1111 on 2011-02-11
@linyx - this is the output of sudo fdisk -l

---

### Post by dragon1111 on 2011-02-11
@searchofgold - But then i have nearly 25GB of unaccounted space on my drive..i thought it must be windows Xp coz i remember having installed ubuntu alonside it

---

### Post by mikewhatever on 2011-02-11
As others pointed out, there is no Windows XP (ntfs file system) in your screenshots, nor is there unallocated space. It's very fortunate indeed that you like Ubuntu. :D

---

### Post by Linyx on 2011-02-11
Their isn't XP Anymore as already pointed by the other members above.......You can better Guess that their aren't any NTFS-Partition...

---

### Post by dragon1111 on 2011-02-12
:guitar: 

thanks guys...basically,my windows Xp was counterfeit and my system kept hanging by the hour...plus it was too friggin slow and was gettin on my nerve.. No such problems now that i've got Ubuntu...and any minor issues i can always get help on the forum 
\\:D/:lolflag:   ):P

---

