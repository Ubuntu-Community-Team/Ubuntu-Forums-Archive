---
title: "Sharing Files in XP/Ubuntu on Netbook"
date: 2009-09-14
forum: New to Ubuntu
---

### Post by mark111 on 2009-09-14
I have been trying pretty hard to make dual-boot file sharing work and need some help.  I have a Asus 1005HA netbook (that is, no CD drive) properly set up for dual boot.  I would like to share files when in either environment from the same hard drive.

Here is my journey.  To do so, I understand, I must partition the hard drive (Samba doesn't work if XP is not booted and XP can't see Ubuntu files if Ubuntu is not loaded).  

To partition the hard drive I have to make space, but the main partition can't be unmounted in Ubuntu and is in use and therefore locked using XP utilities.  So I could boot using a USB drive (again, no CD drive in a netbook and a cross-over cable to another computer doesn't work for a network boot).

I have used the USB Start-up Disk Creator to set that up, but there are .exe files and partitions on the USB drive that gparted won't take out, and re-formatting the USB will not wipe those files out as they are protected.

Help, please.  I feel like I have gone down several different paths and gotten stuck each time.  Surely there must be an easier way???  Thanks in advance.

---

### Post by nhasian on 2009-09-14
sharing folders in ubuntu is easy.  just browse to the folder you want with the nautilus file manager.  then right click on the folder and select sharing.  it will ask if you would like to install samba, then your all set.

---

### Post by mark111 on 2009-09-14
Thanks, and that would be the easiest thing.  However, the only directory that is shown on the places/computer screen is a directory called PE, and this directory contains 2 folders (Documents and Settings and Minint) together with about a dozen .bmp files.  The Documents and Settings folder has a few folders inside, but the only file is desktop.ini.

So, I don't have access to the files in My Documents on the hard drive, which is the whole source of the problem and the need to establish a partition. If I could set up file sharing with Nautilus the problem would be solved.

Many thanks for any assistance.

---

### Post by Arla on 2009-09-14
Starting from the beginning, what does the machine currently have installed on it? It sounds (reading between the lines) like it has Ubuntu and you need to install XP as well?

---

### Post by mark111 on 2009-09-14
Thanks.  This machine has XP Home SP3 pre-installed.  I installed Ubuntu 9.04 using the web-installation approach (because this netbook has no CD/DVD drive).  I am now asked at start-up which application I wish to use.

I have changed the Ubuntu/linux kernel to 2.6.30 in order to permit the netbook wireless to work, as the 2.6.28 kernel in Jaunty does not work with the wireless driver for this netbook.  All other changes have been to applications and not to boot or hard drive areas.

According to XP, the current partition situation is with a an EFI partition of 39 MB, a 4.9 GB FAT32 partition that is called PE, and the regular C: partition of 114GB, of which 43 GB are in use.

Ubuntu (according to Gparted) thinks the hard drive has 3 partitions, with the 39 MB partition (sda3) has an unknown file system, with the main one, which is the boot drive (sda1) is in NTFS and the PE drive (sda2) is FAT32. The sizes are the same as in Windows as shown above.  I believe the 39MB partition is the Windows recovery area.

---

### Post by mark111 on 2009-09-14
OK, many thanks folks.  In drafting my last reply I realised that both Ubuntu and Windows were in the SAME partition.  Windows' My Documents and Ubuntu's Documents were just in different places.  I could find the My Documents folder by doing a search on the contents of a distinctively named file in My Documents, which is actually located in /host/documents and settings/*ACCOUNT NAME*/My documents.

All of my exploration of partitions, USB booting, etc, is still not solved by no longer relevant.

Cheers to you all.

---

### Post by nhasian on 2009-09-16
ah okay so you install ubuntu with the wubi windows installer.  in the future if you decide you want to stick with ubuntu you will want to put it on its own partition as it will be faster.

---

### Post by Paqman on 2009-09-16
> **nhasian said:**
> ah okay so you install ubuntu with the wubi windows installer.  in the future if you decide you want to stick with ubuntu you will want to put it on its own partition as it will be faster.

Speed isn't really a drawback with Wubi. The disk-performance hit is so small that you're unlikely to notice it. Wubi does have limitations, but that's not a significant one IMO.

mark111: You can easily bookmark a location in the Windows file structure for easy use in Ubuntu. Just navigate through /host to the location you want (eg: docs & settings) then hit Bookmarks > Add. From then on that location will show up in Places and in the sidebar of the file browser.

---

