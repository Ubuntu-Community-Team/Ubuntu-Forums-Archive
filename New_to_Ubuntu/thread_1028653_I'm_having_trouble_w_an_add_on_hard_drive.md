---
title: "I'm having trouble w/ an add on hard drive"
date: 2009-01-02
forum: New to Ubuntu
---

### Post by new_2_Intrepid on 2009-01-02
Hi, I just recently installed 8.10 on an wd 160Gb sata drive ..(no problem)
well I just added an wd 80Gb ide drive w/win2000 on it and i'm having problems trying to keep it as a slave... I installed 8.10 on it and now it keeps loading it instead of my sata ... How do I fix it???

---

### Post by Kellemora on 2009-01-02
Hi New 2

Check your GRUB configuration file and move the one you want to boot first to the top of the list.

GRUB boots from the topmost entry, so if you installed the experimental 8.10 program last, it will boot first.

TTUL
Gary

---

### Post by egalvan on 2009-01-02
You probably need to change the boot order in the bios.

---

### Post by new_2_Intrepid on 2009-01-03
yeah I got it thanks all... I just plugged it in after I updated the computer and all and it just uses it as a slave

---

### Post by superprash2003 on 2009-01-03
please mark thread as SOLVED.. under thread tools

---

