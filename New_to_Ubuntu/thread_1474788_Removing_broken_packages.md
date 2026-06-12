---
title: "Removing broken packages"
date: 2010-05-06
forum: New to Ubuntu
---

### Post by ozbolt on 2010-05-06
I've been searching for solution but could find an answer (silly me).
There are 2 screenshots:

[img]http://www.shrani.si/f/2j/sl/zv2WCpG/screenshot.png[/img]
[img]http://www.shrani.si/f/3v/bm/49NECyOA/screenshot-1.png[/img]

The same thing happens all 3 packages then removing.

I think they are broken because they were interupted while installation with a reboot from my younger brother (which should have happened, Canonical -- just another papercut to solve). I don't seem to be able to remove or really install them with Gnome UI or that recovery mode. What is the command, folks?

Thanks

---

### Post by jbrown96 on 2010-05-06
```
sudo apt-get -f install
``` will usually fix the broken installation, then you should be able to remove them.

---

### Post by ozbolt on 2010-05-09
Thank you for help... But still:
[[img]http://www.shrani.si/t/1O/46/WBFPvpL/screenshot.jpg[/img]](http://www.shrani.si/?1O/46/WBFPvpL/screenshot.png)

---

### Post by jbrown96 on 2010-05-09
Try ```
sudo dpkg-reconfigure -a
``` Could you also just paste the output into a set of code tags. The screenshots are not searchable for others that may have your same problem.

---

### Post by linuxman94 on 2010-05-09
I had this problem once.  The solution is quite simple. Open up a root nautilus to this folder.  

```
sudo nautilus /var/lib/dpkg/info/
```

Delete the files with apport-hooks-mediabuntu, libmp4v2-0, and  unrar in the name and you should be set.

---

### Post by ozbolt on 2010-06-01
Linuxman94, it worked. Thanks

---

