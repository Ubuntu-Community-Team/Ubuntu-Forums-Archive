---
title: "how do I make it so I can see a folder that is being shared by an XP computer??"
date: 2007-01-11
forum: Networking &amp; Wireless
---

### Post by presbp on 2007-01-11
so the computer upstairs currently has the shared folder on the network.. and I can see it in Windows but how do I configure Ubuntu Edgy so that I can see it?

---

### Post by ajmorris on 2007-01-11
You need to run samba.  This can be started from a shell but i can't remember the command. If search the forums for it, you will robably find something. :)

---

### Post by kebes on 2007-01-11
What you want to do is "mount a samba share" in Ubuntu. This guide:
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_mount.2Funmount_network_folders_manually.2C_and_allow_all_users_to_read.2Fwrite](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_mount.2Funmount_network_folders_manually.2C_and_allow_all_users_to_read.2Fwrite)

Explains how to do that using the commandline.

To do it graphically, try:

Places > Computer

Then go File > Connect to Server...

Select "Windows Share" and enter the appropriate information.



The above-mentioned guide also explains how to set this to auto-mount during bootup, so you don't have to do it manually each time.

---

