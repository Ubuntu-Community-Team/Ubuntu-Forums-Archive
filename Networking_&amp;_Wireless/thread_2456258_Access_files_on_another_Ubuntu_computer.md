---
title: "Access files on another Ubuntu computer"
date: 2021-01-07
forum: Networking &amp; Wireless
---

### Post by John Jason Jordan on 2021-01-07
OK, this is a little involved. I have two computers, both Xubuntu 20.04, up to date. 

One is a desktop with a big UHD screen that functions during the day to play internet radio, or my own music, and during the evening to play movies, or sometimes over the air television with my HDHomeRun tuner. There is not a lot of software on it, because that's about all it does.

The other computer is my main machine, a Thinkpad P73, also UHD, with massive software installed, a lot of which is for video. I buy hundreds of movies each year, mostly BD nowadays, which I have to rip and encode in order to view them on computer #1. Because I have so many such movie .mkv files I installed Thunderbolt 3 enclosure with 31TB of NVMe drives. It is a delight - so FAST!

The TB3 enclosure is backed up nightly to a Synology NAS, with two 16TB WD Gold drives in RAID0. Both computers have full access to the Synology, so when I want to play a movie on computer #1 I access it on the Synology.

This system works fine, but my life would be a little simpler if computer #1 could access the files on the TB3 enclosure connected to the Thinkpad rather than on the Synology. Everything is on gigabit ethernet, although both computers also have active wifi connections. 

I think I need NFS to do this, but I need help to figure out how. Or maybe it can't be done. Any ideas?

---

### Post by oldfred on 2021-01-07
I use NFS, but have been told for my use case SSH would be better.
I am just copying files from one system to another on an adhoc  basis.
But I have the install of nfs system files, creation of mount points, edit of /etc/exports, all automated as part of my new install scripts.
And then I run one script to mount and another to rsync files. I think some that add mount to fstab have timing issues and end up adding script to update after system have fully booted so network is available. Some system boot so quick network is not available and then nfs mount fails.

My details, but other probably more simple suggesitons:
[https://ubuntuforums.org/showthread.php?t=2387690](https://ubuntuforums.org/showthread.php?t=2387690)

[https://www.tldp.org/HOWTO/NFS-HOWTO/server.html](https://www.tldp.org/HOWTO/NFS-HOWTO/server.html)
[https://help.ubuntu.com/community/SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo)
[http://mostlylinux.wordpress.com/network/nfshowto/](http://mostlylinux.wordpress.com/network/nfshowto/)
Autofs mount directories on an as-needed basis.
[https://help.ubuntu.com/community/Autofs](https://help.ubuntu.com/community/Autofs)
Example autofs and _netdev
[https://ubuntuforums.org/showthread.php?t=2450936](https://ubuntuforums.org/showthread.php?t=2450936)

---

### Post by John Jason Jordan on 2021-01-08
@oldfred,

Thanks for the info and links. I tried several of them, and nothing worked. I give up.

Someday someone at Ubuntu needs to make an application (no, not a set of scripts), that will search the local network, find other Ubuntu computers, and connect to them for file transfer. I can't believe no one has ever done this.

---

### Post by cmcanulty on 2021-01-09
have you tried grsync all gui  no scripting required

[https://askubuntu.com/questions/234690/how-to-backup-over-lan](https://askubuntu.com/questions/234690/how-to-backup-over-lan)

---

### Post by John Jason Jordan on 2021-01-09
Someone on my local Linx user group came up with the solution - Gigolo, which was already installed, as were openssh, client and server. In Gigolo all I had to do was click on Actions > Connect, type in the IP address of the other computer, and then my login name and password, et voilà! I now have a GUI file manager with everything that is on the other computer.

---

