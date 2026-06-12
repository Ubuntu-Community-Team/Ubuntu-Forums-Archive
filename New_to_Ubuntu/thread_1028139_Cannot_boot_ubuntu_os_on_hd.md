---
title: "Cannot boot ubuntu os on hd"
date: 2009-01-02
forum: New to Ubuntu
---

### Post by derrick_how on 2009-01-02
Hello,
      I m totally new on Ubuntu . Hv just install ubuntu on a new slave hd with a running xp win os on the ms hd. Hv tried booting up ubuntu with the new hd but to no avail. I can only boot  with the installing cd on . pls help 
Thks.

---

### Post by Michael.Godawski on 2009-01-02
> **derrick_how said:**
> Hello,
      I m totally new on Ubuntu . Hv just install ubuntu on a new slave hd with a running xp win os on the ms hd. Hv tried booting up ubuntu with the new hd but to no avail. I can only boot  with the installing cd on . pls help 
Thks.

hi, 

can you boot into windows?

Are you getting any error messages during the booting process?

---

### Post by rolnics on 2009-01-02
Welcome to the forums.

Firstly I assume you are running Ubuntu Ibex (8.10)?

Are you still able to boot windows?

If you could run this command in terminal when you have booted into Ubuntu via the cd, this will help the rest of us.

If you click on the following:- 
Applications -> Accessories -> Terminal

That will run a terminal session for you and then if you copy the below code and copy the results back here.

```
sudo fdisk -l
```

---

### Post by derrick_how on 2009-01-04
Hi, 
Sorry for the late reply. I tried to use the terminal but got error opening until today. The result are below:

Disk /dev/sda: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xba64ba64

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1829    14691411    7  HPFS/NTFS
/dev/sda2            1830        2434     4859662+   5  Extended
/dev/sda5            1830        2434     4859630+   7  HPFS/NTFS

Disk /dev/sdb: 8455 MB, 8455200768 bytes
255 heads, 63 sectors/track, 1027 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x97494974

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1026     8241313+   7  HPFS/NTFS

Pls help THks

---

### Post by derrick_how on 2009-01-05
> **Michael.Godawski said:**
> hi, 

can you boot into windows?

Are you getting any error messages during the booting process?

No error Message except it carrying on reading the cdrom disk.
I can choose to boot from window xp n it boot. I must choose to boot from ubuntu then ESC and choose start from cd. Hope it can help to solve the problem. Anyway hv read some articles from the forum that ubuntu cannot boot up on NTFS system file hd. Is it true . My hd is ntfs format. 
Thks

---

