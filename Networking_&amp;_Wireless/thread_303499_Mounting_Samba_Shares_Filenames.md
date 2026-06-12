---
title: "Mounting Samba Shares Filenames"
date: 2006-11-20
forum: Networking &amp; Wireless
---

### Post by DimitrisC on 2006-11-20
I have mounted my samba shares and i can browse the files on my windows machine just fine!  My problem is that all files that are written in greek appar as ?????? instead of the correct filename and when i click on them they disappear.

I have tried different mount commands such as:

sudo mount //PC1/Backup /media/HomeNet/ -o username=******,password=*****,dmask=777,fmask=777

sudo mount -t smbfs //PC1/Backup /media/HomeNet -o iocharset=utf8,username=*******,password=******

sudo mount -t smbfs //PC1/Backup /media/HomeNet -o iocharset=iso8859-7,username=******,password=****** 

sudo mount -t smbfs //PC1/Backup /media/HomeNet -o iocharset=utf8,username=******,password=*****,uid=1000,mask=000


but nothing works.  I don't know what else to try.  I can access the shares with nautilus through the network icon and the filenames appear fine.  All my videos and music is on another computer and i read that i have to mount the shares in order to get playback in my linux box.

Any ideas??? Thnx!

---

### Post by DimitrisC on 2006-11-20
Well answering my own post :D i found a solution that worked here: [http://ubuntuforums.org/showthread.php?t=288534](http://ubuntuforums.org/showthread.php?t=288534)

It may help other people having the same problem.  It's not just for greek its for other encodings as well.

---

