---
title: "Help Getting from 8.04 to 10.4"
date: 2010-07-08
forum: New to Ubuntu
---

### Post by ityro on 2010-07-08
Need some help/advice on an upgrade (fresh install if upgrade fails) from 8.04 LTS to 10.4 LTS.  My system is dual boot Ubuntu/XP and has a separate Home partition.

Upgrade Question:
1. Should I remove Avast! Antivirus (not in repositories) before upgrade and reinstall  after? If YES how do I remove it?


Fresh Install Question:  (Pls see screenshot of GParted) I have seen many examples of partitions but when I looked at my own I found “media” and decided I do not want to mess with it as I have no idea what it's for, so:
1. Can I simply click on partition hda2 (system) and click on format (ext3)?






My System:  Dual boot Ubuntu 8.04 (separate home folder) with XP on a HP COMPAQ   nx9010 Notebook,  Intel Pentium 4 CPU 2.66GHz,  706MB RAM,  40GB HDD,  USB 2.0,  CD-R Drive,  Floppy Drive,  80GB External HDD.  Single user for home use only.

---

### Post by S.R on 2010-07-08
> **ityro said:**
> 
Upgrade Question:
1. Should I remove Avast! Antivirus (not in repositories) before upgrade and reinstall  after? If YES how do I remove it?

I would ... use the remove function of the command line such as: rm (file name) or if your are unsure of part of the file name  do something like rm avast*

> Fresh Install Question:  (Pls see screenshot of GParted) I have seen many examples of partitions but when I looked at my own I found &#8220;media&#8221; and decided I do not want to mess with it as I have no idea what it's for, so:
1. Can I simply click on partition hda2 (system) and click on format (ext3)?

You are have some material in your media folder. I would let the installer do its job and then when it cam time just have it format the partition how you desire.

Couldn't you just do an apt-get dist-upgrade? 



> My System:  Dual boot Ubuntu 8.04 (separate home folder) with XP on a HP COMPAQ   nx9010 Notebook,  Intel Pentium 4 CPU 2.66GHz,  706MB RAM,  40GB HDD,  USB 2.0,  CD-R Drive,  Floppy Drive,  80GB External HDD.  Single user for home use only.

---

### Post by ityro on 2010-07-08
Thank You for a quick response. You have given me things to check out. Thanks again.

---

### Post by ityro on 2010-07-08
S.R I finally found Avast in Synaptic under the name avast4workstation and did a complete removal. No problems and for me, avoids the opportunity of foot wounds. Thanks.

---

### Post by S.R on 2010-07-08
> **ityro said:**
> S.R I finally found Avast in Synaptic under the name avast4workstation and did a complete removal. No problems and for me, avoids the opportunity of foot wounds. Thanks.

Roger that. Good work!

---

