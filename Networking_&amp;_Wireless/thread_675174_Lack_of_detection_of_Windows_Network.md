---
title: "Lack of detection of Windows Network"
date: 2008-01-22
forum: Networking &amp; Wireless
---

### Post by amcg06 on 2008-01-22
A few months ago when I started with Ubuntu it networked perfectly via my ethernet ADSL router with my XP Home (SP2) computer. Then it went belly up for no obvious reason, internet connectivity remained on both PCs and I am able to access the XP pc directly via its IP address. But Ubuntu is unable to detect any computers on the "Windows Network" in Nautilus, or in Konqueror and won't pick up the XP machine by its share name. 

Meanwhile XP can't detect the Ubuntu machine on the Windows Network either. Though that isn't a great concern to me as all I want to do is access the music and printer with ease on the XP box. 

Anyway, any ideas?

---

### Post by rosegarden78 on 2008-01-22
You can always share information over wireless home network or Internet.  Just run Apache Web Server on both computers.  I think they have Apache for Windows now.  Set up a local-host on both systems.  Then share files by placing them in /var/www and accessing them using the ip address range specified by your router or network. ie. 192.168.2.1 & 192.168.2.2 if the base for your network is 192.168.2.1.

---

### Post by rosegarden78 on 2008-01-22
> **amcg06 said:**
> 

Meanwhile XP can't detect the Ubuntu machine on the Windows Network either. Though that isn't a great concern to me as all I want to do is access the music and printer with ease on the XP box. 

Anyway, any ideas?

Sorry ... your Ubuntu box is in EXT3 file format most likely.  The default format for XP is NTFS unless you manually select FAT32 during installation.  If you have an NTFS/EXT3 combo you'll need to download shareware, freeware, software or compile source code from the Internet that will interface or mount an EXT3 file system in Windows.

If your need NTFS in Ubuntu check the repositories for NTFS and FUSE.  May I suggest you convert your NTFS drive to FAT32 because it is the most compatible format.  My LACIE 250GB USB Hard Drive came from the factory with FAT32.

---

### Post by dannyboy79 on 2008-01-22
> **amcg06 said:**
> A few months ago when I started with Ubuntu it networked perfectly via my ethernet ADSL router with my XP Home (SP2) computer. Then it went belly up for no obvious reason, internet connectivity remained on both PCs and I am able to access the XP pc directly via its IP address. But Ubuntu is unable to detect any computers on the "Windows Network" in Nautilus, or in Konqueror and won't pick up the XP machine by its share name. 

Meanwhile XP can't detect the Ubuntu machine on the Windows Network either. Though that isn't a great concern to me as all I want to do is access the music and printer with ease on the XP box. 

Anyway, any ideas?

in your /etc/samba/smb.conf file, is your workgroup the same for all machines? if it's not, than it won't see any computers through nautilus. also, it order to get name resolution between windows and linux, you either need to edit your hosts file on linux and lmhosts on windows OR use winbind per this guide: [http://ubuntuforums.org/showthread.php?t=288534&highlight=mount+samba+shares](http://ubuntuforums.org/showthread.php?t=288534&highlight=mount+samba+shares)

---

