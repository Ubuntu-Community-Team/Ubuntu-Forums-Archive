---
title: "Strange smbfs problem"
date: 2006-10-23
forum: Networking &amp; Wireless
---

### Post by cosborn72 on 2006-10-23
I've been using ubuntu for a while, and have had little difficulty as far as networking.  This one, however, stumps me.

I have a (K)ubuntu desktop running Dapper trying to connect to a Debian server through SMB.

I can access the network folders and edit files, but I can't copy or save anything to the network. i.e - no write permission.

Here is my fstab. (I added the fmask and dmask while troubleshooting).

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
//192.168.1.100/public  /media/cprcd    smbfs   username=chris,password=##########,dmask=777,fmask=777  0       0

Here is the directory from the mounted folder in media/cprcd.

```
drwxr-xr-x 1 root root 0 2006-06-20 09:12 bryan
drwxr-xr-x 1 root root 0 2006-10-18 14:48 candy
drwxr-xr-x 1 root root 0 2006-10-19 13:12 chris
drwxr-xr-x 1 root root 0 2006-10-10 10:44 clientapps
drwxr-xr-x 1 root root 0 2006-10-23 07:42 dropbox
drwxr-xr-x 1 root root 0 2006-09-05 11:26 EC
drwxr-xr-x 1 root root 0 2006-06-19 11:29 erin
drwxr-xr-x 1 root root 0 2006-10-20 14:34 hometeam
drwxr-xr-x 1 root root 0 2006-07-10 13:23 lindy
drwxr-xr-x 1 root root 0 2006-10-03 08:12 logos
drwxr-xr-x 1 root root 0 2006-06-19 09:49 mike
drwxr-xr-x 1 root root 0 2006-06-19 11:20 pictures
drwxr-xr-x 1 root root 0 2006-06-19 10:28 sara
drwxr-xr-x 1 root root 0 2006-10-18 14:13 stephanie

```

Here is what the server shows for that same folder. Note the permission difference.

```
drwxrwxrwx   3 chris  chris   4096 2006-06-20 09:12 bryan
drwxrwxrwx  23 chris  chris   4096 2006-10-18 14:48 candy
drwxrwxrwx  13 chris  chris   4096 2006-10-19 13:12 chris
drwxrwxrwx   5 chris  chris   4096 2006-10-10 10:44 clientapps
drwxrwxrwx  49 chris  chris   4096 2006-10-23 07:42 dropbox
drwxrwxrwx  63 chris  chris   4096 2006-09-05 11:26 EC
drwxrwxrwx  37 chris  chris   4096 2006-06-19 11:29 erin
drwxrwxrwx  18 chris  chris   4096 2006-10-20 14:34 hometeam
drwxrwxrwx  66 chris  chris   4096 2006-07-10 13:23 lindy
drwxrwxrwx  11 chris  chris   4096 2006-10-03 08:12 logos
drwxrwxrwx   6 chris  chris   4096 2006-06-19 09:49 mike
drwxrwxrwx  48 chris  chris   4096 2006-06-19 11:20 pictures
drwxrwxrwx  15 chris  chris   4096 2006-06-19 10:28 sara
drwxrwxrwx   2 nobody nogroup 4096 2006-10-18 14:13 stephanie

```

Here is my dmesg | tail
```
[17179597.240000] Bluetooth: L2CAP ver 2.8
[17179597.240000] Bluetooth: L2CAP socket layer initialized
[17179597.264000] Bluetooth: RFCOMM socket layer initialized
[17179597.264000] Bluetooth: RFCOMM TTY layer initialized
[17179597.264000] Bluetooth: RFCOMM ver 1.7
[17179599.596000] [drm] Initialized drm 1.0.1 20051102
[17179599.596000] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 177
[17179599.596000] [drm] Initialized i915 1.4.0 20060119 on minor 0
[17179602.780000] eth0: no IPv6 routers present
[17182195.056000] smb_lookup: find hometeam/.directory failed, error=-512
```

