---
title: "Ubuntu Low disk space warning.. though i've moved some to host (windows)"
date: 2010-12-22
forum: New to Ubuntu
---

### Post by mockie on 2010-12-22
[CENTER]hi all.. i'm new here =)
[/CENTER]
 
i got low disk space warning.. then i moved some files (about 600MB) to wind*** partition.. but i still get that warn.. so i try to restart (300MB warn about disk before restart).. but i still get that warn even smaller free disk warning (95MB)... is that a virus? CMIIW.. sorry if my english is bad =)

thanks.
mockie

---

### Post by Verbeck on 2010-12-22
how much did you allocate to the ubuntu partition?
try using the disk usage analyser in applications>accessories to find which folder is taking up the space

also run *sudo apt-get clean*  from a terminal to clear out the download archives

---

### Post by ironic.demise on 2010-12-22
Empty the trash can?

---

### Post by mockie on 2010-12-22
@ironic : yes i did it.. but didnt work :'(


@verbeck : 6 or 7 GB. can i upgrade it without re-install the ubuntu? how?


thanks.

---

### Post by BbUiDgZ on 2010-12-22
> **mockie said:**
> @ironic : yes i did it.. but didnt work :'(


@verbeck : 6 or 7 GB. can i upgrade it without re-install the ubuntu? how?


thanks.

try using gparted to increase the partition size

---

### Post by Hippytaff on 2010-12-22
whats the output of
```

df -h

```or
```

sudo fdisk -l

``` Thats a lowercase L rather than an upper case i.

---

### Post by mockie on 2010-12-22
@hippy taff :

Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2550    20482843+   7  HPFS/NTFS
/dev/sda2            2551        9728    57657285    f  W95 Ext'd (LBA)
/dev/sda5            2551        5100    20482843+   7  HPFS/NTFS
/dev/sda6            5101        9728    37174378+   7  HPFS/NTFS

---

### Post by Hippytaff on 2010-12-22
I can't see whats what here. As suggested above, boot from a livecd, run gparted and see if you can rearrange some partitions to make room...if you get stuck post a screen shot of your gparted.

Edit -> also I'm not au fait with the HPFS filesystem hence not being to sure about whats going on here :-)

---

### Post by Verbeck on 2010-12-22
i'm not sure whether a 10.04/10.10 wubi install can be expanded...

---

### Post by Hippytaff on 2010-12-22
wubi!? well I should have read the opening post more thoroughly...thought I was missing something when I couldn't see the expected partition info, so obvious now :roll:

I would suggest a 'real' install if you intend using ubuntu for any length of time ;-)

---

