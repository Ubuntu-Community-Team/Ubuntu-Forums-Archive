---
title: "New vaio z custom SSDs causing problems?"
date: 2010-06-21
forum: New to Ubuntu
---

### Post by A Feyn Man on 2010-06-21
So my laptop got stolen and I'm looking to replace it.
I have never found a laptop seemed to be tailored specifically for me than the new vaio z series (vpcz1190x), but I've done some searching and it looks like since they have custom SSDs (not 2.5" and not 1.8") there will be problems with Ubuntu compatibility, namely trim. There are intel drivers that support trim on this bad boy for windows of course, but not linux.

I read in a previous post about this thread:
[https://lists.launchpad.net/sony-vaio-z-series/]("https://lists.launchpad.net/sony-vaio-z-series/")
But these address very specific issues such as microphone and such.
I of course don't want to just throw Ubuntu on a dual boot on this custom SSD if trim isn't supported. Also I have heard that since the drives are in RAID0 trim could be more difficult, but the one I would be getting would only have one 128GB SSD which sony says is in RAID0 (though I thought that was only possible with multiple disks).
I want to know if anyone knows of ANY working linux distro for this laptop? 

Also what are the drawbacks if I have Win7 on half the drive with TRIM and a linux distro on the other half without TRIM?

I'm really looking for any help at all.

---

### Post by masteler on 2010-07-12
Yes!

I have the same problem as you heard about. 

I've been bought a Vaio vpZ1 with HD 256GB SSD (4 x 64GB SSD).

I' tried with Ubuntu 10.4 LTS unsuccessfully. An error occurs when starting caused by the RAID 0.
By the moment I run w7, amd I'm waiting for time and help to return on. 


I supose you could prepare a dual boot, which was'nt easy for me, when I try, I had same problems with disk array.

Good luck!

---

### Post by Paqman on 2010-07-12
Trim isn't supported in the current kernel we've got in Ubuntu. The next version due out in October will support Trim for Ext4, so as long as your drive's firmware supports Trim you can enable it by adding an option to that drive/partition's entry in /etc/fstab.

> **A Feyn Man said:**
> 
Also what are the drawbacks if I have Win7 on half the drive with TRIM and a linux distro on the other half without TRIM?


They're on separate partitions, so they're completely independent of each other. You could be Trimming away happily under Win7 on it's NTFS partition, and not Trimming at all under Ubuntu on Ext4 and it would be no problem. It's just that the Ubuntu side will suffer the performance degrade of not having Trim. The amount of performance you'd lose between now and getting a Trimming kernel in October would be infinitesimal.

---

### Post by A Feyn Man on 2010-07-15
Paqman could you help out here:

[http://ubuntuforums.org/showthread.php?t=1531121&highlight=RAID](http://ubuntuforums.org/showthread.php?t=1531121&highlight=RAID)

---

