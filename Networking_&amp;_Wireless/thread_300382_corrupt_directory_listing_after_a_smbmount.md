---
title: "corrupt directory listing after a smbmount"
date: 2006-11-15
forum: Networking &amp; Wireless
---

### Post by tfotherby on 2006-11-15
Hi,

I have a NAS (Network-Addressed Storage) drive connected to my network and I have installed samba and so can access it fine by going to Places -> Network Servers then Windows Network -> Kixntom -> Bitbucket -> Public.

But I want to work with the command line and so I need to mount my network harddisk. If I run '[COLOR="RoyalBlue"]smbclient -L //BITBUCKET[/COLOR]' I get:

[COLOR="SeaGreen"]        Sharename       Type      Comment
        ---------       ----      -------
        PUBLIC          Disk
        IPC$            IPC

        Server               Comment
        ---------            -------

        Workgroup            Master
        ---------            -------[/COLOR]

Furthermore, if I run '[COLOR="RoyalBlue"]smbclient \\\\BITBUCKET\\public[/COLOR]' I get a prompt and get to do 'ls' and ftp-ish stuff. But it's slow and tedious so I really really want to use smbmount. However, if I run '[COLOR="RoyalBlue"]sudo smbmount \\\\BITBUCKET\\public /mnt/OurNASDisk/[/COLOR]' and do '[COLOR="RoyalBlue"]ls /mnt/OurNASDisk[/COLOR]' I get:

[COLOR="SeaGreen"]                  ???  ??2???  N???  p#? ^??  _successful?? ^?[/COLOR]

i.e. A corrupt filesystem.

Does anyone know why smbmount isn't working for me? Perhaps I need to know more about the filesystem on my NAS?

Any ideas at all?

Thanks,
Tom

---

### Post by dmizer on 2006-11-15
try the third link in my thread.  use cifs instead of smbmount.

---

### Post by tfotherby on 2006-11-16
I'm still having no luck after trying cifs.

```

sudo mount -t cifs //BITBUCKET/PUBLIC /mnt/OurNASDisk/ -o username=****,password=******,iocharset=utf8,file_mode=0777,dir_mode=0777

```

gives:

```

mount error 20 = Not a directory
Refer to the mount.cifs(8) manual page (e.g.man mount.cifs)

```

I'm not sure whether I have got the '//netbiosname/sharename' part right. 

I'm assuming:

netbiosname = BITBUCKET
sharename   = PUBLIC

If I run 'smbtree' I get:

```

KIXNTOM
        \\HANTARIO                      hantario server (Samba, Ubuntu)
                \\HANTARIO\print$               Printer Drivers
                \\HANTARIO\IPC$                 IPC Service (hantario server (Samba, Ubuntu))
                \\HANTARIO\ADMIN$               IPC Service (hantario server (Samba, Ubuntu))
        \\BITBUCKET
                \\BITBUCKET\IPC$
                \\BITBUCKET\PUBLIC

```

I have installed winbind and restarted my network.

Using the IP address also doesn't work:

```

sudo mount -t cifs //192.168.0.4/PUBLIC /mnt/OurNASDisk/ -o username=****,password=******,iocharset=utf8,file_mode=0777,dir_mode=0777

```

Anyone got any ideas?

---

### Post by dmizer on 2006-11-16
linux is case sensitive.  is there a directory in mnt that reads exactly "OurNASDisk" ?

otherwise everything looks okay.  you have the netbios name and share name correct so ... not sure.  if that doesn't work, try this:
```
sudo mount -t cifs //BITBUCKET/PUBLIC /mnt/OurNASDisk/ --verbose -o username=****,password=******,iocharset=utf8,file_mode=0777,dir_mode=0777
```

---

### Post by tfotherby on 2006-11-16
The OurNASDisk directory exists.

[COLOR="SeaGreen"]ls -l /mnt/[/COLOR]

gives:

```

drwxr-xr-x 2 root root 4096 2006-11-04 11:20 OurNASDisk

```

[COLOR="SeaGreen"]sudo mount -t cifs //BITBUCKET/PUBLIC /mnt/OurNASDisk/ --verbose -o username=****,password=******,iocharset=utf8,file_mode=0777,dir_mode=0777[/COLOR]

gives:

```

parsing options: rw,username=*****,password=*****,iocharset=utf8,file_mode=0777,dir_mode=0777

mount.cifs kernel mount options unc=//BITBUCKET\PUBLIC,ip=192.168.0.4,ver=1,rw,username=*****,password=*****,iocharset=utf8,file_mode=0777,dir_mode=0777
mount error 20 = Not a directory
Refer to the mount.cifs(8) manual page (e.g.man mount.cifs)

```

](*,)

---

### Post by dmizer on 2006-11-16
try both of the following:
first: replace "PUBLIC" with "public" and see if you can mount then.
second: replace "BITBUCKET" with 192.168.0.4 and see if you can mount then.

something fishy about these nas units i haven't quite figured out yet.

---

### Post by tfotherby on 2006-11-16
Thanks for your suggestions but still no luck.