Lastly, here is the share from the smb.conf file in Debian
```
[public]
comment= Public Folder
path = /home/public
public=yes
writable=yes
create mask=0777
directory mask=0777
force user=nobody
force group=nogroup

```

As you can see, I've removed every conceivable security protection I can:) , so I can't figure out why it is not allowing me to write.

---

### Post by dbott67 on 2006-10-23
What type of filesystem is on the 192.168.1.100 server (or what is the OS of the server)?  EDIT: D'oh --- can't read so well... I see it's Debian server).

*I'll leave this in for others that may have problems writing to a Windows system.*

**[nevermind=cosborn72]**

If it's a Windows sytems (NT/XP, 2000/2003) the default filesystem is NTFS, which in generally 'Read Only' in linux.  There are newer packages, such as 'captive ntfs' that allow read/write access, but they are experimental/alpha (i.e. they could hose your files.

Best option is to format the partition/volume as FAT... then all OSes can read it (Windows, Linux, OSX, etc.).
**[/nevermind]**

-Dave

---

### Post by dbott67 on 2006-10-23
Here's a HOWTO I wrote on [connecting to an SMB server]("http://www.ubuntuforums.org/showthread.php?t=280473").  The only difference I notice between mine & yours is the fstab.
```
//192.168.1.2/Music /home/dbott/music   smbfs  [COLOR="Red"]auto[/COLOR],username=dbott,password=mysecretpassword,[COLOR="Red"]uid=1000,umask=000,user   0 0[/COLOR]
```

vs.

```
//192.168.1.100/public /media/cprcd smbfs username=chris,password=##########,[COLOR="Red"]dmask=777,fmask =777 0 0[/COLOR]
```


[http://www.ubuntuforums.org/showthread.php?t=280473](http://www.ubuntuforums.org/showthread.php?t=280473)

---

### Post by dbott67 on 2006-10-23
Just a few other things I'm noticing that are different.  Not that I'm sure which one is right or wrong --- just that they aren't the same.

Keep in mind that my "server" is not a Debian or Ubuntu box --- it's just a little NexStar NAS device, so I'm kind of limited as to what access I have to the config files (it's all done via administrative web page).

From my client PC, my mounted folder has the following permissions:
```

drwxr-xr-x  1 [COLOR="Red"]dbott[/COLOR] root       4096 2006-10-19 11:14 music

```

When I connect to the NAS (via FTP) and do a directory listing, this is what I get:
```
dbott@thedrake:$ ftp 192.168.1.2

Connected to 192.168.1.2.
220 NET Disk FTP Server ready.
Name (192.168.1.2:dbott): dbott
331 User name okay, need password.
Password:
230 User logged in, proceed.
Remote system type is UNIX.
Using binary mode to transfer files.

ftp> ls -all
200 Command okay.
150 File status okay; about to open data connection.
drw-rw-rw-   1 user     group           0 Jan  1 00:02 PUBLIC
drw-rw-rw-   1 user     group           0 Jan  1 00:02 Data
drw-rw-rw-   1 user     group           0 Jan  1 02:01 Archive
drw-rw-rw-   1 [COLOR="Red"]user     group[/COLOR]           0 Sep  1 22:02 Music
226 Closing data connection.
ftp>
```

Again, the difference is that on your server, the owner & group is 'chris'.  Perhaps it might be an ownership issue.  I've never setup Linux to be a dedicated SMB server (only limited filesharing through Ubuntu, so I don't really have any expertise configuring the SMB server).

-Dave

---

### Post by cosborn72 on 2006-10-27
Well, the problem seems to have gone away- I don't know why, but I will keep looking around and seeing if I can find anything funky. 

Thanks for you help dbott!

---

### Post by dbott67 on 2006-10-27
Glad all is working... if you do happen to figure out what was wrong, let us know.  Update to a package maybe?

-Dave

---

