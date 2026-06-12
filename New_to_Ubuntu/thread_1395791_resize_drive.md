---
title: "resize drive"
date: 2010-02-01
forum: New to Ubuntu
---

### Post by DarinB on 2010-02-01
I have 
/dev/sda1 windows vista
/dev/sda5   /
/dev/sdb1   /home
/dev/sdc1   /mnt/music

can i??? resize the mnt/music and use it to put on it my home folder
then use the /dev/sdb drive not the /home as my os hdd,,,i think the os drive is in trouble and may die one day,,i pray not! 
BTW each drive is 750GB more than enough space for all my stuff.
thanks everyone,
i bet if Taurus reads this he will know,,,,that guy is a genius!!!

---

### Post by Bachstelze on 2010-02-01
Moving your /home folder to another partition is perfectly possible, our favourite aysiu has [a tutorial]("http://psychocats.net/ubuntu/separatehome") for that. While moving your root partition is also technically feasible, I wouldn't recommend it. Just doing a fresh install will probably be quicker if you're not familiar with the OS.

---

### Post by tom.swartz07 on 2010-02-01
> **DarinB said:**
> I have 
/dev/sda1 windows vista
/dev/sda5   /
/dev/sdb1   /home
/dev/sdc1   /mnt/music

can i??? resize the mnt/music and use it to put on it my home folder
then use the /dev/sdb drive not the /home as my os hdd,,,i think the os drive is in trouble and may die one day,,i pray not! 
BTW each drive is 750GB more than enough space for all my stuff.
thanks everyone,
i bet if Taurus reads this he will know,,,,that guy is a genius!!!

Could you paste the output of 
```
sudo fdisk -l
```

It would give us a better idea of the size of your drive and what we have to work with. Also, a screencap of gparted would be sweet too.

---

### Post by DarinB on 2010-02-02
Disk /dev/sda: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x11446ceb

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       48092   386296828    7  HPFS/NTFS
/dev/sda2           48093       91201   346273042+   5  Extended
/dev/sda5           48093       90066   337156123+  83  Linux
/dev/sda6           90067       91201     9116856   82  Linux swap / Solaris

Disk /dev/sdb: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x790b9718

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       91201   732572001   83  Linux

Disk /dev/sdc: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x790b971b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       91201   732572001   83  Linux

---

### Post by warfacegod on 2010-02-02
If you are concerned about your HDD's then I suggest testing them. System> Admin.> Disk Utility. Compare the results of that with gsmartcontrol.

```
sudo apt-get install gsmartcontrol
```

Once it installs, you will find it under: Applications> System Tools> GsmartControl. Use the extended self-test in gsmart.

---

