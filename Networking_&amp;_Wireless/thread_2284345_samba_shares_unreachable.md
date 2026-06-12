---
title: "samba shares unreachable"
date: 2015-06-28
forum: Networking &amp; Wireless
---

### Post by creznedmick on 2015-06-28
After my first attempt to set up Samba in Ubuntu-mate 15.04 would not let me open displayed folders through the network even on my own computer (i.e. I could see the folders through Caja's network browser, but they would ask for password and then "Failed to open network shares").

I purged, reloaded samba and followed the first part this tutorial for the simplest possible set-up.    [liberiangeek.net/2014/07/ubuntu-tips-create-samba-file-server-ubuntu-14-04/}

My computer shows on Caja's network browser but the allaccess folder does not show when my computer icon is clicked on, just a blank space. Obviously they are unreachable on the windows computers as well

/etc/samba/allaccess folder is there, and I think permissions look good

drwxr-xr-x   3 root    root  4096 Jun 26 22:33 samba    
drwxr-xr-x 2 michael root 4096 Jun 26 22:33 allaccess

This is all there is in smb.conf;

[global]

workgroup = WORKGROUP

server string = Samba Server %v

netbios name = srvr1

security = user

map to guest = bad user

name resolve order = bcast host

dns proxy = no

#============================ Share Definitions ==============================

[AllAccess]

path = /samba/allaccess

browsable =yes

writable = yes

guest ok = yes

read only = no
------------------------------------------------------

Thanks

---

### Post by Morbius1 on 2015-06-29
> **[COLOR=#0000cd]/etc/samba/allaccess[/COLOR]** **[COLOR=#0000cd]folder is there[/COLOR]**, and I think permissions look good

drwxr-xr-x 3 root root 4096 Jun 26 22:33 samba
drwxr-xr-x 2 michael root 4096 Jun 26 22:33 allaccess

> [AllAccess]
**[COLOR=#0000cd]path = /samba/allaccess[/COLOR]**
browsable =yes
writable = yes
guest ok = yes
read only = no
Either change the path in the share definition to point to where the folder is located ( an odd place for a shared folder ) or create the shared folder to match the path in the share definition.

---

### Post by creznedmick on 2015-06-29
Greetings, I set up the directory and folder at /samba/allaccess for the sake of this exercise. The shown lines are cut from ls -l / and ls -l /samba.
The idea is to get this set up working and then add directories an increase security

---

### Post by Morbius1 on 2015-06-30
I don't know what to tell you. Your smb.conf has been butchered but it should work more or less. Your share won't allow guest write access like you want because the Linux permissions on the folder being shared won't allow it but you should have read access.

I avoid anyone who proposes to replace the default smb.conf with their own as the HowTo suggests because that usually indicates a lack of understanding about the default settings of samba and what smb.conf is really for.  

I would restore the default smb.conf.

Add the following lines to the [global] section:
```
netbios name = srvr1
name resolve order = bcast host
```
Add the share definition:```

[allaccess]
path = /samba/allaccess
browsable = yes
writable = yes
guest ok = yes
read only = no

```
Then restart the samba services:
```
sudo service smbd restart
sudo service nmbd restart

```

You are going to have to come to terms with the permissions on the folder being shared if you truly want guest write access by all clients. So changing the permissions on /samba/allaccess  to 777 or changing the share definition to something like this are two of many options:
```
[allaccess]
path = /samba/allaccess
browsable = yes
writable = yes
guest ok = yes
read only = no
force user = michael

```

[COLOR=#0000cd]**Note**[/COLOR]: When it comes time to create what the HowTo calls the "secured" share don't do what he proposes. He has you create the share folder here:
> path = /samba/allaccess/secured
Creating a private share within a public share is goofy.

Create the share here instead: 
> path = /samba/secured

---

