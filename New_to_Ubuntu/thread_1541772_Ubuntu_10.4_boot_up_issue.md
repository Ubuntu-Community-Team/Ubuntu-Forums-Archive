---
title: "Ubuntu 10.4 boot up issue"
date: 2010-07-29
forum: New to Ubuntu
---

### Post by altruist77 on 2010-07-29
Hi,
    I have a laptop with Windows 7 and Ubuntu installed in seperate  partitions. When I boot up the computer I get options to boot either in  windows 7 or Ubuntu. Yesterday I updated Ubuntu to 10.4 version. I have  been having issues with grub rescue, which was rectified an hour ago.  Now I can boot up into windows 7, but when I try to boot into Ubuntu, I  get a GRUB screen as below:
```
GNU GRUB Version 1.97~beta4
[Minimal Bash-like line editing is supported. For the first words TAB  lists possible command completions. Anywhere else TAB lists possible  device/File completeions.]
sh: grub>
```When I type 'ls' I get the following list
(loop0) (hd0) (hd0,4) (hd0,3) (hd0,2) (hd0,1) 

Please help me to restore Ubuntu. I have no prior knowledge about the  command prompt scripts. Kindly help me through with some patience.
Thank you
Best wishes
Arul

---

### Post by oldfred on 2010-07-29
Your update should not have installed grub to the MBR. wubi works thru the windows boot loader.

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

You can reinstall from a liveCD a windows style boot loader or run fixMBR from windows repair.

Restore basic windows boot loader - universe enabled from Ubuntu or liveCD
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
May show error messages about the rest of lilo missing, ignore, we just want MBR

---

### Post by bcbc on 2010-07-29
> **altruist77 said:**
> Hi,
    I have a laptop with Windows 7 and Ubuntu installed in seperate  partitions. When I boot up the computer I get options to boot either in  windows 7 or Ubuntu. Yesterday I updated Ubuntu to 10.4 version. I have  been having issues with grub rescue, which was rectified an hour ago.  Now I can boot up into windows 7, but when I try to boot into Ubuntu, I  get a GRUB screen as below:
```
GNU GRUB Version 1.97~beta4
[Minimal Bash-like line editing is supported. For the first words TAB  lists possible command completions. Anywhere else TAB lists possible  device/File completeions.]
sh: grub>
```When I type 'ls' I get the following list
(loop0) (hd0) (hd0,4) (hd0,3) (hd0,2) (hd0,1) 

Please help me to restore Ubuntu. I have no prior knowledge about the  command prompt scripts. Kindly help me through with some patience.
Thank you
Best wishes
Arul
You still have the wubildr from Ubuntu 9.10. The first thing I'd try is replacing this as per: [http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10)

If that fails, you should try booting from a live CD, loopmounting your root.disk and checking that it is ok. i.e. the mount is successful.

EDIT I see from the bootinfoscript in your other post that the wubi root.disk is ok. Also, backup the original wubildr before replacing.

EDIT if it still doesn't work, you can try the latest wubildr I generated from the version you are on (10.04.1). But try the simplest option first.

---

