---
title: "help mounting hard drive from a dual boot Windows/Ubuntu computer"
date: 2010-06-13
forum: New to Ubuntu
---

### Post by johnrcomeau on 2010-06-13
I'm brand new to Ubuntu, so please have patience about this posting.

I have a Eee netbook PC that dual boots Windows and Ubuntu.  A friend helped me install this, and in the bootup process there's a screen about the "Windows Boot Loader", so it seems that maybe Ubuntu is installed in sort of a subordinate role to Windows on this Eee netbook.

I want to be able to access and modify the files on this hard drive from a different Ubuntu (desktop) computer.  When I plug the drive into the Ubuntu desktop and run 'sudo fdisk -l', I get the following results:

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       13055   104857600    7  HPFS/NTFS
/dev/sdb2           13055       29094   128835584    f  W95 Ext'd (LBA)
/dev/sdb3           29094       30400    10485760   1b  Hidden W95 FAT32
/dev/sdb4           30400       30401       16064+  ef  EFI (FAT-12/16/32)
/dev/sdb5           13055       29094   128834560    7  HPFS/NTFS

If I run 'sudo mount /dev/sdb1 /mnt', I can successfully mount the sdb1 partition.  Likewise, I can mount sdb3 and sdb5.  However, I have not been able to find the Ubuntu file system on these partitions.  sdb1, sdb3 and sdb5 all seem to contain Windows-oriented files.  Am I right in suspecting that it is either sdb2 or sdb4 that contains the Ubuntu file structure?  How do I mount these drives?

Based on what I read in
  [https://help.ubuntu.com/community/AutomaticallyMountPartitions](https://help.ubuntu.com/community/AutomaticallyMountPartitions)

I tried the following command to mount sdb4:
  sudo mount -t vfat /dev/sdb4 /mnt

However, this produces an error message:

  mount: wrong fs type, bad option, bad superblock on /dev/sdb4,
         missing codepage or helper program, or other error
         In some cases useful info is found in syslog - try
         dmesg | tail  or so

The syslog error doesn't help me much either:

  VFS: Can't find a valid FAT filesystem on dev sdb4.

Isn't "EFI (FAT-12/16/32)" system referred to as 'vfat' in Linux?  Why won't this partition mount?  Also, is there any way to mount sdb2 (W95 Ext'd (LBA))?  It appears that this file system is not supported by Ubuntu.  I definitely hope my files are under /dev/sdb4 because that looks more promising.

Thanks,
John

---

### Post by cogier on 2010-06-13
How did you install Ubuntu and which version?

There is no partition that is formatted in Ext which is Ubuntu's favoured format. 

At first glance I would say Ubuntu is not installed as Ubuntu controls the boot process on a dual boot system not Windows.

---

### Post by oldfred on 2010-06-13
You have a wubi install that is inside you main windows install, unless you directed to install to another windows partition (windows may call it a drive but it is a partition)

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)
The Windows-based Ubuntu Installer (Wubi) allows you to install and uninstall Ubuntu from within Microsoft Windows. It lets a Microsoft Windows user try Ubuntu without risking any data loss due to disk formatting or partitioning.

Your Ubuntu is just in a file in the NTFS partition. 
/ubuntu/disks/root.disk

---

### Post by Don1500 on 2010-06-13
> Device Boot Start End Blocks Id System
/dev/sdb1 * 1 13055 104857600 7 HPFS/NTFS
/dev/sdb2 13055 29094 128835584 f W95 Ext'd (LBA)
/dev/sdb3 29094 30400 10485760 1b Hidden W95 FAT32
/dev/sdb4 30400 30401 16064+ ef EFI (FAT-12/16/32)
/dev/sdb5 13055 29094 128834560 7 HPFS/NTFS
sdb1 is your boot partition with 104gb
sdb2 looks like it may be where Ubuntu is but it looks like you have it on a Virtual Machine on an extended Windows partition 12 gb
sdb3 is you hidden recovery for windows
sdb4 & sdb5 are other partition but I'm not sure what.

could you open Gparted (in Ububtu, SYSTEM=>ADMINISTRATION=>GPARTED and show a screenshot of this drive?

If you don't have gparted it is available from the synaptic package manager or in terminal ```
sudo apt-get install gparted
```

---

### Post by johnrcomeau on 2010-06-13
oldfred, thanks for your answer.  It does appear to be a Wubi installation.  I was able to mount my Ubuntu files using the command

  sudo mount /dev/sdb5 /mnt
  sudo mkdir /vdisk
  sudo mount -o loop /mnt/ubuntu/disks/root.disk /vdisk

Now I have access to the entire Ubuntu file structure under /vdisk.

I don't really like this Wubi system though because I'm not really a Windows user and have no need for the Windows installation.  My next step is switch over to a pure Ubuntu system.  Now that I have access to these files, I feel a lot better.

Thanks,
John

---

