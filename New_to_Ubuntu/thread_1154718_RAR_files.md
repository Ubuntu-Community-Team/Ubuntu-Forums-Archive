---
title: "RAR files"
date: 2009-05-10
forum: New to Ubuntu
---

### Post by RandomP on 2009-05-10
Hey guys, I was wondering if anyone could help me get RAR support in Archive Manager. I do not want to run Wine and use Winrar through that. Thanks!

---

### Post by collinp on 2009-05-10
Open a Terminal and run:
```
sudo apt-get install unrar
```That should fix your issues.

---

### Post by RandomP on 2009-05-10
Thank you.

---

### Post by ashmew2 on 2009-05-10
> **Hellow said:**
> Open a Terminal and run:
```
sudo apt-get install unrar
```That should fix your issues.

Wouldnt he also need to install rar if he needs to make RAR files ?

```
sudo apt-get install rar unrar

```

If you need all the extras like MS fonts etc , 

```

sudo apt-get install ubunt-restricted-extras
```

---

### Post by aravindc26 on 2009-05-15
just go to add/remove search for rar.........
install the .......wolla......its.........:Ddone

---

### Post by LowSky on 2009-05-15
asmew you command is typed wrong, you forgot a u

```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by carml on 2009-05-15
As far as I know the unrar package is meant to be used to uncompress the .rar files,the rar package is avaible for free only for a limited period of time,if you want it after that time you have to pay it.;)

---

### Post by juanp.contreras on 2009-05-16
Hi...
I adder unrar from synaptic. Whenever I want to unrar files I can see them in the archiver utility, but  if I try to extract them nothing happens (i.e. it only creates the supposed directory but none of the files are extratecd...). Trying with terminal, unrar output "failed" for every file...

---

### Post by carml on 2009-05-26
Maybe the file is corrupted or it's a fake .rar file,some days ago I downloaded any .rar files I thought were compressed slides I needed,but those were all porn file with a .rar extension.
I hope this message may help you.:)

---

