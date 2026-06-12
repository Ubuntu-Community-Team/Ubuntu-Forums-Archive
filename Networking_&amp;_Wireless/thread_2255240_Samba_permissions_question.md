---
title: "Samba permissions question"
date: 2014-12-03
forum: Networking &amp; Wireless
---

### Post by osborni on 2014-12-03
Current setup

14.04 Ubuntu machine running samba with a 2T share drive. (/srv/samba/share/) This drive is intended to be a movie server for a modest library of DVDs and a music server for good sized library.

I have a Windows 7 machine running in the living room. This is the client machine.

I am running a Plex media server on the Ubuntu box. The W7 machine is the client and is hooked up to the home theater. 

I'm not really worried about user security behind my router's firewall. I'm the only user of the server and the client machine.

What I've been struggling to figure out is the Samba permissions.

If I type:

sudo chmod -R 777 /srv/samba/share

everything works the way I want it too. The client machine needs to be able to read, write and execute on the samba server.

I need to type the chmod command at every re-boot. I'm pretty sure that the chmod is over-riding the smb.conf permissions as that is post boot.

What is the correct smb.conf command set to basically do a 777 permission on the share folders?

---

### Post by bab1 on 2014-12-03
> **osborni said:**
> Current setup

14.04 Ubuntu machine running samba with a 2T share drive. (/srv/samba/share/) This drive is intended to be a movie server for a modest library of DVDs and a music server for good sized library.

It's not at all clear whether the shared directory resides on a separate (possibly external) physical device or is just a partition of the main drive.  More importantly; what file system formatting (ext4 or...) is the partition that holds the data at */srv/samba/share/*?  If this is an external USB connected hard drive with NTFS formating then chmod commands will have no effect.
> 

I have a Windows 7 machine running in the living room. This is the client machine.

I am running a Plex media server on the Ubuntu box. The W7 machine is the client and is hooked up to the home theater. 

I'm not really worried about user security behind my router's firewall. I'm the only user of the server and the client machine.

What I've been struggling to figure out is the Samba permissions.

If I type:

sudo chmod -R 777 /srv/samba/share

everything works the way I want it too. The client machine needs to be able to read, write and execute on the samba server.

I need to type the chmod command at every re-boot. I'm pretty sure that the chmod is over-riding the smb.conf permissions as that is post boot.

What is the correct smb.conf command set to basically do a 777 permission on the share folders?
The chmod command sets the permissions mode for Linux type file system formatting (ext).  Samba permissions are for the access to the share at the Samba application level.  These are two different conditions.

This issue is most likely going to need more than one simple command to resolve.  Setting the permissions on existing files and directories is only a partial solution.  You also need to control the access to newly created files and directories also.  If the partition is formatted NTFS then you can only set the permissions at mount time via mount options.

More information is needed to determine what you need to do.  Please post the output of this command```

sudo blkid -c /dev/null -o list

```

---

### Post by osborni on 2014-12-03
OK - thanks. I'll pull that tonight.  

