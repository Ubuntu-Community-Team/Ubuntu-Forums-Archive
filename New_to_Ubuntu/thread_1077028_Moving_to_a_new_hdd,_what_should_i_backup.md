---
title: "Moving to a new hdd, what should i backup?"
date: 2009-02-21
forum: New to Ubuntu
---

### Post by LastWho on 2009-02-21
Hi,
**What i have:** ubuntu 8.04 installed on 40 GB hdd
[B]
What i plan to do:[/B] [INDENT]- moving to a new hdd 250 GB, 
- dual booting ubuntu 8.10 and windows7 (for gaming and readiris - OCR), 
- then adding my old hdd (after probably formatting it).
[/INDENT]i m willing to partition the new drive like this: 30 GB unpartitioned, 17 GB for root (/), 3 GB swap, and the rest a home partition --> installing ubuntu then windows (on the unpartitioned space) (by following some threads i found on this forum)

**Questions:**
 1- i assume that i could access easily my home partition from both windows7 and ubuntu, right?

2- what do i need to back up from my old drive, i backed up some personal files on dvds, what else could/should i back up? 
(e.g i installed hundred of applications with ubuntu 8.04, could i back up that?)

3- after dual booting on the new hard disk, could i mount the old one and access to files on it, or i have to format it before?


thank you so much for ur help

[FONT=Arial Narrow][SIZE=1](sorry for my bad eng)[/SIZE][/FONT]

---

### Post by T2manner on 2009-02-22
I would just backup your home folder.
I've never tried to backup anything else.

---

### Post by logos34 on 2009-02-22
like t2manner says, your /home files are the only ones you need to backup.  None of the applications or programs you installed on 8.04 will be worth saving since 8.10 probably uses newer/different versions.

Look[ here ]("http://www.psychocats.net/ubuntu/mountlinux")for how to format and mount the old disk for use in 8.10

good luck

---

### Post by hyperyoda on 2009-02-22
> **LastWho said:**
> Hi,
**What i have:** ubuntu 8.04 installed on 40 GB hdd
[B]
What i plan to do:[/B] [INDENT]- moving to a new hdd 250 GB, 
- dual booting ubuntu 8.10 and windows7 (for gaming and readiris - OCR), 
- then adding my old hdd (after probably formatting it).
[/INDENT]i m willing to partition the new drive like this: 30 GB unpartitioned, 17 GB for root (/), 3 GB swap, and the rest a home partition --> installing ubuntu then windows (on the unpartitioned space) (by following some threads i found on this forum)

**Questions:**
 1- i assume that i could access easily my home partition from both windows7 and ubuntu, right?

2- what do i need to back up from my old drive, i backed up some personal files on dvds, what else could/should i back up? 
(e.g i installed hundred of applications with ubuntu 8.04, could i back up that?)

3- after dual booting on the new hard disk, could i mount the old one and access to files on it, or i have to format it before?


thank you so much for ur help

[FONT=Arial Narrow][SIZE=1](sorry for my bad eng)[/SIZE][/FONT]


It's a good idea to backup your $HOME directory as well as any config files you setup such as /etc/X11/xorg.conf 

Zach

---

### Post by LastWho on 2009-02-22
thanks guys for ur help, especialy logos34! the tutorial u gave me is great!!

i ve a question plz: i m willing to make the home partition an ext3! 
i know that with the Ext2 IFS i can read and write from an ext3 but can i install windows programs on it??

thanks

---

