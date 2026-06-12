---
title: "Filesharing between Ubuntu boxes..??"
date: 2006-12-20
forum: Networking &amp; Wireless
---

### Post by Robert.Zapata on 2006-12-20
Hello Team and Happy Holidays.

How can I share files between my Ubuntu machines..?? My understanding is that Samba is only required for connecting to/from Windos machines. 

How do you see/share other Ubuntu boxes in your same network..??

Thank you very much.

---

### Post by PilotJLR on 2006-12-20
NFS is the most common way to do this.

---

### Post by mscclr3 on 2006-12-20
How I've done it is:

Install SSH on both machines
from a terminal type ssh *other machine's ip*
then it should appear as a network share in the left panel of a file browser (in same list as File System and dave (my username) on my laptop)

This assumes that you:
a.) are on a lan where you can control the dns stuff (it isn't a big deal if you aren't, I just like being able to have the addresses as static on not have to reset the connection)
b.) you have the same username on both machines


I had tried to set up nfs and samba at variou points but had no success so, this works for now... I was surprised to see the icon said "ssh" towards the bottom of it.

---

