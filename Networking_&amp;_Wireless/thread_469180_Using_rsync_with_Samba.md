---
title: "Using rsync with Samba"
date: 2007-06-09
forum: Networking &amp; Wireless
---

### Post by mholmes on 2007-06-09
I have a Maxtor Terabyte NAS drive which stores all my media, and I'd like to back up the music to a machine running Feisty. I've been able to mount the shares from the network drive on the Ubuntu desktop, but I can't figure out the exact syntax for an rsync command that will back up the network drive to my local drive. The shares are Samba shares, but when I try to use the Samba protocol to connect to the remote drive, rsync fails to connect. I have smbfs installed.These are some of the many things I've tried:

rsync -av --stats -"smb://mholmes@192.168.0.158:Public/Our Music" /media/disk2/music/
rsync -av --stats "smbfs://mholmes@192.168.0.158:Public/Our Music" /media/disk2/music/
rsync -av --stats -e smbfs "mholmes@192.168.0.158:Public/Our Music" /media/disk2/music/

Does anyone have any idea how to make this work? If I can access the drives from my Ubuntu desktop, surely I should be able to use rsync to copy files? I've been able to get a similar system working on an OSX machine.

The Maxtor drive doesn't have ssh support, so that's out, unfortunately.

All help appreciated,
Martin

---

