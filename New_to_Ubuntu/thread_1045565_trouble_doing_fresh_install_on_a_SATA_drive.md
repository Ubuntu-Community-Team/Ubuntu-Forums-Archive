---
title: "trouble doing fresh install on a SATA drive"
date: 2009-01-20
forum: New to Ubuntu
---

### Post by evencoil on 2009-01-20
Ok, so I'm not a complete beginner, but this is a beginner-esqe problem so I think this is the right place.

I'm trying to install Kubuntu 8.04 on a brand new system with a solitary fresh SATA drive.

First problem was the Kubuntu installation didn't find the SATA drive. So I changed it to AHCI in the BIOS and that solved that problem.

Set up my partitions manually for the first time (perhaps I erred here):
  15 GB at /
  8 GB swap
  rest at /home

   All of them ext3 and "primary partitions" (is that right?)

Then when I reboot I get Error 17: Cannot mount selected partitions. Tried disabling ACHI and trying again, but same thing.

Can anyone help? Thanks!

---

### Post by blueridgedog on 2009-01-20
If you are posting off of the liveCD, perhaps you can post the output of

```
sudo lshw
```

and

```
sudo fdisk -l
```

---

### Post by evencoil on 2009-01-22
yeah those would always fail to show a drive.

i found out what was wrong though. there's another option in the bios called "onboard SATA/IDE" which you can set to ACHI and then it worked.

so for anyone who finds this in the future this was for a WD Caviar on a Gigabyte GA-EP45-UD3R

in the bios should have "RAID/ACHI" set to ACHI and "onboard SATA/IDE" set to ACHI as well. The other permutations didn't work for me.

---

