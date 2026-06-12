---
title: "ubuntu e WinXP LAN. Sharing resources."
date: 2007-09-16
forum: Networking &amp; Wireless
---

### Post by vampire666eng on 2007-09-16
Hi again.:)

I have one PC (let's call it [COLOR="Blue"]PcXP[/COLOR]) with Windows XP installed (and on another partition ubuntu of course ;)) and another old PC ([COLOR="DarkOrange"]PcXU[/COLOR]) with xubuntu. 
These two computers are connected to a router connected to the net. Both PC can surf the net without any problem, but now I would like to share the resources of the two computers between the two.

I would like to share  the hard disk of [COLOR="DarkOrange"]PcXU[/COLOR] with [COLOR="Blue"]PcXP[/COLOR].

I would like to share the entire drive (hard disk) of the [COLOR="DarkOrange"]PcXU[/COLOR] so that I can easily access all it's data and make a full backup drive image with the [COLOR="Blue"]PcXP[/COLOR] (which has Acronis True Image program installed).
I don't want to share only some directories, I would like to share the complete drive if possible (or better all xubuntu's partitions).

What should I do?

Thanks a bunch.

---

### Post by vampire666eng on 2007-09-16
Basically what I did was:
-Installed Samba,
-In the Shared Folders I inserted the File System(/) (shared through Windows networks (SMB)) and specified the workgroup used on the PcXP (workgroup:CASA).

But nothing changes on PcXP.....I can't see the shared (/) of PcXU.

EDIT: Basically I followed this tutorial without any success:

[http://www.techotopia.com/index.php/Sharing_Ubuntu_Linux_Folders_with_Remote_Windows_Systems](http://www.techotopia.com/index.php/Sharing_Ubuntu_Linux_Folders_with_Remote_Windows_Systems)

---

