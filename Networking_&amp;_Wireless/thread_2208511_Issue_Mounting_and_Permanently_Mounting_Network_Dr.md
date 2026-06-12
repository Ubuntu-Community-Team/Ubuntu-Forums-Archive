---
title: "Issue Mounting and Permanently Mounting Network Drive"
date: 2014-02-28
forum: Networking &amp; Wireless
---

### Post by wewantutopia on 2014-02-28
Hi everyone.

I've having issues mounting a network share locally.  I've had this same samba network setup for quite sometime.  Recently, I changed the physical computer that is the samba server.  I used the same smb.conf file just changing the netbios name and location of the shares.  Everything is working fine.  

Note: this samba network requires NO password to connect.

Here is the smb.conf file for the server:

```
[global]
    workgroup = OURHOME
    netbios name = dkkFileServer
    server string = Samba Server %v
    security = SHARE
    auth methods = guest
    domain master = Yes
    preferred master = Yes
    wins support = Yes
    veto files = /Thumbs.db/thumbs.db/desktop.ini/Desktop.ini
    printing = bsd
    printcap name = /etc/printcap
    load printers = yes
    log file = /var/log/samba-log.%m
    lock directory = /var/lock/samba

[Home]
        path = /home/
        read only = No
        guest ok = Yes
        force user = david
        force group = david

[Storage Drive]
        path = /media/Storage Drive/
        read only = No
        guest ok = Yes
        force user = david
        force group = david

[Music]
        path = /media/Storage Drive/Music/
        read only = No
        guest ok = Yes
        force user = david
        force group = david
```

I am able to connect and upload/download files from the server and all other peers just fine.  My music is stored on an external hard drive on the server.  To load music into the library of a peer i use this script before scanning the library:
```
#!/bin/bash

gksudo smbmount //192.168.1.250/Music /mnt/Network/Music 

nautilus /mnt/Network/Music
```

This script works fine after entering my sudo password.  I have nautilus open so I can check that the files actually mounted locally.

Recently I've setup a new computer and included it within the samba network.  Everything works fine.  I can, through nautilus, access smb://192.168.1.250/Music and play files fine.  When I executed the script to mount the share at /mnt/Network/Music nothing shows up in the folder.  The uid,gid, and other for both /mnt/Network and /mnt/Nework/Music are set for my user to be the owner and set for create and delete.

This is the part that gets me:

I tried to run, in terminal, sudo smbmount //192.168.1.250/Music /mnt/Network/Music

After entering my sudo password it prompts: Password:    Since I use no password for the samba network I just hit enter.  After which I get this error:  ```
mount error(13): Permission denied
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)
```

Out of curiosity, on other computers in the network in which this script works, I tried to run, in terminal, ```
sudo smbmount //192.168.1.250/Music /mnt/Network/Music
```  After entering my sudo password I am again promoted with:  Password:  Again, I just hit enter since there is no samba password. **On these other computers it mounts fine with no permission denied error!!**

Since this is a desktop I decided to try and permanently mount this drive via fstab.  I added this line at the bottom of my fstab file:

```
//192.168.1.250/storage\040drive/ /mnt/ cifs guest,uid=david,gid=david  0  0
```

then did ```
sudo mount -a
```  and I was met with the same ```
mount error(13): Permission denied
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs) error.
```

Ah!  I can't figure out what is going on here!  It is only this computer that is acting up.  I've set it up virtually the same as all other computers on the network running Ubuntu 12.04.

I would greatly appreciate your expert eyes/ideas here because I am going nuts!

Thanks!

---

### Post by wewantutopia on 2014-03-02
Hi guys.  Just checking back to see if anyone has any ideas for me.

Thanks!

---

### Post by xicarusx on 2014-03-02
I have a couple of suggestions. 

**One.**
Install or reinstall cifs-utils
```
sudo apt-get update && sudo apt-get install cifs-utils
```

[B]Two.
[/B]Your fstab entry is a little funky. 
This
```
[COLOR=#000000][FONT=Ubuntu Mono]//192.168.1.250/storage\040drive/ /mnt/ cifs guest,uid=david,gid=david  0  0[/FONT][/COLOR]
```
Should be this - Reason, Caps SeNSiTiVE :) Mounting to /mnt requires root access so use a sub directory or use /home/david/Network/Storage
```
[COLOR=#333333]//192.168.1.250/Storage\040Drive/ /mnt/Network/Storage cifs  guest,uid=david 0  0[/COLOR]
```

---

### Post by wewantutopia on 2014-03-03
Hi, thanks for the response!

I've tried your suggestions to no avail.

My user is the owner of /mnt/Network/ and /mnt/Network/Music with create/delete permissions.

The weird thing is that this EXACT setup works with the other systems in the network.

I also tried 
```
sudo mount -t cifs //192.168.1.250/Music /mnt/Network/Music
```

And I get the same outcome.  It asks for my sudo password, then just PASSWORD:  then 
mount error(13): Permission denied
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)

Why would it ask for a password when there is no password required for my samba network??

---

