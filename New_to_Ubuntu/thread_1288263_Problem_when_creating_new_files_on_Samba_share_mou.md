---
title: "Problem when creating new files on Samba share mounted partition by fstab"
date: 2009-10-11
forum: New to Ubuntu
---

### Post by gospodin.horoshiy on 2009-10-11
Hello! I have an issue setting up common share in LAN residing on Ubuntu Server! 
Clients are WinXP and Ubuntu Desktop 9.04

Everything kinda works but, when **Ubuntu desktop user** creates new file|directory on share, new directory permissions are **d rwx r-x r-x**
                           for new file   [B] rwx rw- rw- 
[/B]
and I want it to be drwxrwxrwx!

Now details:

1) Server side
My samba config smb.conf:
[I]
[common]
        path = /var/common
        comment = common
        valid users = common
        browseable = yes
        create mask = 0777
        directory mask =0777
        writeable = yes
[/I]
ls -l for /var/common:
[I]
drwxrwxrwx 14 common   common 4096 2009-10-11 11:51 common[/I]


2)Client side
First, if WinXP user creates file|directory it will become:
#ls -l
[I]drwxrwxrwx  2 common common     4096 2009-10-11 12:33 wintest
-rwxrw-rw-  1 common common        0 2009-10-11 12:33 wintest.txt
[/I]
Here 'x' is missing but at least rw permissions are ok; 

Now lets try Ubuntu client:
First, If user goes to **smb://192.168.1.50/common/** using Gnome GUI and creates file there:
#ls -l
drwxrwxrwx  2 common common     4096 2009-10-11 12:40 ubuntutestgui
-rwxrw-rw-  1 common common        0 2009-10-11 12:40 ubuntutestgui.txt

So its ok as well. Now lets try to mount this share so users don't have to worry about anything having this share on their desktops all the time:
for that we add this line in /**etc/fstab**
[I]//192.168.1.50/common /media/common cifs users,auto,rw,username=common,password=blahblahblah,iocharset=utf8,gid=users,umask=000  0 0

By that, common successfully mounts but when user tries to create something there:
On the client it looks like:
drwxr-xr-x 2 1006 users     0        ubuntufstab  - this is one creaated by **mkdir ubuntufstab**
[/I]*-rwxrw-rw- 2 1006 users     0        ubuntufstab*2.txt - this one is created by [B]nano ubuntufstab2.txt
[/B]*-rw-r--r-- 2 1006 users     0 ubuntufstab.txt *this is one is created by **touch ubuntufstab.txt . **It also said that Permission denied creating timestamp. 

On the server it look like:
drwxr-xr-x  2 common common     4096 2009-10-11 12:47 ubuntufstab
-rwxrw-rw-  1 common common        4 2009-10-11 12:47 ubuntufstab2.txt
-rw-r--r--  1 common common        0 2009-10-11 12:47 ubuntufstab.txt



It appears to me that for creating file  in mounted share the client desktop uses users umask and they also reflect to server. Please help to configure this mounting thing properly so everyone can do everything on this folder. Thnx

As an alternative way, is there a way to prevent **smb://192.168.1.50/common/ **from dissaperiang from Dekstop, when the client reboots?

---

### Post by yeats on 2009-10-11
> Everything kinda works but, when Ubuntu desktop user creates new file|directory on share, new directory permissions are d rwx r-x r-x
for new file rwx rw- rw-

and I want it to be drwxrwxrwx!

This is a setting in /etc/profile and is not a Samba issue.  *umask* is what you're looking for, I think.  Default in /etc/profile is 022, which sets user-created files to rwxr-xr-x.  You can either change this in /etc/profile, or set it in ~/.bash_profile for the user in question.  The umask man page does not seem to be installed by default, but Google can help you out here :-).

---

### Post by Boondoklife on 2009-10-11
Well one option that I did was to simply create a desktop shortcut to smb://SERVERNAME

This way that stays on the desktop and they always can get to what ever share they want by going into it and selecting it.

---

### Post by gospodin.horoshiy on 2009-10-12
That was samba. To resolve my problem I simply added 
[B][global]
unix extensions = no

[/B]to smb.conf on server.

---

