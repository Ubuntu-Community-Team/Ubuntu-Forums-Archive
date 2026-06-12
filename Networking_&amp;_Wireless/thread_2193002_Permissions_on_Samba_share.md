---
title: "Permissions on Samba share"
date: 2013-12-10
forum: Networking &amp; Wireless
---

### Post by miceagol on 2013-12-10
I have an Ubuntu Server where I have a couple of folders I'm trying to share on the network using Samba. The folders are visible on my Ubuntu desktop machine, but I have troubles getting the permissions right.

My requirements:
[LIST]
[*] Guest user must be able to access the share with read only rights.
[*] Authorized users (kikkmikk and kristin) must be able to access the share with full write rights.
[/LIST]

This is the relevant output of /etc/samba/smb.conf for one of the share folders
```

path = /home/kikkmikk/filmer
force user = kikkmikk
force group = kikkmikk
write list = kristin kikkmikk
create mask = 0664
directory mask = 0775
guest ok = Yes

```

On the Ubuntu desktop, the share should automatically mount at boot. I've added the following to /etc/fstab for the share in question
```

//192.168.19.190/filmer /home/filer/felles/jiji/filmer cifs iocharset=utf8,credentials=/root/.smbcredentials,file_mode=0660,dir_mode=0770 0 0

```

The .smbcredentials file contains username and password in the following format
```

username=kikkmikk
password=<password>

```

The share is automatically mounted, but I have no write rights. So it seems like I only have guest access.

The files and folders have the following permissions and owner/group on the server:
```

drwxrwxr-x  8 kikkmikk kikkmikk  4096 sep.  22  2011 Family Guy
-rw-rw-r-- 1 kikkmikk kikkmikk 161716224 des.  30  2010 101 - Death Has A Shadow.avi

```

What am I doing wrong? 

After changing the settings in /etc/fstab I rund *sudo mount -a* to remount it, and after changing settings in the smb.conf file on the server I run *service smbd restart*.

---

### Post by miceagol on 2013-12-11
I manged to solve this after some investigation. The error was due to three closely related issues.

First of all I had only created the kikkmikk user on the server, not on the client:
```

sudo useradd kikkmikk

```
So apparently Ubuntu logged in as guest, since the user didn't exist on the client.

Secondly, I had to add the uid and gid to /etc/fstab (use id -u <user> and id -g <group> to list them):
```

//192.168.19.190/filmer /home/filer/felles/jiji/filmer cifs iocharset=utf8,credentials=/root/.smbcredentials,uid=1002,gid=1002,file_mode=0664,dir_mode=0775 0 0

```

But the user permissions were still not functioning correctly. I could now create files and folders, but they were created with another group owner on the server for some reason. I found the cause was that the kikkmikk GID was different on the server and the client, i.e. GID for kikkmikk was 1002 on the server and 1001 on the client. According to [this thread]("http://unix.stackexchange.com/questions/33844/change-gid-of-a-specific-group"), changing GID is cumbersome. So I changed the user in .smbcredentials to another one with equal UID/GID on both server and client.

Also I changed the smb.conf settings a bit:
```

[filmer]
path = /home/kikkmikk/filmer
read only = Yes
guest ok = No
browseable = Yes
create mask = 0664
directory mask = 0775
write list = @kikkmikk
force user = kikkmikk
force group = kikkmikk

```

Remember to run the following when you change smb.conf to make the changes take effect
```

sudo service smbd reload
sudo service nmbd reload

```

And run
```

sudo umount /path/to/mountpoint
sudo mount -a

```
when you have changed the /etc/fstab file or .smbcredentials file. If you credentials are wrong, mount - a will give you a Permission Denied error.

Hope this helps someone else. :)

---

