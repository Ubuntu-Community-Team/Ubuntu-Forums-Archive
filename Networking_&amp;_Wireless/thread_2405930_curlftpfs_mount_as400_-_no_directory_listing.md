---
title: "curlftpfs mount as400 - no directory listing"
date: 2018-11-13
forum: Networking &amp; Wireless
---

### Post by pietrob71 on 2018-11-13
I have a server 18.04 in which I must mount an ftp fs from a remote as400.

Using Filezilla, I can connect and browsing the folders.

Using curlftpfs as
```
curlftpfs user:password@serverIp//remoteFolder /mnt/as400/localFolder
```
it seems that login works correctly, so ip, username and passwd are corrects, but trying to browse the mount point folder I've got this error.
```
ls: reading directory '.': Input/output error
```

Using Gigolo, when I look the mounted fs using Thunar, the folder is empty

using curlftpfs -v -d .....
```

* Couldn't find host xxx.xxx.xxx.xxx in the .netrc file; using defaults
*   Trying xxx.xxx.xxx.xxx...
* TCP_NODELAY set
* Connected to xxx.xxx.xxx.xxx (xxx.xxx.xxx.xxx) port 21 (#0)
< 220-QTCP at AS400.xxxxxx.COM.
< 220 Connection will close if idle more than 5 minutes.
> USER xxxx
< 331 Enter password.
> PASS xxxx
< 230 xxxx logged on.
> PWD
< 257 "QGPL" is current library.
> SYST
* Entry path is 'QGPL'
< 215  OS/400 is the remote operating system. The TCP/IP version is "V7R1M0".
> SITE NAMEFMT 1
< 250  Now using naming format "1".
> PWD
< 257 "/QSYS.LIB/QGPL.LIB" is current library.
* Entry path is '/QSYS.LIB/QGPL.LIB'
> CWD /
* ftp_perform ends with SECONDARY: 0
< 250 "/" is current directory.
> CWD remoteFolder
< 250 "/remoteFolder" is current directory.
* Remembering we are in dir "/remoteFolder/"
* Connection #0 to host xxx.xxx.xxx.xxx left intact
FUSE library version: 2.9.7
nullpath_ok: 0
nopath: 0
utime_omit_ok: 0
unique: 1, opcode: INIT (26), nodeid: 0, insize: 56, pid: 0
INIT: 7.26
flags=0x001ffffb
max_readahead=0x00020000
   INIT: 7.19
   flags=0x00000011
   max_readahead=0x00020000
   max_write=0x00020000
   max_background=0
   congestion_threshold=0
   unique: 1, success, outsize: 40
unique: 2, opcode: ACCESS (34), nodeid: 1, insize: 48, pid: 2018
   unique: 2, error: -38 (Function not implemented), outsize: 16
unique: 3, opcode: LOOKUP (1), nodeid: 1, insize: 47, pid: 2018
LOOKUP /.Trash
getattr /.Trash
* Couldn't find host xxx.xxx.xxx.xxx in the .netrc file; using defaults
* Found bundle for host xxx.xxx.xxx.xxx: 0x556658fbdd30 [serially]
* Re-using existing connection! (#0) with host xxx.xxx.xxx.xxx
* Connected to xxx.xxx.xxx.xxx (xxx.xxx.xxx.xxx) port 21 (#0)
* Request has same path as previous transfer
> PASV
* Connect data stream passively
* ftp_perform ends with SECONDARY: 0
< 227 Entering Passive Mode (xxx,xxx,xxx,xxx,94,71)
*   Trying xxx.xxx.xxx.xxx...
* TCP_NODELAY set
* Connecting to xxx.xxx.xxx.xxx (xxx.xxx.xxx.xxx) port 24135
* Connected to xxx.xxx.xxx.xxx (xxx.xxx.xxx.xxx) port 21 (#0)
> TYPE A
< 200 Representation type is ASCII nonprint.
> LIST -a
< 550  Path does not exist: -a
* RETR response: 550
* Remembering we are in dir "/remoteFolder/"
* Connection #0 to host xxx.xxx.xxx.xxx left intact
ftpfs: operation ftpfs_getattr failed because No such file or directory
   unique: 3, error: -2 (No such file or directory), outsize: 16
unique: 4, opcode: LOOKUP (1), nodeid: 1, insize: 49, pid: 2018
LOOKUP /.Trash-0
getattr /.Trash-0
* Couldn't find host xxx.xxx.xxx.xxx in the .netrc file; using defaults
* Found bundle for host xxx.xxx.xxx.xxx: 0x556658fbdd30 [serially]
* Re-using existing connection! (#0) with host xxx.xxx.xxx.xxx
* Connected to xxx.xxx.xxx.xxx (xxx.xxx.xxx.xxx) port 21 (#0)
* Request has same path as previous transfer
> PASV
* Connect data stream passively
* ftp_perform ends with SECONDARY: 0
< 227 Entering Passive Mode (xxx,xxx,xxx,xxx,248,15)
*   Trying xxx.xxx.xxx.xxx...
* TCP_NODELAY set
* Connecting to xxx.xxx.xxx.xxx (xxx.xxx.xxx.xxx) port 63503
* Connected to xxx.xxx.xxx.xxx (xxx.xxx.xxx.xxx) port 21 (#0)
> LIST -a
< 550  Path does not exist: -a
* RETR response: 550
* Remembering we are in dir "/remoteFolder/"
* Connection #0 to host xxx.xxx.xxx.xxx left intact
ftpfs: operation ftpfs_getattr failed because No such file or directory
   unique: 4, error: -2 (No such file or directory), outsize: 16

```

---

