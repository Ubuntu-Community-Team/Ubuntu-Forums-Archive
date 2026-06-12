---
title: "HPLIP cannot scan with LaserJet m2727"
date: 2009-01-18
forum: New to Ubuntu
---

### Post by eagle416 on 2009-01-18
I have the new version of HPLIP (2.8.12), and when I click on scan with the m2727, it says something like "cannot contact device". Bottom line is it doesn't work.

I checked all the HPLIP stuff, apparently there was a problem with scanning incompatibility issues with this model before, but it apparently is supported now.

My other computer uses the LaserJet 3390, an almost identical model, which works perfectly.

By the way, the LaserJet m2727 is connected via USB, and it works perfectly for all other functions. I have tried reinstalling HPLIP.

---

### Post by NewJack on 2009-01-18
Not sure, but the printer database at [www.openprinting.org](www.openprinting.org) states that scanning isn't currently supported for your printer

[http://openprinting.org/show_printer.cgi?recnum=HP-LaserJet_M2727](http://openprinting.org/show_printer.cgi?recnum=HP-LaserJet_M2727)

---

### Post by eagle416 on 2009-01-18
weird, because on the HPLIP website, under Ubuntu 8.10, under Scanning, it says "Yes"

I guess it's mistaken.

---

### Post by NewJack on 2009-01-19
Well the entry on [www.openprinting.org]("http://www.openprinting.org") usually has feedback from a user who has tested the driver.  Not to say that it is 100% correct, but apparently that person had the same issue as you.

EDIT: Did you look at the note attached to the SCAN option:

 3 Scan supported means that PC initiated scan using a SANE compatible software application is supported over parallel, USB, or network (depending on I/O connection). Information on digital sending products is covered in note 9, below.
 
and

9 Device supports digital sending, not standard scanning protocols. See this [KB article]("http://hplipopensource.com/node/302") for more info.

So it looks like you have to go through X-Sane (If you haven't done that already).

Good Luck

---

### Post by eagle416 on 2009-01-19
Okay...... So it looks like scanning won't work because of it's digital coding. I even tried using X-Sane, and it didn't work. I'll try my local (other) computer with it, and see if it's computer bug.

In the meantime, is there a workaround?

---

### Post by NewJack on 2009-01-19
I can't say that I know of one, sorry.

---

### Post by eagle416 on 2009-02-01
I was able to solve the issue with 

```

sudo hp-setup

```

I don't know why that didn't happen automatically happen when I installed HPLIP, but it works now.

---

