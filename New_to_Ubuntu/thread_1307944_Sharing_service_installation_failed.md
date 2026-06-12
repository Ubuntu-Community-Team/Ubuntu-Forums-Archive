---
title: "Sharing service installation failed"
date: 2009-10-31
forum: New to Ubuntu
---

### Post by Daleblue on 2009-10-31
Hi

I am attempting to share a folder to a window PC on the network. However when attempting to share the folder, the 'sharing service' fails to install.

I've attempted the command

sudo apt-get install samba smbfs

I receive error message stating package samba is not available. I then tried the following command

sudo apt-get install samba-common-bin smbclient samba-common

This installs and confirms newest version. However when using the GUI to share the folder, it still attempts to reinstall 'sharing service' which fails, and I am unable to share folder.

I am very new to ubuntu, however I have previous completed this in 9.04 and it worked like a dream. I've done a clean new install of 9.10 and the problems started.

Any help would be most appreicated.

---

