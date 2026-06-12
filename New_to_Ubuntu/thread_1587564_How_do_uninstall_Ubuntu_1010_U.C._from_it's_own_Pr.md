---
title: "How do uninstall Ubuntu 10:10 U.C. from it's own Primary Partition?"
date: 2010-10-03
forum: New to Ubuntu
---

### Post by mikodo on 2010-10-03
Hello again,

I as stated in an earlier thread here                           [I'm putting Ubuntu 10.10 R.C. and Deja-dup throught their paces, but one question.]("http://ubuntuforums.org/showthread.php?t=1587525")
I put a new install of Maverick R.C. on it's own Primary Partition. I was experimenting, with Maverick, Deja-dup, and the manual installer. 

I want to delete the Maverick partition, and just continue Lucid for now. The last time I had a situation like this was with Hardy as my production OS, with Karmic and Lenny on other partitions. I decided to delete the partitions for Karmic and Lenny in Gparted and hosed either the MBR or Grub and couldn't boot back into Hardy again, and not knowing what to do, I reinstalled Hardy and started over.

I don't want the same problem again in removing the /dev/sda4 partition of Maverick R.C.

**Please tell me how to correctly remove Maverick from my system and still have my excellently running Lucid OS intact. Everything except /dev/sda4, I want to keep with Lucid.        **

See below a screen shot of my partitions in Gparted and results of fdisk -l.  

```
Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x1549f232

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1402    11261533+  83  Linux
/dev/sda2            1403        3503    16876282+  83  Linux
/dev/sda3            3504       15893    99522644+   5  Extended
/dev/sda4           19853       38913   153107482+  83  Linux
/dev/sda5            3504        4140     5116671   82  Linux swap / Solaris
/dev/sda6            4141       15893    94405941   83  Linux




```Thanks.

---

### Post by andrewthomas on 2010-10-03
Just delete the /dev/sda4 partition from lucid and go into synaptic select grub-pc and reconfigure to make sure that the grub2 installed to the mbr is controlled by lucid and not maverick.

---

### Post by mikodo on 2010-10-03
> **andrewthomas said:**
> Just delete the /dev/sda4 partition from lucid and go into synaptic select grub-pc and reconfigure to make sure that the grub2 installed to the mbr is controlled by lucid and not maverick.

Thanks Andrew.

I was a "nervous puppy" this being my only computer, and if the same thing happened as last time, the only recourse again, for me, would have been another new install.

So, I deleted /dev/sda6 (Maverick partition) in Lucid and re-installed  grub-pc in synaptic (only way I could think of configuring it for Lucid), crossed my fingers and rebooted. As you can see, it worked.

```
mikodo@mikodo-desktop:~$  sudo fdisk -l

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x1549f232

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1402    11261533+  83  Linux
/dev/sda2            1403        3503    16876282+  83  Linux
/dev/sda3            3504       15893    99522644+   5  Extended
/dev/sda5            3504        4140     5116671   82  Linux swap / Solaris
/dev/sda6            4141       15893    94405941   83  Linux
mikodo@mikodo-desktop:~$ 


```Thanks again Andrew!

---

