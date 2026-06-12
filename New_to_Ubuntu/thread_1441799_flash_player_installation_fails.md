---
title: "flash player installation fails"
date: 2010-03-29
forum: New to Ubuntu
---

### Post by mronegear on 2010-03-29
Hey Users!

i am running Ubuntu 9.10 from a 4GB Flasdrive.

I try to install a adobe flash player for mozilla that i can few u-tube videos, but it fails...

it says: "dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem."

and if i do so, it says:" dpkg: Fehler beim Parsen, in Datei »/var/lib/dpkg/updates/0019« nahe Zeile 0:
 EOF nach Feldname »«"

so what can i do to solve the prob?

thanx for replay

---

### Post by undecim on 2010-03-29
> **mronegear said:**
> Hey Users!

i am running Ubuntu 9.10 from a 4GB Flasdrive.

I try to install a adobe flash player for mozilla that i can few u-tube videos, but it fails...

it says: "dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem."

and if i do so, it says:" dpkg: Fehler beim Parsen, in Datei »/var/lib/dpkg/updates/0019« nahe Zeile 0:
 EOF nach Feldname »«"

so what can i do to solve the prob?

thanx for replay

I think you have run out of disk space... Never a pretty situation

That second message (as translated by Google) basically says that /var/lib/dpkg/updates/0019 suddenly breaks off when it should be giving more info. This sounds like it used up the last free block on your 4GB drive. I bet if you were to look at the size of that file, it would be exactly a multiple of 4KB.

What you need to do to fix this is first, FREE UP SOME DISK SPACE. You don't want to do a lot of anything on your system with a full disk, because that can lead to data loss (i.e. as a program frees up a block to rewrite a configuration file, another process will use up that block. That config file has nowhere to be stored, so its lost.) Empty your trash, Shift+Delete some unimportant files, and run "sudo aptitude clean" 

Once you have some free space, then we can fix dpkg and any other problems that have arised from this.

---

### Post by mronegear on 2010-03-29
ok, running out of diskspace sounds possible...

i checked the drive and ist says, that still 1,5 GByte free Diskspace available, but maybe that is not enought?!

I did partion 2 GB for permanent Files on the stick, the Rest ist for the Ubuntu Kernel.

thanx,

Frank

---

### Post by undecim on 2010-03-29
> **mronegear said:**
> ok, running out of diskspace sounds possible...

i checked the drive and ist says, that still 1,5 GByte free Diskspace available, but maybe that is not enought?!

I did partion 2 GB for permanent Files on the stick, the Rest ist for the Ubuntu Kernel.

thanx,

Frank

So you created this with the USB startup disk creator? If so, then the free space shown on another computer is completely irrelevant. There is a file on the thumb drive that contains all other files and acts as a drive. Once that file is filled up, the USB system will consider all space to be used up.

If you have another Ubuntu system, you can mount the file and remove files from there, which would be safer than booting the thumb drive.

---

### Post by QIII on 2010-03-29
If it might help, a better translation is

```
dpkg: parse error, in file '/var/lib/dpkg/updates/0019' near line  0:  EOF after field name ''
```

[]("http://dict.tu-chemnitz.de/deutsch-englisch/Viel.html")Viel Erfolg.

---

