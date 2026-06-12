---
title: "Sharing service installation failed"
date: 2009-05-27
forum: New to Ubuntu
---

### Post by Tokalosh on 2009-05-27
Hi folks,
 
I have created a folder name share1, gone to sharing option and click on "Share this folder". A dialog box popped up saying that the "Sharing service is not installed" so I clicked on "Install service", to which I got a message says that the "Sharing service installation failed". I have verified that the machine is connected to the net by browsing to a website.
 
Any Ideas

---

### Post by superprash2003 on 2009-05-28
install samba manually by typing** sudo apt-get install samba smbfs **at the ubunbu terminal

---

### Post by mapes12 on 2009-05-28
Can you explain a little more what you are trying to network please. For example is your network all Ubu boxes or a mix of windoze and Ubu. And how many client machines?

---

### Post by Daleblue on 2009-10-31
Hi 

I have the same problem. I am attempting to share a folder to a windoze PC on the network. However when attempting to share the folder, the 'sharing service' fails to install.

I've attempted the command

sudo apt-get install samba smbfs

I receive error message stating package samba is not available. I then tried the following command 

sudo apt-get install samba-common-bin smbclient samba-common

This installs and confirms newest version. However when using the GUI to share the folder, it still attempts to reinstall 'sharing service' which fails, and I am unable to share folder.

I am very new to ubuntu, however I have previous completed this in 9.04 and it worked like a dream. I've done a clean new install of 9.10 and the problems started. 

Any help would be most appreicated.

---

