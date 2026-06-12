---
title: "Change network of Ubuntu Machine (ubuntu machine on mshome network)"
date: 2006-08-07
forum: Networking &amp; Wireless
---

### Post by djsamsel on 2006-08-07
my computer can see my windows network, but my other computers can't see this machine. There are two winows networks listed (hartford and mshome). the other computers show up in hartford, this computer shows up in mshome. how do i add this computer to the hartford network. is there a gui entry somewhere? thanks, doug

---

### Post by meng on 2006-08-07
To do it through GUI, I would try System > Admin > Shared Folders and there's a "General Windows Settings" button if you add or edit a share. I don't know this works, as I usually tweak the smb.conf file.

---

### Post by fourchannel on 2006-08-07
The file that controls sharing on windows networks is the /etc/samba/smb.conf file.

In that file, near the top, is a place where you can change the workgroup name. Not so supprisingly it's called "workgroup = WHATEVER"

to change that file run this command ```
sudo gedit /etc/samba/smb.conf
``` and to restart samba after you're done run ```
sudo /etc/init.d/samba restart
``` 
EDIT:
Meng's way is by far the easier way or if you are uncomfortable with editing text files. =D

---

