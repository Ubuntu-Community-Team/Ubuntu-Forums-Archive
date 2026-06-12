---
title: "Samba: some folders work, some not"
date: 2014-10-08
forum: Networking &amp; Wireless
---

### Post by freverte on 2014-10-08
Hi.

I am having problems while configuring samba after installing ubuntu 14.10. I got 2 folders, both exactly with same configuration, one is on the OS hdd and the other is another SATA HDD. I can access to the first one, but not to the second one. I don't understand why, as far as the configuration is exactly the same. When I try to go into the Folder2 from Windows 8 i get the "no permissions" message. Both are "rasputin:rasputin" chmod'ed and 777 permissions. Any help really appreciated as I have been some hours with that without being able to solve it.

My config file:


> [global]
   workgroup = CASA
   server string = %h server (Samba, Ubuntu)
   netbios name = rasputin
#   security = user
   dns proxy = no
   map to guest = bad user

   log file = /var/log/samba/log.%m
   max log size = 1000
   syslog = 0
   panic action = /usr/share/samba/panic-action %d
   server role = standalone server
   passdb backend = tdbsam
   obey pam restrictions = yes
   unix password sync = yes
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
   pam password change = yes

[Folder1]
        path = /home/rasputin/Desktop/folder1
        browseable = yes
        read only = no
        guest ok = yes

[Folder2]
        path = /media/rasputin/folder2
        browseable = yes
        read only = no
        guest ok = yes

---

### Post by JDorfler on 2014-10-08
Make sure the samba group has the proper permissions for the folders.
```
sudo chown -R root:sambashare ./directory
```

Then add users to to samba itself
```
sudo smbpasswd -a "user"
```

This is important, especially the second folder that doesn't belong to you.  Technically it belongs to root.  Also, your first folder will not be able to be accessed unless you are logged into the machine itself.  Changing the owner and group to root:sambashare will allow access to the shares when you aren't logged in.  So you can change files in the folders in your home directory, add yourself to the sambashare group;
```
sudo useradd -G sambashare user
```

You might also want to change the perms back so only those users you have added via samba can access the files;

```
sudo chmod 774 -R ./directory
```

---

### Post by freverte on 2014-10-08
Hi, thanks for the answer, but I don't understand what you want to say. Both folders belongs to "rasputin:rasputin" and their permissions are 777 (to test). Changing the owner will make them not available to other tasks. Rasputin is the main user in the machine and should be able to access everywhere. Samba is configured for anonymous access. Don't understand why one works and the other don't.

---

### Post by freverte on 2014-10-08
However, I tested what you told me, it doesn't work neither. No access to the folder2.

---

### Post by freverte on 2014-10-08
I finally could make it work, using "force user = rasputin". I can access anonymously and i can control read only access with "read only = yes/no". Chmod back permission to folders to 755. 

Thanks.

---

