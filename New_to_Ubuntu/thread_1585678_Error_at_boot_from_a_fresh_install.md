---
title: "Error at boot from a fresh install"
date: 2010-09-30
forum: New to Ubuntu
---

### Post by MatrimFTW on 2010-09-30
I just reformatted the HDD and installed unbuntu 10.04 and it says restart which is expected and then I receive an error

[4.088504] nForce2_smbus 0000:00:0a.1: error probing SMB1

[11.972019] ata2:SRST failed (errno=-16)




81.960204 ata2: SError: { PHYRdyChg 10B8B Dispar LinkSeq TrStaTrns }

and it continues on and then it screens to black.

---

### Post by andrewthomas on 2010-10-01
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/220706](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/220706)
 
The beginning comments are old but the later ones are current.  
 
This just may help you out.

---

### Post by sikander3786 on 2010-10-01
Please post your hardware specs. Which motherboard, and how many SATA controllers have you got?

---

### Post by MatrimFTW on 2010-10-02
> **sikander3786 said:**
> Please post your hardware specs. Which motherboard, and how many SATA controllers have you got?

  abit Fatality FP-IN9 SLI MB, intel 2.4 quad. 1 HDD Bus, 1 DVD-RW.

Read through the previous link and sadly I'm at a loss. I'm probably not as computer savvy as I should be and so this is a slow learning process. I see the poster in [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/220706](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/220706) suggested switching IDE cable direction as well as using "git" to rebuild the kernel. Cables I can do, but I haven't worked with a command line since DOS and I was 12.

According to the post in [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/595448](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/595448)  its suggested to use 

> diff lucidconfig linux-2.6/.config
3,4c3,4
< # Linux kernel version: 2.6.35-rc3
< # Thu Jun 24 11:15:51 2010
---
 > # Linux kernel version: 2.6.35-rc3-ahci
> # Fri Jun 25 13:21:38 2010
  1646c1646
< CONFIG_SATA_AHCI=m
---
 > CONFIG_SATA_AHCI=y
  1648c1648
< CONFIG_SATA_INIC162X=m
---
 > CONFIG_SATA_INIC162X=y
  1693c1693
< CONFIG_PATA_IT821X=m
---
 > CONFIG_PATA_IT821X=y
  1719c1719
< CONFIG_PATA_MPIIX=m
---
 > CONFIG_PATA_MPIIX=yCan I just type this in from the default line that comes after the error and continue boot (Shift + D) ? Also if you need further info re: my system I'll be happy to add detail.

---

### Post by andrewthomas on 2010-10-02
> **MatrimFTW said:**
> 
According to the post in [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/595448](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/595448)  its suggested to use 
```
diff lucidconfig linux-2.6/.config
3,4c3,4
< # Linux kernel version: 2.6.35-rc3
< # Thu Jun 24 11:15:51 2010
---
 > # Linux kernel version: 2.6.35-rc3-ahci
> # Fri Jun 25 13:21:38 2010
  1646c1646
< CONFIG_SATA_AHCI=m
---
 > CONFIG_SATA_AHCI=y
  1648c1648
< CONFIG_SATA_INIC162X=m
---
 > CONFIG_SATA_INIC162X=y
  1693c1693
< CONFIG_PATA_IT821X=m
---
 > CONFIG_PATA_IT821X=y
  1719c1719
< CONFIG_PATA_MPIIX=m
---
 > CONFIG_PATA_MPIIX=y                      
```Can I just type this in from the default line that comes after the error and continue boot (Shift + D) ? Also if you need further info re: my system I'll be happy to add detail.
Those changes are changes you have to make during the "make menuconfig" stage of compiling the kernel.  There is no way to feed those changes to the kernel at boot.

---

### Post by MatrimFTW on 2010-10-05
Ok so... then what of that post did I miss to solve my problem?

---

