---
title: "Sharing external drive"
date: 2007-07-27
forum: Networking &amp; Wireless
---

### Post by munchy on 2007-07-27
Hi,
I have an external USB hard drive (FAT format) connected to my Kubuntu Feisty box and I'd like to share it on my wireless network via samba (or other suggested method?) so i can read/write access it from my macbook (or any other mac/windows comp on my network) and continue to use it as normal from my Kubuntu box. I'm kinda familiar with samba config for sharing home folders but not sure how to add this drive.....pls help
cheers :)

---

### Post by moeFinley on 2007-07-28
You can share a drive in the same way as you share anything else.  Right click and select 'Share this folder'.  You USB drive will be somewhere similar to /media/usbdrive

The problem I'm having is I can't set the permissions for the shared drive.  I can see the share from other machines but I don't have permissions to see or write files.  When I try changing the permissions in Nautilus it automatically switches it back.  I've tried doing the same with Sudo Nautilus and got the same.  Any ideas?

---

### Post by Wordcrasher on 2007-10-04
Hi,
how is your USB drive formatted ?   I have the same issue with mine, and I'm beginning to think the issue may be it is a NFTS drive.

---

### Post by c9ops on 2007-11-13
I have the exact same issue as well.  My external USB connected drive is formatted as FAT32.  This is a pretty pointed thread for a specific issue.  If anyone could post the reason why we all are not 'easily' able to change the permissions for this external drive... that would be great.

The permissions and ownership seem to be the key here.

I have used masks on the fstab with no success.  Sudo chmod and chown commands seem to take from the terminal but then checking the properties shows the change did not take effect.

Thanks in advance.

---

### Post by hardin0341 on 2007-11-21
I am in the same boat! I have an Ubuntu Server 6.06 running fine. I plugged in the USB external hard drive, and mounted it in my file system (under my /home/"user" directory so I could use with Samaba). I can see the drive, but I cannot access it, cannot change read/write, cannot cd in to it. 

I found out I have to format to FAT32 (it is NTFS). I will transfer all files to Wind@R) machine, then format, then transfer back for serving over my LAN. Any ideas on the easiest way to format to FAT32? Also, is there a straightforward way to serve the files via Samba over the WAN???  

Thanks for all you all do! I love this community, and hope to be able to share some help (when I figure something out!).

---

