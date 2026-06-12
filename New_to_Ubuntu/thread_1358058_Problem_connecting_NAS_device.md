---
title: "Problem connecting NAS device"
date: 2009-12-17
forum: New to Ubuntu
---

### Post by moransa on 2009-12-17
I installed Ubuntu 9.10 for the first time last night and have it almost where I want it.  But I cannot get it to permanently mount my NAS device.  My NAS device is an HP Media Vault.  I can mount the NAS by running smb://ipaddress/folder, but it loses the mount after reboot.  I've been reading up, searching the [forums]("http://ubuntuforums.org/showthread.php?t=255872&highlight=mounting+shares") which are very helpful and I've learned a lot about my new toy (biggest lesson was that I've spent far too much time in a Windows data center).  I've modified the /etc/fstab file and created a password file separately and it does not work.  

I used terminal to test the code I inserted to fstab: smbmount //ip/folder /mountdirectory -o credentials=/home/moransa/.nascred

I get: 
mount error: can not change directory into mount target /media/data/mountdirectory

WHY NOT????

I have several problems with this to begin with, I do not want to mount a disk *under another disk folder*, I would prefer to mount it under /media, but it will not allow me to create a folder there.  I've done sudo to try and use root permissions for it, but either way I try it, it still does not work.  

Help please.....

---

### Post by moransa on 2009-12-17
Got it.  Not used to case sensitive folder names, let's blame Gates for this one =)

I logged in a root, created a folder called HPNAS under /media, gave my userid full permissions, logged back in as myself, made the case sensitive change to the script and it ran.  

Thanks anyway to those who thought about replying....

---

### Post by moransa on 2009-12-18
I take that back, it does not work when I login.  It works if I paste the command into terminal, but does not mount upon reboot.  I inserted the following into /etc/fstab file at the bottom:

smbmount //nasipaddress/folder /media/HPNAS -o credentials=/home/moransa/.nascred

How is the fstab folder processed on boot, and where can I find log files that might indicate why it is not mounting?  I've looked in System>Administration>Log File Viewer, but I can't make heads or tails from it.

---

### Post by SteveHillier on 2009-12-18
I have used it with automatic mount on boot and somewhere there is a post of mine on how I did it but...
These days, I connect to a network drive using the 'connect to server' link in the menu.  Then when I have set up all the credentials I drop it in my bookmarks.  Next time I want it I just click on my bookmark and away we go.

---

### Post by moransa on 2009-12-18
I would like to use 'connect to server', but this is not a Windows share, so to speak.  It's a NAS running on some kind of hybrid HP-Linux OS, but I can only map it from Ubuntu as a Windows device with an IP...  Point is, I've tried all the options under connect to server and none work, can you elaborate to the selections you use?  

Thanks,

---

### Post by SteveHillier on 2009-12-20
Hi moransa,
When I set up a NAS server (using FreeNAS) I was able to format the partitions with NTFS and see them as a Windows share.  
You say you have got access using```
smb://ipaddress/folder
``` so you are seeing the drive via SAMBA which is how Ubuntu sees Windows drives.
Are you sure once you have got it open you can't just bookmark it?

---

