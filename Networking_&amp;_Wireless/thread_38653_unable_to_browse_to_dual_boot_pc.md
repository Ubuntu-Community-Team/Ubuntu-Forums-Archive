---
title: "unable to browse to dual boot pc"
date: 2005-06-01
forum: Networking &amp; Wireless
---

### Post by n21roadie on 2005-06-01
I am able to browse to other pc's on my home network ,

but i am unable to browse to this pc ( dual boot Xp + ubuntu - Scsi hard drive ) own network files , 

in wind*ws this pc is listed on the network as "kitchen_pc", 

it is not showing under ubuntu places/network server, the other pc's are ,

i assume i must have not configured samba correctly ?, also i best mention that , i have two network cards installed (1) static ip 11.*.*.3 , this one is for the home network and nic (2) dynamic ip for internet ,from dsl router modem , and this pc is my internet server for the network ,i havn't setup this pc as internet server yet, one
step at the time?, i have however installed firestarter ( Firewall )

---

### Post by Alexander Kirillov on 2005-06-01
[QUOTE=n21roadie]I am able to browse to other pc's on my home network ,

but i am unable to browse to this pc ( dual boot Xp + ubuntu - Scsi hard drive ) own network files , 

in wind*ws this pc is listed on the network as "kitchen_pc", 

it is not showing under ubuntu places/network server, the other pc's are ,

i assume i must have not configured samba correctly ?, also i best mention that , i have two network cards installed (1) static ip 11.*.*.3 , this one is for the home network and nic (2) dynamic ip for internet ,from dsl router modem , and this pc is my internet server for the network ,i havn't setup this pc as internet server yet, one
step at the time?, i have however installed firestarter ( Firewall )[/QUOTE]
 Do I understand you correclty? You want to see shared files which are  in Windows folders on this pc - when loggged in to Ubuntu *on this computer*? But obviously, when you are logged in  Ubuntu, Windows is not running, and it is not serving any files. If this is your problem, look here: 
