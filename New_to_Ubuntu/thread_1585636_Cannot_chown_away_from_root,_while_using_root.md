---
title: "Cannot chown away from root, while using root"
date: 2010-09-30
forum: New to Ubuntu
---

### Post by imgod22222 on 2010-09-30
```
sudo chown -R andrew /media/400GB
```
that runs.
immediately after:
```
ls -la /media/400GB
```
**EVERYTHING** is still owned by root.
...what's going on?
Note: I am mounting this on boot with an edited fstab.

EDIT:
Thought I'd post what my terminal spit out.
```
andrew@andrew-desktop:~$ sudo chown -R andrew /media/400GB/
[sudo] password for andrew: 
chown: cannot access `/media/400GB/Music_Folder/Megadeth/MD. 45 - The Craving (Remastered)/AlbumArt_{BF9F61B9-AADC-4697-80C4-08CDECE163B0}_Large.jpg': Value too large for defined data type
chown: cannot access `/media/400GB/Music_Folder/Megadeth/Greatest Hits_ Back to The Start/AlbumArtSmall.jpg': Value too large for defined data type
chown: cannot access `/media/400GB/Music_Folder/Unclassified Music/Douchy Songs/AlbumArt_{5C11E7EA-F0C7-4F65-8BC9-1E9E64921027}_Large.jpg': Value too large for defined data type
andrew@andrew-desktop:~$ ls -la /media/400GB/
total 1810344
drwxrwxrwx  1 root root      32768 2010-09-11 21:36 .
drwxr-xr-x 12 root root       4096 2010-09-29 14:39 ..
drwxrwxrwx  1 root root       4096 2007-08-12 18:00 1GB SD CARD (E)
-rwxrwxrwx  2 root root   41725952 2007-06-08 14:55 BoBoBo Theme Song.mpg
drwxrwxrwx  1 root root      32768 2008-06-21 12:07 CS Source Maps
drwxrwxrwx  1 root root       4096 2008-06-21 12:06 Deathklok Metaloclypse season 1 [BKD]
-rwxrwxrwx  2 root root       1434 2007-02-19 19:06 DivX Author – Create DivX Movies.lnk
-rwxrwxrwx  2 root root       1318 2007-02-19 19:06 DivX.com.lnk
drwxrwxrwx  1 root root      12288 2010-04-03 16:22 Dtella Dl's
-rwxrwxrwx  2 root root   38511295 2006-10-30 21:40 FINAL ANTIGONE.wmv
drwxrwxrwx  1 root root       4096 2009-07-28 00:05 FLCL
-rwxrwxrwx  1 root root       1110 2007-11-07 07:00 globdata.ini
-rwxrwxrwx  2 root root     858813 2006-10-07 11:42 Heat_Miser.wma
-rwxrwxrwx  2 root root   24798269 2006-10-07 11:31 HeatMiser.wmv
-rwxrwxrwx  2 root root      16931 2009-08-08 12:30 importing into itunes.odt
-rwxrwxrwx  1 root root     855040 2007-11-07 07:44 install.exe
-rwxrwxrwx  1 root root        843 2007-11-07 07:00 install.ini
-rwxrwxrwx  2 root root      75280 2007-11-07 07:44 install.res.1028.dll
-rwxrwxrwx  2 root root      95248 2007-11-07 07:44 install.res.1031.dll
-rwxrwxrwx  2 root root      90128 2007-11-07 07:44 install.res.1033.dll
-rwxrwxrwx  2 root root      96272 2007-11-07 07:44 install.res.1036.dll
-rwxrwxrwx  2 root root      94224 2007-11-07 07:44 install.res.1040.dll
-rwxrwxrwx  2 root root      80400 2007-11-07 07:44 install.res.1041.dll
-rwxrwxrwx  2 root root      78864 2007-11-07 07:44 install.res.1042.dll
-rwxrwxrwx  2 root root      74768 2007-11-07 07:44 install.res.2052.dll
-rwxrwxrwx  2 root root      95248 2007-11-07 07:44 install.res.3082.dll
drwxrwxrwx  1 root root      49152 2010-09-25 17:21 Music_Folder
drwxrwxrwx  1 root root      12288 2010-08-22 15:35 Network Accesible Folder
drwxrwxrwx  1 root root       8192 2010-09-19 07:18 Panasonic Lumix Lz2
-rwxrwxrwx  2 root root   38761917 2007-08-16 20:37 [PM]Pokemon_Nintendo_Battle_Revolution_Strategy_Guide[8558700C].pdf
drwxrwxrwx  1 root root          0 2008-10-19 16:40 Prototype This
-rwxrwxrwx  2 root root      52224 2007-03-11 23:51 Quigley Time-Line Project.doc
drwxrwxrwx  1 root root       4096 2008-01-02 13:26 RecoveryBin
drwxrwxrwx  1 root root       4096 2010-08-22 14:14 $RECYCLE.BIN
drwxrwxrwx  1 root root       4096 2009-09-28 21:17 RECYCLER
drwxrwxrwx  1 root root       4096 2007-08-13 02:15 Red vs. Blue
-rwxrwxrwx  2 root root    3891620 2006-11-07 21:48 Ricky Martin - Livin' La Vida Loca.mp3
drwxrwxrwx  1 root root       4096 2007-08-14 11:42 south park
-rwxrwxrwx  2 root root       1360 2007-02-19 19:06 Stage6 – Download Free DivX Videos.lnk
drwxrwxrwx  1 root root       4096 2009-02-22 09:37 System Volume Information
drwxrwxrwx  1 root root       4096 2009-08-26 11:12 To burn
drwxrwxrwx  1 root root          0 2010-09-11 21:36 .Trash-1000
drwxrwxrwx  1 root root       4096 2009-08-07 21:58 Unclassified Music
-rwxrwxrwx  1 root root    1927956 2007-11-07 07:50 VC_RED.cab
-rwxrwxrwx  1 root root       5686 2007-11-07 07:00 vcredist.bmp
-rwxrwxrwx  1 root root     242176 2007-11-07 07:53 VC_RED.MSI
-rwxrwxrwx  1 root root  395941888 2009-05-25 17:43 Win2K.iso
-rwxrwxrwx  2 root root 1348288512 2007-01-10 04:31 ZeldaOoT_SS_457.avi

```

---

### Post by sisco311 on 2010-09-30
Please post the relevant fstab entry.

---

### Post by GlazedDonut on 2010-09-30
What filesystem is it using? if its NTFS or FAT32, then there are no permissions to be changed in the first place.

---

### Post by imgod22222 on 2010-09-30
Its NTFS. I want to share (use smbd) and smbd gives me an error saying i need to change smb.conf. Did that, and now smbd is angry and not working.

Additionally, things like EASYtag like to complain "Oh, well, the current user doesn't have permissions so (spit out error messages)."

Any ideas for a remedy (that excludes formatting my drive?)

---

### Post by CharlesA on 2010-09-30
Change this in smb.conf:
```
security = user
```

```
security = share
```

See if that works.

---

