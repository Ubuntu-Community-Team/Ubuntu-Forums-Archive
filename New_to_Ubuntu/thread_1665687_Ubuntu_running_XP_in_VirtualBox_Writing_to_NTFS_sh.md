---
title: "Ubuntu running XP in VirtualBox: Writing to NTFS share corrupts filesystem!!"
date: 2011-01-12
forum: New to Ubuntu
---

### Post by JesperSP on 2011-01-12
Hi everyone!,

I have a Dell Vostro 1500 laptop with a 640GB samsung drive. I run windows XP and Ubuntu dual-boot system. I have 3 partitions on my drive:

dev/sda1 (NTFS) C: WinXP (OS) 160GB
dev/sda2 extended
 | dev/sda5 (NTFS) D: DATA 290GB
 | dev/sda6 (ext4) Ubuntu OS (150GB)
 | dev/sda7 (linux-swap).

I run VirtualBox under ubuntu because I need to have specific windows software running: MS Word+ Endnote. 

I have all my documents in a folder on the D: drive, which is accessible from both my XP installation and my Ubuntu installation. When I run XP in the virtualBox under ubuntu, I access the D:\documents folder in VirtualBox as a shared folder. This appears to work well, but I have had at least 4 instances where files on the D: Drive have become corrupted after files were written via XP in the virtualbox. It has occured when saving games in Civilization2 running in the virtualbox, and much worse it happened when writing my endnote library. I booted into XP and it appeared that half the files in the folder was missing, and CHKDSK in XP found several erros. Unfortunately CHKDSK couldn't restore my Endnote library, so the file was deleted!! Fortunately I had a recent backup of the file (Crashplan), but I have become very suspicious about accessing the D: drive using virtual box. 

My question is: Is it safe to write files to NTFS drives under ubuntu? - Is there something I can do to make it more safe?

Cheers,
Jesper

---

### Post by b0b138 on 2011-01-12
When you say accessing it as a shared folder, do you mean a network share, or a vbox shared folder?

---

### Post by JesperSP on 2011-01-20
It's a VBox shared folder... I have the D: drive mounted in Read/write mode, and can access the files in ubuntu also. I experienced the Ubuntu NTFS file system error again, without even using Vbox: I copied 3 files of ½ GB each from my dropbox folder in Ubuntu to my D: drive. All 3 files got corrupted :(

So I guess it's win7-time for me until this error gets fixed :(

Cheers,
Jesper

---

### Post by JesperSP on 2011-01-20
It's a VBox shared folder... I have the D: drive mounted in Read/write mode, and can access the files in ubuntu also. I experienced the Ubuntu NTFS file system error again, without even using Vbox: I copied 3 files of ½ GB each from my dropbox folder in Ubuntu to my D: drive. All 3 files got corrupted :(

So I guess it's win7-time for me until this error gets fixed :(

Cheers,
Jesper

---

