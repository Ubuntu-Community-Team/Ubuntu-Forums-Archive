---
title: "Another cifs problem"
date: 2014-02-19
forum: Networking &amp; Wireless
---

### Post by James Wilde on 2014-02-19
Setup is Ubuntu 13.10 64 bit trying to mount an external disk on a Windows 7 64 bit machine.  Both machines have fixed IP addresses on the 192.168.1 net.

This command works ok:

sudo mount -t cifs -o sec=ntlmssp,username=Monica,password=<password>,domain=workgroup,iocharset=utf8,file_mode=0777,dir_mode=0777 //192.168.1.102/Seagate /media/james

This shows up as james in Nautilus, but I would like to have it show up as Seagate in Nautilus.  /media/james should be the mount point but I can live with it showing up as james.

However, we don't use passwords on the home network, so I have taken away the temporary password I gave my wife on her machine (the windows box) and replaced password=<password> with password=''.  Now I get the infamous Error 115 and the remote drive does not mount.

Can someone please suggest a command line which will mount the remote disk without a password, and preferably so that it shows up in Nautilus as Seagate.  I've tried a lot of different varieties of the mount command, without success, and I can't find an answer with a search of this forum.

I do have a suspicion that it won't work without a password, and wonder if someone alternatively can confirm that, and possibly find a workaround.

---

### Post by James Wilde on 2014-02-20
Never mind.  Fixed it.

---

### Post by wildmanne39 on 2014-02-20
Please post how you fixed it so the whole community can benefit.
Thanks

---

