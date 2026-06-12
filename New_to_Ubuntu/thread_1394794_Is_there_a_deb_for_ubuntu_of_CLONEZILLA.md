---
title: "Is there a deb for ubuntu of CLONEZILLA ?"
date: 2010-01-31
forum: New to Ubuntu
---

### Post by frenchn00b on 2010-01-31
unfortunaltely there is nothing into the repositories :( :KS no deb

[http://clonezilla.org/download/sourceforge/](http://clonezilla.org/download/sourceforge/)

---

### Post by Temposs on 2010-01-31
generally you don't need to install clonezilla on your existing install, so it's not necessary to have  a deb of it. Clonezilla is primarily intended to be used in a LiveCD environment, so you get the ISO, load it on a CD, and boot your machine with it.

---

### Post by frenchn00b on 2010-01-31
> **Temposs said:**
> generally you don't need to install clonezilla on your existing install, so it's not necessary to have  a deb of it. Clonezilla is primarily intended to be used in a LiveCD environment, so you get the ISO, load it on a CD, and boot your machine with it.


I can run it with ```
qemu -hda clonezilla-stable.iso 
``` and try to backup my harddisk, i.e. the other partitions on my pc ?

---

### Post by Temposs on 2010-01-31
sure, if you like. just saying the primary use.

I prefer using a proper backup program for regularly backing up my files.

---

### Post by Torrilin on 2010-01-31
> **frenchn00b said:**
> I can run it with ```
qemu -hda clonezilla-stable.iso 
``` and try to backup my harddisk, i.e. the other partitions on my pc ?

Clonezilla works to clone your hard disk partitions. This means it can create a backup of an installed operating system (like your linux install, or a windows install) that will boot and run correctly. Having a clone partition is very useful if you're not the only user on a machine, or if you do a lot of experimental stuff that can seriously damage your install. It also works well if you're maintaining many computers where the installed OS needs to be identical. For most home Linux users, a LiveCD will work fine as a recovery tool, and Clonezilla is the wrong kind of tool.

It is not by any stretch the tool I'd pick for regular backups of my books, music, photographs and programming files. For regular data files, I simply keep copies on a large spare USB key. An external USB hard drive can work also. If any of my files were of financial value, I'd pay for a Dropbox or Ubuntu One account (or something similar) so I could maintain an off site backup. A single backup is not a good strategy when you've got files that are critical to your income.

If you decide that you do need Clonezilla, definitely use it as a LiveCD, and figure out a sensible location for the OS clone partition(s) to go on your network.

---

### Post by ororo on 2012-06-24
This post is quite old, anyway I found the solution today:

[http://packratstudios.com/index.php/2008/04/20/how-to-setup-clonezilla-on-linux-ubuntu-quick-start-guide/](http://packratstudios.com/index.php/2008/04/20/how-to-setup-clonezilla-on-linux-ubuntu-quick-start-guide/)

It tells there is a repository where you can download the packages for both clonezilla and drbl (so, also the .deb if you neeed it).

Just add 
```
deb http://free.nchc.org.tw/drbl-core drbl stable
```

to your [FONT="Courier New"]/etc/apt/source.list[/FONT].

---

### Post by Rodney9 on 2012-06-24
Clonezilla Tutorial showing you both how to backup and restore an operating system

[http://www.dedoimedo.com/computers/clonezilla.html](http://www.dedoimedo.com/computers/clonezilla.html)

Rodney

---

### Post by coffeecat on 2012-06-24
Old thread closed.

---