The samba drive is a partition on the Ubuntu machine. Physically the same drive as the Ubuntu installation. Same format as Ubuntu. (not NTFS, but I can't remember the specific formation as I type this. ext3 I think?).

---

### Post by bab1 on 2014-12-03
> **osborni said:**
> OK - thanks. I'll pull that tonight.  

The samba drive is a partition on the Ubuntu machine. Physically the same drive as the Ubuntu installation. Same format as Ubuntu. (not NTFS, but I can't remember the specific formation as I type this. ext3 I think?).

Samba shares directories not drives.  In Linux speak, a drive is the physical device.  The partition is all or part of that drive's space.  What I'm looking for is the ability to set the current permissions via chmod and what to do about users ownership of the files and subdirectories in the directory that is shared by Samba.

After we get that set up correctly we can talk about any adjustments to the Samba Share definitions.

To my way of thinking the users should be known to both Linux and Samba.  I believe you are already the Ubuntu first user (uid 1000).  You should create a Samba user for that username too.

In addition to the other info, post the output of these commands```
sudo pdbedit -L

getent passwd 1000

ls -l /srv/samba
```...the first one shows the Samba users.  The second one shows the user that installed Ubuntu (you???).  The third command lists the permissions and ownership of the directory that is shared.  I believe plex is a user also.  Is that so?  If you aren't sure you can check using this command```
getent passwd plex
```...this command checks for the existence of the user *plex * in the users file (e.g. passwd)

---

### Post by osborni on 2014-12-03
sudo pdbedit -L - returned nothing


sudo blkid -c /dev/null -o list
> [COLOR=#222222][FONT=Verdana]device     fs_type label    mount point    UUID[/FONT][/COLOR]-------------------------------------------------------------------------------
/dev/sda1  ext4             /boot           efa5d8f3-c34a-4c23-9ad1-1edeca148481
/dev/sda5  ext4             /                   4a42a7a8-13c4-4315-aed4-0a690ac80e1f
/dev/sda6  ext4             /home           6e488266-94aa-45fb-b172-ac96233339cf
/dev/sda7  ext4             /srv               930702a2-391c-4c98-91b8-501b5da2a279
/dev/sda8  swap             <swap>       13b31577-ca1d-4cc2-ae41-876890621e65

getent passwd 1000
> ian: x : 1000:1000:Ian,,,:/home/ian:/bin/bash

ls -l /srv/samba
> total 4drwxrwxrwx 6 nobody nogroup 4096 Nov 27 18:33 share


---

### Post by osborni on 2014-12-03
getent passwd plex
> plex: x :116:125::/var/lib/plexmediaserver:/bin/bash

---

### Post by bab1 on 2014-12-03
> **osborni said:**
> sudo pdbedit -L - returned nothing

sudo blkid -c /dev/null -o list
```

device  fs_type  label  mount point      UUID
-------------------------------------------------------------------------------
/dev/sda1   ext4   /boot   efa5d8f3-c34a-4c23-9ad1-1edeca148481
/dev/sda5   ext4   /      4a42a7a8-13c4-4315-aed4-0a690ac80e1f
/dev/sda6   ext4   /home    6e488266-94aa-45fb-b172-ac96233339cf
/dev/sda7   ext4   /srv    930702a2-391c-4c98-91b8-501b5da2a279
/dev/sda8   swap  <swap>    13b31577-ca1d-4cc2-ae41-876890621e65
```

getent passwd 1000
```
getent passwd 1000
ian: x : 1000:1000:Ian,,,:/home/ian:/bin/bash
```

ls -l /srv/samba
```
ls -l /srv/samba
total 4drwxrwxrwx 6 nobody nogroup 4096 Nov 27 18:33 share
```


It appears that there is no Samba users other than the guest user/group of nobody/nogroup. The partition is an ext type and will respond to chmod.  In fact the permissions at the /srv/samba/share is set to 777.

What are the file and directory ownership and permissions below /srvlsamba/share.  Post the output of ```
ls -l /srv/samba/srv/share
```...if you only have directories just below /srv/samba/share, post the output of what is in one of those sub-directories.

Let's have a look at the smb.conf file.  Post the output of```
cat /etc/samba/smb.conf
```

It is hard to read the output of the text unless you post the output using the [code] blocks.  This preserves the fixed width formatting.  To do this click on the **[SIZE=4]#  [/SIZE]** icon.  This is available at the top right next to the *quote *icon in the advanced mode of the reply editor.

I see there is a user *plex*.

My guess is that not all the files and folders are set to 777 under the shared directory.  We shall see with your next reply.

---

### Post by osborni on 2014-12-04
```
ls -l /srv/samba/share

total 16
drwxrwxrwx  5 ian    ian     4096 Nov 29 22:51 Extras
drwxrwxrwx 74 root   root    4096 Dec  4 06:52 movies
drwxrwxrwx  5 root   root    4096 Nov 29 08:58 music
drwxrwxrwx  3 nobody nogroup 4096 Nov 30 16:02 Program Files



```

I noticed that ownership of the 4 directories is mixed. Those should be consistent given that the usage is consistent? Extras, movies and music are for Plex. Program Files is really a quick and dirty file dump to move files between computers.

I did some reading and I think it is working properly - though having everything at 777 and user forced to root without "proper" permissions setup is rather crude.  

```
[share]  comment = Ubuntu-basement File Server Share
    path = /srv/samba/share
    browsable = yes
    guest ok = yes
    writable = yes
    read only = no
    create mask = 777
    directory mask = 777
    force create mode = 777 #file permissions
    force directory mode = 777 #directory permissions
    force user = root
    force group = root

```

---

### Post by bab1 on 2014-12-04
> **osborni said:**
> ```
ls -l /srv/samba/share

total 16
drwxrwxrwx  5 ian    ian     4096 Nov 29 22:51 Extras
drwxrwxrwx 74 root   root    4096 Dec  4 06:52 movies
drwxrwxrwx  5 root   root    4096 Nov 29 08:58 music
drwxrwxrwx  3 nobody nogroup 4096 Nov 30 16:02 Program Files



```

I noticed that ownership of the 4 directories is mixed. Those should be consistent given that the usage is consistent? Extras, movies and music are for Plex. Program Files is really a quick and dirty file dump to move files between computers.

This can happen when you add directories directly at the server.  I'll bet you changed the Samba share definitions also.  It appears that the chmod command worked however.
> 

I did some reading and I think it is working properly - though having everything at 777 and user forced to root without "proper" permissions setup is rather crude. 

It is crude.  The share definition is also something I would not do.  I would put the user *plex* and the user *ian* in a common group.  You can use the group *_users_* if you like or make your own group (maybe *_htpc_*).   I would set the group ownership (GID) on the /srv/samba/share directory to the common group (i.e.: sudo chown -R root:htpc <or root:users> /srv/samba/share).  Then you set the inheritance of the group ownership with ```
sudo chmod -R 2775 /srv/samba/share 
```

Now set the Samba share definition to this.  Some of the parameters were redundant.

```
[share]  comment = Ubuntu-basement File Server Share
    path = /srv/samba/share
    browsable = yes
    guest ok = yes
    writable = yes

[COLOR="#FF0000"]    create mask = 0664    # this seems to preserve file permissions better for me
    force directory mode = 2775   # sets directory permissions
    force group = *users*        # or htpc if that is what you use[/COLOR]

```

One last thing.  make sure that the ownership of the parent directories (/srv and /srv/samba are owned by root:root and the permissions on those directories is 0775.  Now all users that are part of the common group (i.e. *_users_* or *_htpc_*) have read/write access to the data.  All others have read access.  The* force group* parameter will insure that the common group is correct if you create files later on.

Questions or comments?

---

