---
title: "Browsing networked linux files from windows"
date: 2008-04-18
forum: Networking &amp; Wireless
---

### Post by Patch Adams on 2008-04-18
After some time spend trying to share my files so windows can find them I though that I had succeeded.

But now quite, the windows machine can see my computer and then open it to see the folders I have networked but it cannot browse beyond this point, ie to open folders and view files inside.

Any help would be greatly appreciated

---

### Post by Patch Adams on 2008-04-18
i should have added my smb.conf

[global]
workgroup = MSHOME
server string = %h server (Samba, Ubuntu)
netbios name = nancy
domain master = no
guest ok = yes


[Music]
	path = /home/sam/Music
	available = yes
	browseable = yes
	guest ok = yes
	writeable = no

---

### Post by Patch Adams on 2008-04-18
SOLVED

I had to right click the folders, go to permissions and change the last section on file access to allow everyone read only permissions

---

