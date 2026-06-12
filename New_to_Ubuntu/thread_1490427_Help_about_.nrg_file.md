---
title: "Help about .nrg file"
date: 2010-05-22
forum: New to Ubuntu
---

### Post by vooolt on 2010-05-22
Hi All,
I've a program in a .nrg file, how can i open it as "Daemon tools" in windows.
i installed a program called: giSOMount, but i couldn't open the file.
Thanks

---

### Post by zeroseven0183 on 2010-05-22
I'm not very familiar with daemon tools in Windows but there's a simple program called **nrg2iso** (install it from Ubuntu Software Center) that can convert .NRG to .ISO. After installing, open a Terminal and type

```
nrg2iso sourcefile.nrg outputfile.iso
```Then you can probably use gISOmount to use the ISO.

---

### Post by ssj6akshat on 2010-05-22
install acetoneiso by typing in a terminal

sudo apt-get install acetoneiso

or got to software centre and install it.

You will be able to mount your file like daemon tools.

---

### Post by vooolt on 2010-05-22
Thanks 4 help
 when i write:
sudo apt-get install acetoneiso
 i recieve:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package acetoneiso

What does that mean?

---

### Post by zeroseven0183 on 2010-05-26
Hmmm.. It should get AcetoneISO from the repos. Anyway, you can get it from [http://www.getdeb.net/updates/Ubuntu/9.10/?q=acetoneiso](http://www.getdeb.net/updates/Ubuntu/9.10/?q=acetoneiso) if it still does not work.

---

### Post by vooolt on 2010-06-13
Thanks again.
but after opening the link and click "Install now"
it starts to download, after downloading, i receive:
"Could not find package 'acetoneiso' "

any new suggestions?

---

