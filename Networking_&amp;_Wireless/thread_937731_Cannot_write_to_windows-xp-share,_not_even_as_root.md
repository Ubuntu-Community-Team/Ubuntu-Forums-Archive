---
title: "Cannot write to windows-xp-share, not even as root"
date: 2008-10-04
forum: Networking &amp; Wireless
---

### Post by lupoph on 2008-10-04
After looking through how-tos, manpages, tutorials and forums for hours, not gaining any helpful information, I'll try it this way...

What I want: I want to synchronize my data on a Windows XP notebook with my data on my Asus EEEPC 1000H (Ubuntu runs on it) using unison.

What works: I can read my Windows-Shares both as user and as root. This works by any way I tried to mount it, using 
- sudo mount -t cifs //IP/SHARE /mnt/test
- fstab-entries:
- - /IP/SHARE /mnt/test	cifs	username=XX,password=YY,uid=1000,iocharset=utf8,dir_mode=0775	0	0 
- - /IP/SHARE /mnt/test	cifs	credentials=/home/XX/.smbcredentials,uid=1000,iocharset=utf8,dir_mode=0775	0	0 
as username and password, both when trying to pass them via the fstab-entry and the .smbcredentials I used my Administrator-Account on the Windowsmachine (i.e. username=examplename,password=pass, no domain or anything specified)

What doesn't work: Whenever I try to write to any mounted share, it tells me: Access denied. Well... The access should be allowed; I used the simple share feature of windows xp home, allowing both read and write access. The shares are all on ntfs-drives, and some of them cannot be changed into fat32 for practical reasons.

The other way around (sharing an ubuntu-folder with "sudo nautilus"-gui) works only if I allow read/write even to guests; I couldn't figure out how to log in with a use account from the windows-machine on the ubuntu-machine. This wouldn't make sense for me, for the ubuntu-machine is the one i use on the run in public wlans, so I cannot allow those access rights on the ubuntu machine. More over I'd have to make workaround again, If I had to run some synchronization-software from the windows-machine. 

When I try to open a text-file on the share via nautilus, even reading works quite odd. It re-requests username and password and domain again and again and never accepts them; as domain I use the workgroup of the windows-machine.

Another useful information may be, that I'm trying to do these things via WLAN.

By the way, I'm still a bit of a newbie to ubuntu, at least to asking for help, so please excuse me, if I give the information the wrong way.


*edit* Oops, wrong sub-forum?

*edit* Btw, I'm using Ubuntu 8.04

---

### Post by lupoph on 2008-10-04
*bumP*

---

### Post by lupoph on 2008-10-04
I just noticed, that write-access does neither work when trying to write from xp to ubuntu.
*edit* But got it to work at least the one direction with GSAMBAD. Still noone any idea?

---

