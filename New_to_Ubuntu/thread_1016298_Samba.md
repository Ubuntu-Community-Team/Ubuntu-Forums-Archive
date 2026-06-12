---
title: "Samba"
date: 2008-12-19
forum: New to Ubuntu
---

### Post by Archer Troy on 2008-12-19
So im not really sure what happened...about 2 hours ago i was able to connect to  my other computer on the network through smb://192.168.1.101/ in nautilus, but after a restart whenever i try. nothing comes up but a blank window...firewall is down and the computers IP hasnt changed. any suggestion yall..

---

### Post by Archer Troy on 2008-12-19
driving me up a wall. anyone?

---

### Post by Kellemora on 2008-12-19
Hi Archer

Can you PING the other machines at all?

This is done from System/Administration/NetworkTools.

Also, install smbtree from Synaptic Package Manager and while there if you see smbfs is checked, uncheck it.

After installing smbtree, use a terminal and just type smbtree in the command line and see if that shows all of your shares.

TTUL
Gary

---

