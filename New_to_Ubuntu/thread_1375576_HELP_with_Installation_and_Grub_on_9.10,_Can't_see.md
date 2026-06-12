---
title: "HELP with Installation and Grub on 9.10, Can't see my Windows partition at boot"
date: 2010-01-08
forum: New to Ubuntu
---

### Post by fparri on 2010-01-08
Hi guys, anyone can suggest me how to modify my grub configuration in order to have my windows OS appear at boot time. Windows is on /dev/sda2, but at boot time I am only shown its setup, on /dev/sda1.

> 
Disco /dev/sda: 120.0 GB, 120034123776 byte
255 testine, 63 settori/tracce, 14593 cilindri
Unità = cilindri di 16065 * 512 = 8225280 byte
Identificativo disco: 0x7ab852fc

Dispositivo Boot      Start         End      Blocks   Id  System
/dev/sda1               1         262     2098176   27  Sconosciuto
/dev/sda2   *         263       11024    86438286+   7  HPFS/NTFS
/dev/sda3           11025       14593    28667992+   5  Esteso
/dev/sda5           14229       14593     2931831   82  Linux swap / Solaris
/dev/sda6           11025       14228    25736067   83  Linux

---

### Post by cariboo on 2010-01-08
if you run:

```
sudo update-grub
```

in a terminal it should detect your Windows installation.

---

### Post by fparri on 2010-01-08
I actually solved the problem by running the proposed upgrades. Probably one of those rerun grub-update ;)

---

### Post by daimaru on 2010-01-08
> **fparri said:**
> I actually solved the problem by running the proposed upgrades. Probably one of those rerun grub-update ;)
then could you please mark this thread as "SOLVED" since i just wasted my time clicking on it :) . sorry but i just clicked a bunch of threads that should have already been marked as solved so i thought maybe people dont realize that there is an option to do this(thread tools -> mark solved). it really helps people browsing the forums to not look at solved threads and waste time reading all the stuff posted until one gets to the bottom and reads .... thx did that works fine cya ...duh. 

this is not meant as an insult just an advice.

---