[http://ubuntuguide.org/#windows](http://ubuntuguide.org/#windows)

Or do you want to see the files on this pc *from* other computers?

---

### Post by n21roadie on 2005-06-01
[HTML]Do I understand you correclty? You want to see shared files which are in Windows folders on this pc - when loggged in to Ubuntu *on this computer*? But obviously, when you are logged in Ubuntu, Windows is not running, and it is not serving any files. If this is your problem, look here:
[http://ubuntuguide.org/#windows](http://ubuntuguide.org/#windows)[/HTML] 

Yes , i want to see windows files when i am logged into ubuntu , same hard drive ( Scsi ) different partition , but more important is the Ide drive (ntfs) attached to this pc , which has files i want to see, i followed you link to ubuntu guide ,which resulted in "busy" ,when i tried to mount the device ??


~$ sudo fdisk -l

Disk /dev/sda: 9100 MB, 9100032000 bytes
255 heads, 63 sectors/track, 1106 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           3       24066   14  Hidden FAT16 <32M
/dev/sda2   *           4         555     4433940    7  HPFS/NTFS
/dev/sda3             556        1106     4425907+  83  Linux

Disk /dev/sdb: 9105 MB, 9105018880 bytes
255 heads, 63 sectors/track, 1106 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         553     4441941   83  Linux
/dev/sdb2   *         554        1106     4441972+   7  HPFS/NTFS

Disk /dev/hda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4865    39078081    7  HPFS/NTFS

Disk /dev/sdc: 512 MB, 512483328 bytes
16 heads, 63 sectors/track, 993 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1         992      499851+   6  FAT16
james@james:~$ sudo mount /dev/sdb /media/windows/ -t ntfs -o umask=0222
mount: /dev/sdb already mounted or /media/windows/ busy
james@james:~$ sudo mount /dev/sda /media/windows/ -t ntfs -o umask=0222
mount: /dev/sda already mounted or /media/windows/ busy
james@james:~$ sudo mount /dev/hda /media/windows/ -t ntfs -o umask=0222
mount: /dev/hda already mounted or /media/windows/ busy```
Do I understand you correclty? You want to see shared files which are in Windows folders on this pc - when loggged in to Ubuntu *on this computer*? But obviously, when you are logged in Ubuntu, Windows is not running, and it is not serving any files. If this is your problem, look here:
http://ubuntuguide.org/#windows
```

---

### Post by Alexander Kirillov on 2005-06-01
[QUOTE=n21roadie][HTML]Do I understand you correclty? You want to see shared files which are in Windows folders on this pc - when loggged in to Ubuntu *on this computer*? But obviously, when you are logged in Ubuntu, Windows is not running, and it is not serving any files. If this is your problem, look here:
[http://ubuntuguide.org/#windows](http://ubuntuguide.org/#windows)[/HTML] 

Yes , i want to see windows files when i am logged into ubuntu , same hard drive ( Scsi ) different partition , but more important is the Ide drive (ntfs) attached to this pc , which has files i want to see, i followed you link to ubuntu guide ,which resulted in "busy" ,when i tried to mount the device ??


~$ sudo fdisk -l

Disk /dev/sda: 9100 MB, 9100032000 bytes
255 heads, 63 sectors/track, 1106 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           3       24066   14  Hidden FAT16 <32M
/dev/sda2   *           4         555     4433940    7  HPFS/NTFS
/dev/sda3             556        1106     4425907+  83  Linux

Disk /dev/sdb: 9105 MB, 9105018880 bytes
255 heads, 63 sectors/track, 1106 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         553     4441941   83  Linux
/dev/sdb2   *         554        1106     4441972+   7  HPFS/NTFS

Disk /dev/hda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4865    39078081    7  HPFS/NTFS

Disk /dev/sdc: 512 MB, 512483328 bytes
16 heads, 63 sectors/track, 993 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1         992      499851+   6  FAT16
james@james:~$ sudo mount /dev/sdb /media/windows/ -t ntfs -o umask=0222
mount: /dev/sdb already mounted or /media/windows/ busy
james@james:~$ sudo mount /dev/sda /media/windows/ -t ntfs -o umask=0222
mount: /dev/sda already mounted or /media/windows/ busy
james@james:~$ sudo mount /dev/hda /media/windows/ -t ntfs -o umask=0222
mount: /dev/hda already mounted or /media/windows/ busy```
Do I understand you correclty? You want to see shared files which are in Windows folders on this pc - when loggged in to Ubuntu *on this computer*? But obviously, when you are logged in Ubuntu, Windows is not running, and it is not serving any files. If this is your problem, look here:
http://ubuntuguide.org/#windows
```[/QUOTE]
 correct command should be 
sudo mount /dev/sda2 /media/windows/ -t ntfs -o umask=0222
Note: /dev/sda2, not /dev/sda

---

### Post by n21roadie on 2005-06-01
```
 correct command should be
sudo mount /dev/sda2 /media/windows/ -t ntfs -o umask=0222
Note: /dev/sda2, not /dev/sda
``` 

Still the same -
```
mount: /dev/sda2 already mounted or /media/windows/ busy
mount: according to mtab, /dev/sda2 is mounted on /media/windows
```

---

### Post by Alexander Kirillov on 2005-06-01
[QUOTE=n21roadie]```
 correct command should be
sudo mount /dev/sda2 /media/windows/ -t ntfs -o umask=0222
Note: /dev/sda2, not /dev/sda
``` 

Still the same -
```
mount: /dev/sda2 already mounted or /media/windows/ busy
mount: according to mtab, /dev/sda2 is mounted on /media/windows
```[/QUOTE]
If so, it means that it si already mounted. Open File manager and go to location /media/windows - can you see Windows files there?

---

### Post by n21roadie on 2005-06-02
```
If so, it means that it si already mounted. Open File manager and go to location /media/windows - can you see Windows files there?
``` 

Ok many thanks ,i can see my scsi drive and it's folders , but i am unable to see any files from ide drive attached 

```
Disk /dev/hda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
``` 

sudo mount /dev/hda /media/windows/ -t ntfs -o umask=0222
mount: /dev/hda already mounted or /media/windows/ busy

---

### Post by Alexander Kirillov on 2005-06-02
[QUOTE=n21roadie]```
If so, it means that it si already mounted. Open File manager and go to location /media/windows - can you see Windows files there?
``` 

Ok many thanks ,i can see my scsi drive and it's folders , but i am unable to see any files from ide drive attached 

```
Disk /dev/hda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
``` 

sudo mount /dev/hda /media/windows/ -t ntfs -o umask=0222
mount: /dev/hda already mounted or /media/windows/ busy[/QUOTE]
Well, obviously if you have mounted /dev/sda2 on /media/windows, you have to moutn /dev/hda on some other directory - say, /media/windows2. 
BTW: shouldn't it be /dev/hda1, not /dev/hda ?

---

### Post by n21roadie on 2005-06-03
```
Well, obviously if you have mounted /dev/sda2 on /media/windows, you have to moutn /dev/hda on some other directory - say, /media/windows2.
BTW: shouldn't it be /dev/hda1, not /dev/hda ?
``` 

Thanks once again , made a different folder folder the ide drive , and now i can see the ide drive with the file browser, 

```
sudo mount /dev/hda1 /media/windowsd/ -t ntfs -o umask=0222
``` 

which leads me into another question - howdo i have this ide drive mounted at bootup ,and preferably on the desktop

---

### Post by Alexander Kirillov on 2005-06-03
[QUOTE=n21roadie]```
Well, obviously if you have mounted /dev/sda2 on /media/windows, you have to moutn /dev/hda on some other directory - say, /media/windows2.
BTW: shouldn't it be /dev/hda1, not /dev/hda ?
``` 

Thanks once again , made a different folder folder the ide drive , and now i can see the ide drive with the file browser, 

```
sudo mount /dev/hda1 /media/windowsd/ -t ntfs -o umask=0222
``` 

which leads me into another question - howdo i have this ide drive mounted at bootup ,and preferably on the desktop[/QUOTE]
 [http://ubuntuguide.org/#windows](http://ubuntuguide.org/#windows)

---