```

sudo mount -t cifs //BITBUCKET/public /mnt/OurNASDisk/ --verbose -o username=*****,password=*****,iocharset=utf8,file_mode=0777,dir_mode=0777
sudo mount -t cifs //BITBUCKET/Public /mnt/OurNASDisk/ --verbose -o username=*****,password=*****,iocharset=utf8,file_mode=0777,dir_mode=0777
sudo mount -t cifs //BITBUCKET/PUBLIC /mnt/OurNASDisk/ --verbose -o username=*****,password=*****,iocharset=utf8,file_mode=0777,dir_mode=0777
sudo mount -t cifs //192.168.0.4/PUBLIC /mnt/OurNASDisk/ --verbose -o username=*****,password=*****,iocharset=utf8,file_mode=0777,dir_mode=0777
sudo mount -t cifs //192.168.0.4/Public /mnt/OurNASDisk/ --verbose -o username=*****,password=*****,iocharset=utf8,file_mode=0777,dir_mode=0777
sudo mount -t cifs //192.168.0.4/public /mnt/OurNASDisk/ --verbose -o username=*****,password=*****,iocharset=utf8,file_mode=0777,dir_mode=0777

```

all return:

```

parsing options: rw,username=admin,password=Tom$crap,iocharset=utf8,file_mode=0777,dir_mode=0777

mount.cifs kernel mount options unc=//192.168.0.4\Public,ip=192.168.0.4,ver=1,rw,username=*****,password=*****,iocharset=utf8,file_mode=0777,dir_mode=0777
mount error 20 = [COLOR="Red"]Not a directory[/COLOR]
Refer to the mount.cifs(8) manual page (e.g.man mount.cifs)

```

and

```

sudo mount -t smbfs //BITBUCKET/public /mnt/OurNASDisk/ -o username=*****,password=*****,iocharset=utf8,file_mode=0777,dir_mode=0777
sudo mount -t smbfs //BITBUCKET/Public /mnt/OurNASDisk/ -o username=*****,password=*****,iocharset=utf8,file_mode=0777,dir_mode=0777
sudo mount -t smbfs //BITBUCKET/PUBLIC /mnt/OurNASDisk/ -o username=*****,password=*****,iocharset=utf8,file_mode=0777,dir_mode=0777
sudo mount -t smbfs //192.168.0.4/PUBLIC /mnt/OurNASDisk/ -o username=*****,password=*****,iocharset=utf8,file_mode=0777,dir_mode=0777
sudo mount -t smbfs //192.168.0.4/Public /mnt/OurNASDisk/ -o username=*****,password=*****,iocharset=utf8,file_mode=0777,dir_mode=0777
sudo mount -t smbfs //192.168.0.4/public /mnt/OurNASDisk/ -o username=*****,password=*****,iocharset=utf8,file_mode=0777,dir_mode=0777

```

all return ok but a '[COLOR="SeaGreen"]ls /mnt/OurNASDisk/[/COLOR]' shows a corrupt file system:

```

                  ???  ??2???  N???  p#? ^??  _successful

```

Oh well, nevermind. I will use '[COLOR="SeaGreen"]smbclient //BITBUCKET/PUBLIC[/COLOR]' as a workaround and I will replace Dapper with Edgy to see if it improves things.

If I do get it working, I'll make sure to update this thread.

Thanks for your help dmizer.

---

### Post by dmizer on 2006-11-16
well, it's not help if you're not fixed.  the file that's on your NAS device ... does it have any non-latin characters in it's name?  it could be simply that your cli doesn't have the necessary font to display the file name correctly.

---

### Post by tfotherby on 2006-11-17
No, there's nothing unusual about the file names in the NAS filesystem that I want to mount.

This shows the contents:

```

[FONT="Courier New"]tf98@hantario:~$ smbclient //BITBUCKET/PUBLIC
Password:
smb: \> ls
  .                                   D        0  Sat Jan  1 00:00:32 2005
  ..                                  D        0  Sat Jan  1 00:00:32 2005
  OurVideo                            D        0  Thu Dec  7 22:22:28 2006
  Chloe                               D        0  Thu Dec  7 19:00:52 2006
  OurPics                             D        0  Sun Mar  4 05:47:12 2007
  OurMusic                            D        0  Thu Dec  7 19:06:36 2006
  OurApps                             D        0  Sun Dec 10 02:36:08 2006
  OurPlayLists                        D        0  Sun Dec 10 02:36:26 2006
  Temp                                D        0  Wed Dec 20 11:52:12 2006
  Toms_backups                        D        0  Thu Dec  7 19:05:30 2006
  .sudo_as_admin_successful           A        0  Tue Jan 19 03:14:07 2038

                17881 blocks of size 16777216. 13903 blocks available
smb: \>[/FONT]

```

---

### Post by dmizer on 2006-11-20
do you see: .sudo_as_admin_successful when you mount the share in windows?  it seems that samba is choking on that file.

---

### Post by tfotherby on 2006-11-20
I removed .sudo_as_admin_successful and tried mounting again - No Luck. There are probably other files in the directory structure with special chars e.g. ".", " ", "&" etc but I can't remove/rename them all.

I'll get by using the gnome GUI and 'smbclient -L //BITBUCKET' to access the NAS drive. mounting the NAS file system is really just a  "nice to have" rather than being essential.

---

