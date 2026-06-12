---
title: "XP partition not detected by grub or gparted"
date: 2009-01-12
forum: New to Ubuntu
---

### Post by EastSail on 2009-01-12
Hello everyone

I think I have tied myself up in a real bad spot, and I'd appreciate your help. I tried reading all forums and helps and fixing this on my own first, but so far I have only made things worse. So I'd appreciate your help.

Background:
1- Original set-up: Dell Laptop running XP-SP3
2- Installed Ubuntu from the CD on an 8GB USB stick
3- This caused GRUB to point to the USB stick when loading and I had to have USB in place even if I wanted to go XP
4- I thought I could install grub on XP's hard-disk directly and have two independently bootable disks (one on the HD, and one on the stick).
5- I used grub-install to no avail. Then I used grub CLI and managed to move GRUB off the stick but not onto the HD.
6- Now I could not boot at all from either device.
7- I got the ubuntu CD back, and reinstalled GRUB back on the stick, that works now.
8- I still had no direclty bootable XP hard-disk, and somehow I also managed to lose access to the HD totally. Now I couldn't boot XP at all.
9- I used ms-sys and MBR to fix the master-boot-record and make the XP hard-disk bootable. But that broke things worse.
10- Current situation:
A- When I log into ubuntu from the USB, the computer does not mount the hard-disk (it used to).
B- When I use gparted to see the partitions on the hard-disk, it tells me:
[INDENT]unable to detect the filesystem! possible reasons are:
[LIST]
- The filesystem is damaged
- The filesystem is unknown to GParted
- There is no filesystem available (unformatted)
[/LIST] 
[/INDENT]
C- When I use "sudo fdisk -/dev/sda" it tells me:
> 
Device-----Boot--Start--End------Blocks-----ID----System
/dev/sda1---------1------5-------40131-------de---Dell Utility
/dev/sda2---------6----12160-----97635037+---7----HPFS/NTFS

D- When loading Ubuntu from USB, GRUB reports booting from (HD0,0). This doesn't sound right. USB is my /dev/sdb which should be hd1 in GRUB count. Unless GRUB fails to even see sda, and then it count sdb as HD0.
---
I don't have the XP CD. Is there anyway I can recover the XP boot partition without that CD?

Thanks for all your help.

---

### Post by caljohnsmith on 2009-01-12
In order to get a clearer picture of your setup, how about booting your Live CD (the Ubuntu install CD), download the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to your Ubuntu desktop, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what your booting problem might be.

---

