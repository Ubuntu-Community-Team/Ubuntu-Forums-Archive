---
title: "NAS - setting file permissions in webmin - samba windows file sharing"
date: 2017-09-15
forum: Networking &amp; Wireless
---

### Post by madumi on 2017-09-15
I'm setting up a NAS file server using Ubuntu server 16.04 & accessing it with a Win10 machine... And yes, I am clueless about setting file permissions/users.

I have formatted a new drive as ext4, mounted it in /mnt/FOLDER, and created a Samba new file share NETWORK_FOLDER with writable access under security and access control in webmin (no guest access).

The shared folder, NETWORK_FOLDER isn't writable until I change folder permissions to 777. Ownership presently is root:root

Surely I'm doing something wrong? Wouldn't it be preferable to set folder permissions to 700, or even 600 (I only need read/write access to the file server), and access the network shares using an owner account (?). If so, I'm not sure how to accomplish this.

Any hints what am I doing wrong?

thanks!

---

### Post by madumi on 2017-09-16
Okie, Can someone please correct or confirm if I'm on the right track understanding file permissions.

For hard_drive_A, If I set read/write/execute permissions for the owner, but block it for group and public (700), then the only person who can read/write/execute on the drive is the owner specified...

I noticed standard owner and group permissions both seem allocated to "root." Does this mean that the only person who can potentially read/write/execute on files with permissions set to 770 would be an administrator on the machine? What confuses me is that an administrator should be able to access all files anyway, or at least allocate them to themselves if need be (no?). Does setting the owner/group to something different than "root" mean that that person plus the administrator can access the files, and that if anything should go wrong, an administrator can access/re-allocate the files?

If I'm following things then, the only reason to set 755 for file/folder permissions is if you wished read/execute permissions to be given to someone who could not log into the machine right? Is there any security benefit to leaving them in the dark about directories/files etc (permissions 750)?

Now, if I was running the file server purely for read/write access (no scripts), would it make sense to set permissions to 600?

Thanks!

---

### Post by Morbius1 on 2017-09-17
There are some concepts that need to be explained here I think.

The settings you configure for a samba share determines what the samba client user [COLOR=#0000cd]**may**[/COLOR] do to that share and it's shared folder. The Linux permissions you set on the folder being shared determines what the samba client [COLOR=#0000cd]**can**[/COLOR] do to that folder. Think of the samba share specifications as a gate keeper. Samba "permissions" must always be less than or equal to the Linux permissions, They cannot be greater than.

So let's say you have a share that looks something like this in /etc/samba/smb.conf:
> [NETWORK_FOLDER]
path = /mnt/FOLDER
read only = No
guest ok = no
And that the current permissions of the shared folder are owner = root, group = root, and standard permissions of 755.

Samba the gatekeeper allows anyone with a samba password write access to the folder but Linux permissions prevents a write since it's only writeable to root.

*** You can set permission of /mnt/FOLDER to 777 then any user with a samba password has write access.

*** You can keep the permissions as 755 but change the ownership from root to you (madumi) and change the share definition so that only your user name and samba password can gain access:
> [NETWORK_FOLDER]
path = /mnt/FOLDER
read only = No
guest ok = no
valid users = madumi
Of course if everyone on the lan was told to access the share as madumi you wouldn't need the "valid users" line but ...

*** You can keep the permissions as 755 but change the ownership from root to you (madumi) and change the share definition so that all client users with credentals will act as you - for that share anyway:
> [NETWORK_FOLDER]
path = /mnt/FOLDER
read only = No
guest ok = no
force user = madumi

*** Or you can do a hundred  other things depending on how complex you want to make this.

[COLOR=#0000cd]*Special note: You don't want to set folders at 600 - or any even number. They must be executable. The execute bit on a folder allows it to be opened.  The execute bit on a file allows it to be .. um .. executed.*[/COLOR]

---

### Post by madumi on 2017-09-17
Thanks so much for your explanation. OK, I think I understand better Samba being the gatekeeper.

I'm not sure if I understand things right, but am I correct thinking that once a win10 machine logs in to the Samba file server, any malicious code on that win10 machine would be able to alter the files/folders shared to that user, though it wouldn't be able to execute malicious code from within the Samba/linux server (not having "root" access)... right? Are there any security measures that could mitigate this (I'm guessing not)?

---

