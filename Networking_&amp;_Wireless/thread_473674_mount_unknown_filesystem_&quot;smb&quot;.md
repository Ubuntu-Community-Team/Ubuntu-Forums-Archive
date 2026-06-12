---
title: "mount: unknown filesystem &quot;smb&quot;"
date: 2007-06-14
forum: Networking &amp; Wireless
---

### Post by Luc1fer on 2007-06-14
Hi

I'm getting an error message when running "sudo mount -a" after trying to mount a remote filesystem trough samba by adding this line to fstab.
```
//***.***.***.***/pc	/media/****-pc	smb	defaults	0	0
```

Rebooting doesn't help either.

Tried to search google but couldn't find anything.

Is there any easy solution to this?

---

### Post by incoming429 on 2007-06-14
Hi,

the filesystem is called 'smbfs', not 'smb'. Also make sure you have the smbfs package installed.
Michal

---

### Post by Luc1fer on 2007-06-14
> **incoming429 said:**
> the filesystem is called 'smbfs', not 'smb'. Also make sure you have the smbfs package installed.
That solved the first problem :)

However it still doesn't mount on boot and when I try with "sudo mount -a" I have to enter a password (not the sudo password, i have to enter one more after the sudo part) and then I'm getting this message.
> 6359: session setup failed: ERRDOS - ERRnoaccess (Access denied.)
SMB connection failed
I understand that it doesn't accept my password but what I don't understand is why because it's correct as both system password and samba password.

---

### Post by incoming429 on 2007-06-16
Looking at your example in the first post, you didn't specify your username/password in fstab. Did you try following the Ubuntu Guide? It works well for me using Debian Etch/Samba as the file server.

Direct link here: [http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_mount_network_folders_on_boot-up.2C_and_allow_all_users_to_read.2Fwrite](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_mount_network_folders_on_boot-up.2C_and_allow_all_users_to_read.2Fwrite)

---

### Post by Luc1fer on 2007-06-16
> **incoming429 said:**
> Looking at your example in the first post, you didn't specify your username/password in fstab. Did you try following the Ubuntu Guide? It works well for me using Debian Etch/Samba as the file server.

Direct link here: [http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_mount_network_folders_on_boot-up.2C_and_allow_all_users_to_read.2Fwrite](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_mount_network_folders_on_boot-up.2C_and_allow_all_users_to_read.2Fwrite)
That was the guide i followed in the first place (missed that in my first post), so yes i have the password file.

---

