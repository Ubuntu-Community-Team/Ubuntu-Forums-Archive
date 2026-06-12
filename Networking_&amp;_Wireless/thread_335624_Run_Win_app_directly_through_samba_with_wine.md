---
title: "Run Win app directly through samba with wine?"
date: 2007-01-10
forum: Networking &amp; Wireless
---

### Post by Nakajoe on 2007-01-10
Hi everybody, got a question as to whether something is possible or not. I'm running Edgy now at work on a dual boot with Windows, and would prefer to stick to the Edgy as much as possible; problem is, we use one particular and very important program that's run by executing the file directly from the (Windows) server. If I go to the directory via the smb:// prompt, I get a command unknown error if I try wine.

I can see the file just fine via samba, but can't figure out how, if it's even possible, to use wine to run a .exe without copying it to my drive first, which is impossible in this case. Can't find anything about this on google or in the wine documentation, so I was thinking there might be something I could do on the OS level to make wine think it's a local program or something. Any ideas, or anybody notice something I'm missing?

Thanks for any help!

---

### Post by kebes on 2007-01-10
Instead of navigating to a smb:// location (which wine doesn't understand), you should mount the samba share to a specific location on your hard drive. Then wine should be able to handle it because you'll just be navigating to a folder.

To mount samba into filesystem:
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_mount.2Funmount_network_folders_manually.2C_and_allow_all_users_to_read.2Fwrite](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_mount.2Funmount_network_folders_manually.2C_and_allow_all_users_to_read.2Fwrite)

---

### Post by Nakajoe on 2007-01-11
THAT got it, thanks!

---

