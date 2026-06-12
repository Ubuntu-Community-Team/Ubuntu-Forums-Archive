---
title: "DVD ROM shares in SAMBA"
date: 2014-08-15
forum: Networking &amp; Wireless
---

### Post by x-terry on 2014-08-15
I have recently installed SAMBA on ubuntu 14.04 and configured some shares, most of which are working. but I am having issues sharing the DVD drives.
A connecting windows 7 pc reports that "you do not have permissions to access \\192.168.1.100\DVD-ROM Drive 0..."

Section of smb.conf file:

```
#======================= Share Definitions =======================


# Un-comment the following (and tweak the other settings below to suit)
# to enable the default home directory shares. This will share each
# user's home directory as \\server\username
[homes]
   comment = Home Directories
   browseable = no


# By default, the home directories are exported read-only. Change the
# next parameter to 'no' if you want to be able to write to them.
   read only = no


[external1]
   comment = eternal1 usb drive
   path = /media/terry/external1
#  required for NTFS drives
   force user = terry


[backup]
   comment = backup usbdrive
   path = /media/terry/backup
#  required for NTFS drives
   force user = terry

[DVD-ROM Drive 0]
   path = /cdrom
   browseable = yes
   read only = no
   guest ok = yes
   locking = no
   preexec = /bin/mount /cdrom
   postexec = /bin/umount /cdrom


[DVD-ROM Drive 1]
   path = /cdrom1
   browseable = yes
   read only = yes
   guest ok = yes
   locking = no
   preexec = /bin/mount /cdrom1
   postexec = /bin/umount /cdrom1




```

Also a section from my fstab file:

```
#add dvd drives
/dev/sr0 /cdrom iso9660 defaults,noauto,ro,user 0 0
/dev/sr1 /cdrom1 iso9660 defaults,noauto,ro,user 0 0



```

---

### Post by bab1 on 2014-08-15
> **x-terry said:**
> I have recently installed SAMBA on ubuntu 14.04 and configured some shares, most of which are working. but I am having issues sharing the DVD drives.
A connecting windows 7 pc reports that "you do not have permissions to access \\192.168.1.100\DVD-ROM Drive 0..."

...



Who is the Linux owner:group of the DVD-ROM drive?  You can set that with uid and gid settings in your fstab declaration.  Read the appropriate section of the mount man page```
man mount
```

---

### Post by x-terry on 2014-08-15
I did some playing around. Somehow, I have the second drive working and the first one still not.

I changed my fstab to:

```

#add dvd drives
/dev/sr0 /cdrom0 iso9660 defaults,noauto,ro,user 0 0
/dev/sr1 /cdrom1 iso9660 defaults,noauto,ro,user 0 0

```

and my smb.conf to:

```

[DVD-ROM Drive 0]
   path = /cdrom0
   browseable = yes
   read only = no
   guest ok = yes
   locking = no
   preexec = /bin/mount /cdrom0
   postexec = /bin/umount /cdrom0

[DVD-ROM Drive 1]
   path = /cdrom1
   browseable = yes
   read only = yes
   guest ok = yes
   locking = no
   preexec = /bin/mount /cdrom1
   postexec = /bin/umount /cdrom1

```

The interesting part is the ownership as you mentioned:
ls -al of the root dir showed:

```

drwx------   3 nobody  401  2048 Nov  7  2012 cdrom0
dr-xr-xr-x   1 root   root  2048 Aug 20  2013 cdrom1

```

I checked and DVD-ROM Drive 1 is working and DVD-ROM Drive 0 is not. Ican't understand why the first one is owned by nobody and the group is 401.
I tried change it with chown but this failed.

```

root@Server:/# chown -v root:root cdrom0
chown: changing ownership of &#8216;cdrom0&#8217;: Read-only file system
failed to change ownership of &#8216;cdrom0&#8217; from nobody:401 to root:root
root@Server:/# 

```

---

### Post by bab1 on 2014-08-15
> **x-terry said:**
> I did some playing around. Somehow, I have the second drive working and the first one still not.

I changed my fstab to:

```

#add dvd drives
/dev/sr0 /cdrom0 iso9660 defaults,noauto,ro,user 0 0
/dev/sr1 /cdrom1 iso9660 defaults,noauto,ro,user 0 0

```

and my smb.conf to:

```

[DVD-ROM Drive 0]
   path = /cdrom0
   browseable = yes
   read only = no
   guest ok = yes
   locking = no
   preexec = /bin/mount /cdrom0
   postexec = /bin/umount /cdrom0

[DVD-ROM Drive 1]
   path = /cdrom1
   browseable = yes
   read only = yes
   guest ok = yes
   locking = no
   preexec = /bin/mount /cdrom1
   postexec = /bin/umount /cdrom1

```

The interesting part is the ownership as you mentioned:
ls -al of the root dir showed:

```

drwx------   3 nobody  401  2048 Nov  7  2012 cdrom0
dr-xr-xr-x   1 root   root  2048 Aug 20  2013 cdrom1

```

I checked and DVD-ROM Drive 1 is working and DVD-ROM Drive 0 is not. Ican't understand why the first one is owned by nobody and the group is 401.
I tried change it with chown but this failed.

```

root@Server:/# chown -v root:root cdrom0
chown: changing ownership of &#8216;cdrom0&#8217;: Read-only file system
failed to change ownership of &#8216;cdrom0&#8217; from nobody:401 to root:root
root@Server:/# 

```
I'm surprised you missed this from the man pages```
Mount options for iso9660
       ISO  9660  is  a  standard  describing a filesystem structure to be used on CD-ROMs. (This
       filesystem type is also seen on some DVDs. See also the udf filesystem.)
...

       uid=value and gid=value
              Give  all files in the filesystem the indicated user or group id, possibly overrid&#8208;
              ing the information found in the Rock Ridge extensions.  (Default: uid=0,gid=0.)


```

What this means is that you get to set the ownership at mount time ( the default is 0 (root)).

It is entirely possible to the file manager, in the absence of any specific data, to make a guess as to the ownership.  Using your reference to the user nobody and the group of 401, I would say the guess was due to the share parameter of *guest ok = yes*, as it forces all users to be identified as *nobody*.  The group 401 has no named identity.  The OS uses the uid and gid.  Let's see what you get by posting the results of this command```
getent group 401
```

You can't change anything once the DVD is mounted so chmod and chown don't help in this instance.

I would have added something like this to the mount options```
uid=1000,gid=1000
```
In this manner the first user of the system (maybe you) would become the owner:group-owner of the DVD file system.

The reason cdrom1 works is that the *others* group has r-x (read and eXecute permissions).  These are the 3rd set of permissions (r-xr-xr-x ) as in: owner:group:others.

---

### Post by x-terry on 2014-08-16
Thanks,
adding uid and gid to the fstab file fixed it.

FYI The following returns nothing.
```

root@Server:/# getent group 401
root@Server:/# 

```

---

