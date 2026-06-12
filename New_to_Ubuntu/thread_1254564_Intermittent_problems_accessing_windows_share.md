---
title: "Intermittent problems accessing windows share"
date: 2009-08-31
forum: New to Ubuntu
---

### Post by hnarwan on 2009-08-31
Hi all,

I have managed to access my windows xp shared folder from ubuntu junty but it's really hit and miss.

I installed smbclient and was able to see the windows xp machine in places\network\windows network but now that folder is empty.

When i try to access it directly from ALT + F2 smb://pc1/movieshare i get:

Could not open location 'smb://pc1/movieshare/'

Failed to mount Windows share

I installed pyNeighborhood and that worked initially but now it doesnt. 

I add the windows computer in there, the shares show up which is something but when i click on the one i want i get:

Failed to mount.

Could someone explain to me how to get this working again and how, once and for all i can get this windows xp shared folder to mount in ubuntu and  have it not go missing?

thanks
Hardeep

---

### Post by JillSwift on 2009-08-31
I find this is typically caused by some problem resolving machine names. Possibly because of the shifting of domain stewardship.

Anyway, the best work-around is to get the IP address of the Windows machine and use that in place of the machine name. That is:

Instead of smb://name/share
Use smb://192.168.100/share (replacing 192.168.0.100 with the actual address of your windows machine)

---

### Post by hnarwan on 2009-09-01
Thanks Jill, that works. I dont mind doing this each time but is there a way to mount it so i have an entry in 'places' pointing to this windows share?

---

### Post by JillSwift on 2009-09-01
Sure:

When you have the share open in a nautilus window, just go to the "bookmarks" menu and "add bookmark". :)

---

