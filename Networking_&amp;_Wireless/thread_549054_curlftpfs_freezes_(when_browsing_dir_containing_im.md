---
title: "curlftpfs freezes (when browsing dir containing images?)"
date: 2007-09-12
forum: Networking &amp; Wireless
---

### Post by Rene7705 on 2007-09-12
Hi. I'm trying to connect from 7.04-desktop to an FTPS server using curlftpfs -o ciphers=TLSv1.
I can connect, but after a viewing a few directories it stalls completely. curlftpfs has to be kill -9ed for nautilus and other apps to work again.

I've turned on debugging, and that tells me that when i open a mounted directory that contains images in nautilus, curlftpfs attempts to dnload that image straight away (and then freezes).
Below is a large sample of browsing first a directory containing only other dirs, then browsing a dir that contains images aswell.
I'm not sure that this directory-contains-images is what causes the freeze, but it is consistent behaviour.

Found a bugreport for [curlftpfs on ubuntu]("https://bugs.launchpad.net/ubuntu/+source/curlftpfs/+bug/120018"), but it doesnt tell me much..

I'm new to ubuntu, so i'm wondering if there's another package that can mount FTPS (TLSv1 is the only crypto my hoster supports) reliably. Or possibly i'm just not using curlftpfs correctly... Any tips are greatly appreciated...

```

rene@goose:~$ cat connect_to_somehoster.sh 
#!
rm somehoster.net.log
sudo umount /home/rene/LIVE_WEBSITES_MOUNTED/somehoster.net/
sudo chmod 777 /dev/fuse
curlftpfs -d -v -o debug,ciphers=TLSv1,user=userA:correctpw ftp.somehoster.net /home/rene/LIVE_WEBSITES_MOUNTED/somehoster.net/ 

rene@goose:~$ ./connect_to_somehoster.sh 
rm: cannot remove `somehoster.net.log': No such file or directory
* Couldn't find host ftp.somehoster.net in the .netrc file, using defaults
* About to connect() to ftp.somehoster.net port 21
*   Trying 77.232.67.28... * connected
* Connected to ftp.somehoster.net (77.232.67.28) port 21
< 220 somehoster.net FTP Server #3
> USER userA
< 331 Password required for userA.
> PASS correctpw
< 230 User userA logged in.
> PWD
< 257 "/" is current directory.
* Entry path is '/'
* Connection #0 to host ftp.somehoster.net left intact
unique: 1, opcode: INIT (26), nodeid: 0, insize: 56
INIT: 7.8
flags=0x00000003
max_readahead=0x00020000
   INIT: 7.8
   flags=0x00000000
   max_readahead=0x00020000
   max_write=0x00020000
   unique: 1, error: 0 (Success), outsize: 40
unique: 2, opcode: GETATTR (3), nodeid: 1, insize: 40
* Couldn't find host ftp.somehoster.net in the .netrc file, using defaults
* Re-using existing connection! (#0) with host ftp.somehoster.net
* Connected to ftp.somehoster.net (77.232.67.28) port 21
> CWD /
< 250 CWD command successful
> EPSV
* Connect data stream passively
< 229 Entering Extended Passive Mode (|||61559|)
*   Trying 77.232.67.28... * connected
* Connecting to 77.232.67.28 (77.232.67.28) port 61559
> TYPE A
< 200 Type set to A
> LIST -a
< 150 Opening ASCII mode data connection for file list
< 226 Transfer complete.
* Connection #0 to host ftp.somehoster.net left intact
   unique: 2, error: 0 (Success), outsize: 112
unique: 3, opcode: ACCESS (34), nodeid: 1, insize: 48
ACCESS / 04
   unique: 3, error: -38 (Function not implemented), outsize: 16
unique: 4, opcode: LOOKUP (1), nodeid: 1, insize: 53
LOOKUP /iPod_Control
* Couldn't find host ftp.somehoster.net in the .netrc file, using defaults
* Re-using existing connection! (#0) with host ftp.somehoster.net
* Connected to ftp.somehoster.net (77.232.67.28) port 21
> CWD /
unique: 5, opcode: GETATTR (3), nodeid: 1, insize: 40
   unique: 5, error: 0 (Success), outsize: 112
unique: 6, opcode: OPENDIR (27), nodeid: 1, insize: 48
   unique: 6, error: 0 (Success), outsize: 32
unique: 7, opcode: GETATTR (3), nodeid: 1, insize: 40
   unique: 7, error: 0 (Success), outsize: 112
< 250 CWD command successful
> EPSV
* Connect data stream passively
< 229 Entering Extended Passive Mode (|||53216|)
*   Trying 77.232.67.28... * connected
* Connecting to 77.232.67.28 (77.232.67.28) port 53216
> TYPE A
< 200 Type set to A
> LIST -a
< 150 Opening ASCII mode data connection for file list
< 226 Transfer complete.
* Connection #0 to host ftp.somehoster.net left intact
   unique: 4, error: -2 (No such file or directory), outsize: 16
unique: 8, opcode: LOOKUP (1), nodeid: 1, insize: 57
LOOKUP /.is_audio_player
* Couldn't find host ftp.somehoster.net in the .netrc file, using defaults
* Re-using existing connection! (#0) with host ftp.somehoster.net
* Connected to ftp.somehoster.net (77.232.67.28) port 21
> CWD /
< 250 CWD command successful
> EPSV
* Connect data stream passively
< 229 Entering Extended Passive Mode (|||58011|)
*   Trying 77.232.67.28... * connected
* Connecting to 77.232.67.28 (77.232.67.28) port 58011
> TYPE A
< 200 Type set to A
> LIST -a
< 150 Opening ASCII mode data connection for file list
< 226 Transfer complete.
* Connection #0 to host ftp.somehoster.net left intact
   unique: 8, error: -2 (No such file or directory), outsize: 16
unique: 9, opcode: LOOKUP (1), nodeid: 1, insize: 48
LOOKUP /.hidden
* Couldn't find host ftp.somehoster.net in the .netrc file, using defaults
* Re-using existing connection! (#0) with host ftp.somehoster.net
* Connected to ftp.somehoster.net (77.232.67.28) port 21
> CWD /
< 250 CWD command successful
> EPSV
* Connect data stream passively
< 229 Entering Extended Passive Mode (|||54956|)
*   Trying 77.232.67.28... * connected
* Connecting to 77.232.67.28 (77.232.67.28) port 54956
> TYPE A
< 200 Type set to A
> LIST -a
< 150 Opening ASCII mode data connection for file list
< 226 Transfer complete.
* Connection #0 to host ftp.somehoster.net left intact
   unique: 9, error: -2 (No such file or directory), outsize: 16
unique: 10, opcode: GETATTR (3), nodeid: 1, insize: 40
   unique: 10, error: 0 (Success), outsize: 112
unique: 11, opcode: OPENDIR (27), nodeid: 1, insize: 48
   unique: 11, error: 0 (Success), outsize: 32
unique: 12, opcode: GETATTR (3), nodeid: 1, insize: 40
   unique: 12, error: 0 (Success), outsize: 112
unique: 13, opcode: READDIR (28), nodeid: 1, insize: 64
* Couldn't find host ftp.somehoster.net in the .netrc file, using defaults
* Re-using existing connection! (#0) with host ftp.somehoster.net
* Connected to ftp.somehoster.net (77.232.67.28) port 21
> CWD /
< 250 CWD command successful
> EPSV
* Connect data stream passively
< 229 Entering Extended Passive Mode (|||60193|)
*   Trying 77.232.67.28... * connected
* Connecting to 77.232.67.28 (77.232.67.28) port 60193
> TYPE A
< 200 Type set to A
> LIST -a
< 150 Opening ASCII mode data connection for file list
< 226 Transfer complete.
* Connection #0 to host ftp.somehoster.net left intact
   unique: 13, error: 0 (Success), outsize: 744
unique: 14, opcode: GETATTR (3), nodeid: 1, insize: 40
   unique: 14, error: 0 (Success), outsize: 112
unique: 15, opcode: LOOKUP (1), nodeid: 1, insize: 44
LOOKUP /inp
   NODEID: 2
   unique: 15, error: 0 (Success), outsize: 136
unique: 16, opcode: READDIR (28), nodeid: 1, insize: 64
   unique: 16, error: 0 (Success), outsize: 744
unique: 17, opcode: READDIR (28), nodeid: 1, insize: 64
   unique: 17, error: 0 (Success), outsize: 16
unique: 18, opcode: RELEASEDIR (29), nodeid: 1, insize: 64
   unique: 18, error: 0 (Success), outsize: 16
unique: 19, opcode: OPEN (14), nodeid: 2, insize: 48
* Couldn't find host ftp.somehoster.net in the .netrc file, using defaults
* Re-using existing connection! (#0) with host ftp.somehoster.net
* Connected to ftp.somehoster.net (77.232.67.28) port 21
> CWD /
unique: 20, opcode: STATFS (17), nodeid: 1, insize: 40
   unique: 20, error: 0 (Success), outsize: 96
unique: 21, opcode: GETATTR (3), nodeid: 1, insize: 40
   unique: 21, error: 0 (Success), outsize: 112
unique: 22, opcode: GETATTR (3), nodeid: 1, insize: 40
   unique: 22, error: 0 (Success), outsize: 112
< 250 CWD command successful
> EPSV
* Connect data stream passively
< 229 Entering Extended Passive Mode (|||49697|)
* Expire at 1189582640 / 262870 (300000ms)
*   Trying 77.232.67.28... * Connecting to 77.232.67.28 (77.232.67.28) port 49697
> TYPE I
< 200 Type set to I
> SIZE inp
< 213 15060
> RETR inp
< 150 Opening BINARY mode data connection for inp (15060 bytes)
* Getting file with size: 15060
OPEN[134830680] flags: 0x8000
   unique: 19, error: 0 (Success), outsize: 32
unique: 23, opcode: READ (15), nodeid: 2, insize: 64
READ[134830680] 16384 bytes from 0
* Expire cleared
< 226 Transfer complete.
* Connection #0 to host ftp.somehoster.net left intact
   READ[134830680] 15060 bytes
   unique: 23, error: 0 (Success), outsize: 15076
unique: 24, opcode: FLUSH (25), nodeid: 2, insize: 64
FLUSH[134830680]
   unique: 24, error: 0 (Success), outsize: 16
unique: 25, opcode: RELEASE (18), nodeid: 2, insize: 64
RELEASE[134830680] flags: 0x8000
   unique: 25, error: 0 (Success), outsize: 16
unique: 26, opcode: LOOKUP (1), nodeid: 1, insize: 50
LOOKUP /mb_upload
   NODEID: 3
   unique: 26, error: 0 (Success), outsize: 136
unique: 27, opcode: LOOKUP (1), nodeid: 1, insize: 56
LOOKUP /something-0.7.3
   NODEID: 4
   unique: 27, error: 0 (Success), outsize: 136
unique: 28, opcode: LOOKUP (1), nodeid: 1, insize: 56
LOOKUP /something-0.7.5
   NODEID: 5
   unique: 28, error: 0 (Success), outsize: 136
unique: 29, opcode: LOOKUP (1), nodeid: 1, insize: 54
LOOKUP /something-0.8
   NODEID: 6
   unique: 29, error: 0 (Success), outsize: 136
unique: 30, opcode: LOOKUP (1), nodeid: 1, insize: 54
LOOKUP /something-0.9
   NODEID: 7
   unique: 30, error: 0 (Success), outsize: 136
unique: 31, opcode: LOOKUP (1), nodeid: 1, insize: 54
LOOKUP /something-1.0
   NODEID: 8
   unique: 31, error: 0 (Success), outsize: 136
unique: 32, opcode: LOOKUP (1), nodeid: 1, insize: 65
LOOKUP /something-3rdp-libraries
   NODEID: 9
   unique: 32, error: 0 (Success), outsize: 136
unique: 33, opcode: LOOKUP (1), nodeid: 1, insize: 59
LOOKUP /something-graphics
   NODEID: 10
   unique: 33, error: 0 (Success), outsize: 136
unique: 34, opcode: LOOKUP (1), nodeid: 1, insize: 64
LOOKUP /something-themes-0.7.5p
   NODEID: 11
   unique: 34, error: 0 (Success), outsize: 136
unique: 35, opcode: LOOKUP (1), nodeid: 1, insize: 62
LOOKUP /something-themes-0.9p
   NODEID: 12
   unique: 35, error: 0 (Success), outsize: 136
unique: 36, opcode: LOOKUP (1), nodeid: 1, insize: 61
LOOKUP /something-themes-1.0
   NODEID: 13
   unique: 36, error: 0 (Success), outsize: 136
unique: 37, opcode: LOOKUP (1), nodeid: 1, insize: 51
LOOKUP /server.php
   NODEID: 14
   unique: 37, error: 0 (Success), outsize: 136
unique: 38, opcode: LOOKUP (1), nodeid: 1, insize: 62
LOOKUP /speaktheunspoken.info
   NODEID: 15
   unique: 38, error: 0 (Success), outsize: 136
unique: 39, opcode: LOOKUP (1), nodeid: 1, insize: 43
LOOKUP /uu
   NODEID: 16
   unique: 39, error: 0 (Success), outsize: 136
unique: 40, opcode: LOOKUP (1), nodeid: 1, insize: 44
LOOKUP /www
   NODEID: 17
   unique: 40, error: 0 (Success), outsize: 136
unique: 41, opcode: READDIR (28), nodeid: 1, insize: 64
   unique: 41, error: 0 (Success), outsize: 16
unique: 42, opcode: RELEASEDIR (29), nodeid: 1, insize: 64
   unique: 42, error: 0 (Success), outsize: 16
unique: 43, opcode: OPENDIR (27), nodeid: 3, insize: 48
   unique: 43, error: 0 (Success), outsize: 32
unique: 44, opcode: READDIR (28), nodeid: 3, insize: 64
* Couldn't find host ftp.somehoster.net in the .netrc file, using defaults
* Re-using existing connection! (#0) with host ftp.somehoster.net
* Connected to ftp.somehoster.net (77.232.67.28) port 21
> CWD /
< 250 CWD command successful
> CWD mb_upload
< 250 CWD command successful
> EPSV
unique: 45, opcode: STATFS (17), nodeid: 1, insize: 40
   unique: 45, error: 0 (Success), outsize: 96
* Connect data stream passively
unique: 46, opcode: GETATTR (3), nodeid: 1, insize: 40
   unique: 46, error: 0 (Success), outsize: 112
unique: 47, opcode: GETATTR (3), nodeid: 1, insize: 40
   unique: 47, error: 0 (Success), outsize: 112
< 229 Entering Extended Passive Mode (|||59169|)
*   Trying 77.232.67.28... * connected
* Connecting to 77.232.67.28 (77.232.67.28) port 59169
> TYPE A
< 200 Type set to A
> LIST -a
< 150 Opening ASCII mode data connection for file list
* Remembering we are in dir mb_upload/
< 226 Transfer complete.
* Connection #0 to host ftp.somehoster.net left intact
   unique: 44, error: 0 (Success), outsize: 80
unique: 48, opcode: READDIR (28), nodeid: 3, insize: 64
   unique: 48, error: 0 (Success), outsize: 16
unique: 49, opcode: RELEASEDIR (29), nodeid: 3, insize: 64
   unique: 49, error: 0 (Success), outsize: 16
unique: 50, opcode: STATFS (17), nodeid: 1, insize: 40
   unique: 50, error: 0 (Success), outsize: 96
unique: 51, opcode: OPENDIR (27), nodeid: 4, insize: 48
   unique: 51, error: 0 (Success), outsize: 32
unique: 52, opcode: GETATTR (3), nodeid: 1, insize: 40
   unique: 52, error: 0 (Success), outsize: 112
unique: 53, opcode: READDIR (28), nodeid: 4, insize: 64
* Couldn't find host ftp.somehoster.net in the .netrc file, using defaults
* Re-using existing connection! (#0) with host ftp.somehoster.net
* Connected to ftp.somehoster.net (77.232.67.28) port 21
> CWD /
unique: 54, opcode: GETATTR (3), nodeid: 1, insize: 40
   unique: 54, error: 0 (Success), outsize: 112
< 250 CWD command successful
> CWD something-0.7.3
< 250 CWD command successful
> EPSV
* Connect data stream passively
< 229 Entering Extended Passive Mode (|||63972|)
*   Trying 77.232.67.28... * connected
* Connecting to 77.232.67.28 (77.232.67.28) port 63972
> TYPE A
< 200 Type set to A
> LIST -a
< 150 Opening ASCII mode data connection for file list
* Remembering we are in dir something-0.7.3/
< 226 Transfer complete.
* Connection #0 to host ftp.somehoster.net left intact
   unique: 53, error: 0 (Success), outsize: 120
unique: 55, opcode: READDIR (28), nodeid: 4, insize: 64
   unique: 55, error: 0 (Success), outsize: 16
unique: 56, opcode: RELEASEDIR (29), nodeid: 4, insize: 64
   unique: 56, error: 0 (Success), outsize: 16
unique: 57, opcode: STATFS (17), nodeid: 1, insize: 40
   unique: 57, error: 0 (Success), outsize: 96
unique: 58, opcode: OPENDIR (27), nodeid: 5, insize: 48
   unique: 58, error: 0 (Success), outsize: 32
unique: 59, opcode: GETATTR (3), nodeid: 1, insize: 40
   unique: 59, error: 0 (Success), outsize: 112
unique: 60, opcode: READDIR (28), nodeid: 5, insize: 64
* Couldn't find host ftp.somehoster.net in the .netrc file, using defaults
* Re-using existing connection! (#0) with host ftp.somehoster.net
* Connected to ftp.somehoster.net (77.232.67.28) port 21
> CWD /
unique: 61, opcode: GETATTR (3), nodeid: 1, insize: 40
   unique: 61, error: 0 (Success), outsize: 112
< 250 CWD command successful
> CWD something-0.7.5
< 250 CWD command successful
> EPSV
* Connect data stream passively
< 229 Entering Extended Passive Mode (|||56141|)
*   Trying 77.232.67.28... * connected
* Connecting to 77.232.67.28 (77.232.67.28) port 56141
> TYPE A
< 200 Type set to A
> LIST -a
< 150 Opening ASCII mode data connection for file list
* Remembering we are in dir something-0.7.5/
< 226 Transfer complete.
* Connection #0 to host ftp.somehoster.net left intact
   unique: 60, error: 0 (Success), outsize: 784
unique: 62, opcode: READDIR (28), nodeid: 5, insize: 64
   unique: 62, error: 0 (Success), outsize: 16
unique: 63, opcode: RELEASEDIR (29), nodeid: 5, insize: 64
   unique: 63, error: 0 (Success), outsize: 16
unique: 64, opcode: STATFS (17), nodeid: 1, insize: 40
   unique: 64, error: 0 (Success), outsize: 96
unique: 65, opcode: OPENDIR (27), nodeid: 6, insize: 48
   unique: 65, error: 0 (Success), outsize: 32
unique: 66, opcode: GETATTR (3), nodeid: 1, insize: 40
   unique: 66, error: 0 (Success), outsize: 112
unique: 67, opcode: READDIR (28), nodeid: 6, insize: 64
* Couldn't find host ftp.somehoster.net in the .netrc file, using defaults
* Re-using existing connection! (#0) with host ftp.somehoster.net
* Connected to ftp.somehoster.net (77.232.67.28) port 21
> CWD /
unique: 68, opcode: GETATTR (3), nodeid: 1, insize: 40
   unique: 68, error: 0 (Success), outsize: 112
< 250 CWD command successful
> CWD something-0.8
< 250 CWD command successful
> EPSV
* Connect data stream passively
< 229 Entering Extended Passive Mode (|||63627|)
*   Trying 77.232.67.28... * connected
* Connecting to 77.232.67.28 (77.232.67.28) port 63627
> TYPE A
< 200 Type set to A
> LIST -a
< 150 Opening ASCII mode data connection for file list
* Remembering we are in dir something-0.8/
< 226 Transfer complete.
* Connection #0 to host ftp.somehoster.net left intact
   unique: 67, error: 0 (Success), outsize: 1136
unique: 69, opcode: READDIR (28), nodeid: 6, insize: 64
   unique: 69, error: 0 (Success), outsize: 16
unique: 70, opcode: RELEASEDIR (29), nodeid: 6, insize: 64
   unique: 70, error: 0 (Success), outsize: 16
unique: 71, opcode: STATFS (17), nodeid: 1, insize: 40
   unique: 71, error: 0 (Success), outsize: 96
unique: 72, opcode: OPENDIR (27), nodeid: 7, insize: 48
   unique: 72, error: 0 (Success), outsize: 32
unique: 73, opcode: GETATTR (3), nodeid: 1, insize: 40
   unique: 73, error: 0 (Success), outsize: 112
unique: 74, opcode: READDIR (28), nodeid: 7, insize: 64
* Couldn't find host ftp.somehoster.net in the .netrc file, using defaults
* Re-using existing connection! (#0) with host ftp.somehoster.net
* Connected to ftp.somehoster.net (77.232.67.28) port 21
> CWD /
unique: 75, opcode: GETATTR (3), nodeid: 1, insize: 40
   unique: 75, error: 0 (Success), outsize: 112
< 250 CWD command successful
> CWD something-0.9
< 250 CWD command successful
> EPSV
* Connect data stream passively
< 229 Entering Extended Passive Mode (|||56908|)
*   Trying 77.232.67.28... * connected
* Connecting to 77.232.67.28 (77.232.67.28) port 56908
> TYPE A
< 200 Type set to A
> LIST -a
< 150 Opening ASCII mode data connection for file list
* Remembering we are in dir something-0.9/
< 226 Transfer complete.
* Connection #0 to host ftp.somehoster.net left intact
   unique: 74, error: 0 (Success), outsize: 840
unique: 76, opcode: READDIR (28), nodeid: 7, insize: 64
   unique: 76, error: 0 (Success), outsize: 16
unique: 77, opcode: RELEASEDIR (29), nodeid: 7, insize: 64
   unique: 77, error: 0 (Success), outsize: 16
unique: 78, opcode: STATFS (17), nodeid: 1, insize: 40
   unique: 78, error: 0 (Success), outsize: 96
unique: 79, opcode: LOOKUP (1), nodeid: 1, insize: 54
LOOKUP /something-1.0
   NODEID: 8
   unique: 79, error: 0 (Success), outsize: 136
unique: 80, opcode: GETATTR (3), nodeid: 1, insize: 40
   unique: 80, error: 0 (Success), outsize: 112
unique: 81, opcode: OPENDIR (27), nodeid: 8, insize: 48
   unique: 81, error: 0 (Success), outsize: 32
unique: 82, opcode: GETATTR (3), nodeid: 1, insize: 40
   unique: 82, error: 0 (Success), outsize: 112
unique: 83, opcode: READDIR (28), nodeid: 8, insize: 64
* Couldn't find host ftp.somehoster.net in the .netrc file, using defaults
* Re-using existing connection! (#0) with host ftp.somehoster.net
* Connected to ftp.somehoster.net (77.232.67.28) port 21
> CWD /
< 250 CWD command successful
> CWD something-1.0
< 250 CWD command successful
> EPSV
* Connect data stream passively
< 229 Entering Extended Passive Mode (|||55496|)
*   Trying 77.232.67.28... * connected
* Connecting to 77.232.67.28 (77.232.67.28) port 55496
> TYPE A
< 200 Type set to A
> LIST -a
< 150 Opening ASCII mode data connection for file list
* Remembering we are in dir something-1.0/
< 226 Transfer complete.
* Connection #0 to host ftp.somehoster.net left intact
   unique: 83, error: 0 (Success), outsize: 776
unique: 84, opcode: READDIR (28), nodeid: 8, insize: 64
   unique: 84, error: 0 (Success), outsize: 16
unique: 85, opcode: RELEASEDIR (29), nodeid: 8, insize: 64
   unique: 85, error: 0 (Success), outsize: 16
unique: 86, opcode: STATFS (17), nodeid: 1, insize: 40
   unique: 86, error: 0 (Success), outsize: 96
unique: 87, opcode: LOOKUP (1), nodeid: 1, insize: 65
LOOKUP /something-3rdp-libraries
   NODEID: 9
   unique: 87, error: 0 (Success), outsize: 136
unique: 88, opcode: GETATTR (3), nodeid: 1, insize: 40
   unique: 88, error: 0 (Success), outsize: 112
unique: 89, opcode: OPENDIR (27), nodeid: 9, insize: 48
   unique: 89, error: 0 (Success), outsize: 32
unique: 90, opcode: GETATTR (3), nodeid: 1, insize: 40
   unique: 90, error: 0 (Success), outsize: 112
unique: 91, opcode: READDIR (28), nodeid: 9, insize: 64
* Couldn't find host ftp.somehoster.net in the .netrc file, using defaults
* Re-using existing connection! (#0) with host ftp.somehoster.net
* Connected to ftp.somehoster.net (77.232.67.28) port 21
> CWD /
< 250 CWD command successful
> CWD something-3rdp-libraries
< 250 CWD command successful
> EPSV
* Connect data stream passively
< 229 Entering Extended Passive Mode (|||56079|)
*   Trying 77.232.67.28... * connected
* Connecting to 77.232.67.28 (77.232.67.28) port 56079
> TYPE A
< 200 Type set to A
> LIST -a
< 150 Opening ASCII mode data connection for file list
* Remembering we are in dir something-3rdp-libraries/
< 226 Transfer complete.
* Connection #0 to host ftp.somehoster.net left intact
   unique: 91, error: 0 (Success), outsize: 544
unique: 92, opcode: READDIR (28), nodeid: 9, insize: 64
   unique: 92, error: 0 (Success), outsize: 16
unique: 93, opcode: RELEASEDIR (29), nodeid: 9, insize: 64
   unique: 93, error: 0 (Success), outsize: 16
unique: 94, opcode: STATFS (17), nodeid: 1, insize: 40
   unique: 94, error: 0 (Success), outsize: 96
unique: 95, opcode: LOOKUP (1), nodeid: 1, insize: 59
LOOKUP /something-graphics
   NODEID: 10
   unique: 95, error: 0 (Success), outsize: 136
unique: 96, opcode: GETATTR (3), nodeid: 1, insize: 40
   unique: 96, error: 0 (Success), outsize: 112
unique: 97, opcode: OPENDIR (27), nodeid: 10, insize: 48
   unique: 97, error: 0 (Success), outsize: 32
unique: 98, opcode: GETATTR (3), nodeid: 1, insize: 40
   unique: 98, error: 0 (Success), outsize: 112
unique: 99, opcode: READDIR (28), nodeid: 10, insize: 64
* Couldn't find host ftp.somehoster.net in the .netrc file, using defaults
* Re-using existing connection! (#0) with host ftp.somehoster.net
* Connected to ftp.somehoster.net (77.232.67.28) port 21
> CWD /
< 250 CWD command successful
> CWD something-graphics
< 250 CWD command successful
> EPSV
* Connect data stream passively
< 229 Entering Extended Passive Mode (|||51817|)
*   Trying 77.232.67.28... * connected
* Connecting to 77.232.67.28 (77.232.67.28) port 51817
> TYPE A
< 200 Type set to A
> LIST -a
< 150 Opening ASCII mode data connection for file list
* Remembering we are in dir something-graphics/
< 226 Transfer complete.
* Connection #0 to host ftp.somehoster.net left intact
   unique: 99, error: 0 (Success), outsize: 296
unique: 100, opcode: READDIR (28), nodeid: 10, insize: 64
   unique: 100, error: 0 (Success), outsize: 16
unique: 101, opcode: RELEASEDIR (29), nodeid: 10, insize: 64
   unique: 101, error: 0 (Success), outsize: 16
unique: 102, opcode: STATFS (17), nodeid: 1, insize: 40
   unique: 102, error: 0 (Success), outsize: 96
unique: 103, opcode: LOOKUP (1), nodeid: 1, insize: 64
LOOKUP /something-themes-0.7.5p
   NODEID: 11
   unique: 103, error: 0 (Success), outsize: 136
unique: 104, opcode: GETATTR (3), nodeid: 1, insize: 40
   unique: 104, error: 0 (Success), outsize: 112
unique: 105, opcode: OPENDIR (27), nodeid: 11, insize: 48
   unique: 105, error: 0 (Success), outsize: 32
unique: 106, opcode: GETATTR (3), nodeid: 1, insize: 40
   unique: 106, error: 0 (Success), outsize: 112
unique: 107, opcode: READDIR (28), nodeid: 11, insize: 64
* Couldn't find host ftp.somehoster.net in the .netrc file, using defaults
* Re-using existing connection! (#0) with host ftp.somehoster.net
* Connected to ftp.somehoster.net (77.232.67.28) port 21
> CWD /
< 250 CWD command successful
> CWD something-themes-0.7.5p
< 250 CWD command successful
> EPSV
* Connect data stream passively
< 229 Entering Extended Passive Mode (|||56779|)
*   Trying 77.232.67.28... * connected
* Connecting to 77.232.67.28 (77.232.67.28) port 56779
> TYPE A
< 200 Type set to A
> LIST -a
< 150 Opening ASCII mode data connection for file list
* Remembering we are in dir something-themes-0.7.5p/
< 226 Transfer complete.
* Connection #0 to host ftp.somehoster.net left intact
   unique: 107, error: 0 (Success), outsize: 256
unique: 108, opcode: READDIR (28), nodeid: 11, insize: 64
   unique: 108, error: 0 (Success), outsize: 16
unique: 109, opcode: RELEASEDIR (29), nodeid: 11, insize: 64
   unique: 109, error: 0 (Success), outsize: 16
unique: 110, opcode: STATFS (17), nodeid: 1, insize: 40
   unique: 110, error: 0 (Success), outsize: 96
unique: 111, opcode: LOOKUP (1), nodeid: 1, insize: 62
LOOKUP /something-themes-0.9p
   NODEID: 12
   unique: 111, error: 0 (Success), outsize: 136
unique: 112, opcode: GETATTR (3), nodeid: 1, insize: 40
   unique: 112, error: 0 (Success), outsize: 112
unique: 113, opcode: OPENDIR (27), nodeid: 12, insize: 48
   unique: 113, error: 0 (Success), outsize: 32
unique: 114, opcode: GETATTR (3), nodeid: 1, insize: 40
   unique: 114, error: 0 (Success), outsize: 112
unique: 115, opcode: READDIR (28), nodeid: 12, insize: 64
* Couldn't find host ftp.somehoster.net in the .netrc file, using defaults
* Re-using existing connection! (#0) with host ftp.somehoster.net
* Connected to ftp.somehoster.net (77.232.67.28) port 21
> CWD /
< 250 CWD command successful
> CWD something-themes-0.9p
< 250 CWD command successful
> EPSV
* Connect data stream passively
< 229 Entering Extended Passive Mode (|||59927|)
*   Trying 77.232.67.28... * connected
* Connecting to 77.232.67.28 (77.232.67.28) port 59927
> TYPE A
< 200 Type set to A
> LIST -a
< 150 Opening ASCII mode data connection for file list
* Remembering we are in dir something-themes-0.9p/
< 226 Transfer complete.
* Connection #0 to host ftp.somehoster.net left intact
   unique: 115, error: 0 (Success), outsize: 384
unique: 116, opcode: READDIR (28), nodeid: 12, insize: 64
   unique: 116, error: 0 (Success), outsize: 16
unique: 117, opcode: RELEASEDIR (29), nodeid: 12, insize: 64
   unique: 117, error: 0 (Success), outsize: 16
unique: 118, opcode: STATFS (17), nodeid: 1, insize: 40
   unique: 118, error: 0 (Success), outsize: 96
unique: 119, opcode: LOOKUP (1), nodeid: 1, insize: 61
LOOKUP /something-themes-1.0
   NODEID: 13
   unique: 119, error: 0 (Success), outsize: 136
unique: 120, opcode: GETATTR (3), nodeid: 1, insize: 40
   unique: 120, error: 0 (Success), outsize: 112
unique: 121, opcode: OPENDIR (27), nodeid: 13, insize: 48
   unique: 121, error: 0 (Success), outsize: 32
unique: 122, opcode: GETATTR (3), nodeid: 1, insize: 40
   unique: 122, error: 0 (Success), outsize: 112
unique: 123, opcode: READDIR (28), nodeid: 13, insize: 64
* Couldn't find host ftp.somehoster.net in the .netrc file, using defaults
* Re-using existing connection! (#0) with host ftp.somehoster.net
* Connected to ftp.somehoster.net (77.232.67.28) port 21
> CWD /
< 250 CWD command successful
> CWD something-themes-1.0
< 250 CWD command successful
> EPSV
* Connect data stream passively
< 229 Entering Extended Passive Mode (|||56321|)
*   Trying 77.232.67.28... * connected
* Connecting to 77.232.67.28 (77.232.67.28) port 56321
> TYPE A
< 200 Type set to A
> LIST -a
< 150 Opening ASCII mode data connection for file list
* Remembering we are in dir something-themes-1.0/
< 226 Transfer complete.
* Connection #0 to host ftp.somehoster.net left intact
   unique: 123, error: 0 (Success), outsize: 80
unique: 124, opcode: READDIR (28), nodeid: 13, insize: 64
   unique: 124, error: 0 (Success), outsize: 16
unique: 125, opcode: RELEASEDIR (29), nodeid: 13, insize: 64
   unique: 125, error: 0 (Success), outsize: 16
unique: 126, opcode: STATFS (17), nodeid: 1, insize: 40
   unique: 126, error: 0 (Success), outsize: 96
unique: 127, opcode: LOOKUP (1), nodeid: 1, insize: 62
LOOKUP /speaktheunspoken.info
   NODEID: 15
   unique: 127, error: 0 (Success), outsize: 136
unique: 128, opcode: GETATTR (3), nodeid: 1, insize: 40
   unique: 128, error: 0 (Success), outsize: 112
unique: 129, opcode: OPENDIR (27), nodeid: 15, insize: 48
   unique: 129, error: 0 (Success), outsize: 32
unique: 130, opcode: GETATTR (3), nodeid: 1, insize: 40
   unique: 130, error: 0 (Success), outsize: 112
unique: 131, opcode: READDIR (28), nodeid: 15, insize: 64
* Couldn't find host ftp.somehoster.net in the .netrc file, using defaults
* Re-using existing connection! (#0) with host ftp.somehoster.net
* Connected to ftp.somehoster.net (77.232.67.28) port 21
> CWD /
< 250 CWD command successful
> CWD speaktheunspoken.info
< 250 CWD command successful
> EPSV
* Connect data stream passively
< 229 Entering Extended Passive Mode (|||59872|)
*   Trying 77.232.67.28... * connected
* Connecting to 77.232.67.28 (77.232.67.28) port 59872
> TYPE A
< 200 Type set to A
> LIST -a
< 150 Opening ASCII mode data connection for file list
* Remembering we are in dir speaktheunspoken.info/
< 226 Transfer complete.
* Connection #0 to host ftp.somehoster.net left intact
   unique: 131, error: 0 (Success), outsize: 120
unique: 132, opcode: READDIR (28), nodeid: 15, insize: 64
   unique: 132, error: 0 (Success), outsize: 16
unique: 133, opcode: RELEASEDIR (29), nodeid: 15, insize: 64
   unique: 133, error: 0 (Success), outsize: 16
unique: 134, opcode: STATFS (17), nodeid: 1, insize: 40
   unique: 134, error: 0 (Success), outsize: 96
unique: 135, opcode: LOOKUP (1), nodeid: 1, insize: 43
LOOKUP /uu
   NODEID: 16
   unique: 135, error: 0 (Success), outsize: 136
unique: 136, opcode: GETATTR (3), nodeid: 1, insize: 40
   unique: 136, error: 0 (Success), outsize: 112
unique: 137, opcode: OPENDIR (27), nodeid: 16, insize: 48
   unique: 137, error: 0 (Success), outsize: 32
unique: 138, opcode: GETATTR (3), nodeid: 1, insize: 40
   unique: 138, error: 0 (Success), outsize: 112
unique: 139, opcode: READDIR (28), nodeid: 16, insize: 64
* Couldn't find host ftp.somehoster.net in the .netrc file, using defaults
* Re-using existing connection! (#0) with host ftp.somehoster.net
* Connected to ftp.somehoster.net (77.232.67.28) port 21
> CWD /
< 250 CWD command successful
> CWD uu
< 250 CWD command successful
> EPSV
* Connect data stream passively
< 229 Entering Extended Passive Mode (|||59358|)
*   Trying 77.232.67.28... * connected
* Connecting to 77.232.67.28 (77.232.67.28) port 59358
> TYPE A
< 200 Type set to A
> LIST -a
< 150 Opening ASCII mode data connection for file list
* Remembering we are in dir uu/
< 226 Transfer complete.
* Connection #0 to host ftp.somehoster.net left intact
   unique: 139, error: 0 (Success), outsize: 976
unique: 140, opcode: READDIR (28), nodeid: 16, insize: 64
   unique: 140, error: 0 (Success), outsize: 16
unique: 141, opcode: RELEASEDIR (29), nodeid: 16, insize: 64
   unique: 141, error: 0 (Success), outsize: 16
unique: 142, opcode: STATFS (17), nodeid: 1, insize: 40
   unique: 142, error: 0 (Success), outsize: 96
unique: 143, opcode: LOOKUP (1), nodeid: 1, insize: 44
LOOKUP /www
   NODEID: 17
   unique: 143, error: 0 (Success), outsize: 136
unique: 144, opcode: GETATTR (3), nodeid: 1, insize: 40
   unique: 144, error: 0 (Success), outsize: 112
unique: 145, opcode: OPENDIR (27), nodeid: 17, insize: 48
   unique: 145, error: 0 (Success), outsize: 32
unique: 146, opcode: GETATTR (3), nodeid: 1, insize: 40
   unique: 146, error: 0 (Success), outsize: 112
unique: 147, opcode: READDIR (28), nodeid: 17, insize: 64
* Couldn't find host ftp.somehoster.net in the .netrc file, using defaults
* Re-using existing connection! (#0) with host ftp.somehoster.net
* Connected to ftp.somehoster.net (77.232.67.28) port 21
> CWD /
< 250 CWD command successful
> CWD www
< 250 CWD command successful
> EPSV
* Connect data stream passively
< 229 Entering Extended Passive Mode (|||56379|)
*   Trying 77.232.67.28... * connected
* Connecting to 77.232.67.28 (77.232.67.28) port 56379
> TYPE A
< 200 Type set to A
> LIST -a
< 150 Opening ASCII mode data connection for file list
* Remembering we are in dir www/
< 226 Transfer complete.
* Connection #0 to host ftp.somehoster.net left intact
   unique: 147, error: 0 (Success), outsize: 768
unique: 148, opcode: READDIR (28), nodeid: 17, insize: 64
   unique: 148, error: 0 (Success), outsize: 16
unique: 149, opcode: RELEASEDIR (29), nodeid: 17, insize: 64
   unique: 149, error: 0 (Success), outsize: 16
unique: 150, opcode: STATFS (17), nodeid: 1, insize: 40
   unique: 150, error: 0 (Success), outsize: 96
unique: 151, opcode: LOOKUP (1), nodeid: 1, insize: 44
LOOKUP /inp
   NODEID: 2
   unique: 151, error: 0 (Success), outsize: 136
unique: 152, opcode: GETATTR (3), nodeid: 1, insize: 40
   unique: 152, error: 0 (Success), outsize: 112
unique: 153, opcode: OPEN (14), nodeid: 2, insize: 48
* Couldn't find host ftp.somehoster.net in the .netrc file, using defaults
* Re-using existing connection! (#0) with host ftp.somehoster.net
* Connected to ftp.somehoster.net (77.232.67.28) port 21
> CWD /
unique: 154, opcode: GETATTR (3), nodeid: 1, insize: 40
   unique: 154, error: 0 (Success), outsize: 112
< 250 CWD command successful
> EPSV
* Connect data stream passively
< 229 Entering Extended Passive Mode (|||55554|)
* Expire at 1189582643 / 323798 (300000ms)
*   Trying 77.232.67.28... * Connecting to 77.232.67.28 (77.232.67.28) port 55554
> TYPE I
< 200 Type set to I
> SIZE inp
< 213 15060
> RETR inp
< 150 Opening BINARY mode data connection for inp (15060 bytes)
* Getting file with size: 15060
OPEN[134880104] flags: 0x8000
   unique: 153, error: 0 (Success), outsize: 32
unique: 155, opcode: READ (15), nodeid: 2, insize: 64
READ[134880104] 16384 bytes from 0
* Expire cleared
< 226 Transfer complete.
* Connection #0 to host ftp.somehoster.net left intact
   READ[134880104] 15060 bytes
   unique: 155, error: 0 (Success), outsize: 15076
unique: 156, opcode: LOOKUP (1), nodeid: 1, insize: 50
LOOKUP /mb_upload
   NODEID: 3
   unique: 156, error: 0 (Success), outsize: 136
unique: 157, opcode: FLUSH (25), nodeid: 2, insize: 64
FLUSH[134880104]
   unique: 157, error: 0 (Success), outsize: 16
unique: 158, opcode: GETATTR (3), nodeid: 1, insize: 40
   unique: 158, error: 0 (Success), outsize: 112
unique: 159, opcode: RELEASE (18), nodeid: 2, insize: 64
RELEASE[134880104] flags: 0x8000
   unique: 159, error: 0 (Success), outsize: 16
unique: 160, opcode: LOOKUP (1), nodeid: 1, insize: 56
LOOKUP /something-0.7.3
   NODEID: 4
   unique: 160, error: 0 (Success), outsize: 136
unique: 161, opcode: LOOKUP (1), nodeid: 1, insize: 56
LOOKUP /something-0.7.5
   NODEID: 5
   unique: 161, error: 0 (Success), outsize: 136
unique: 162, opcode: LOOKUP (1), nodeid: 1, insize: 54
LOOKUP /something-0.8
   NODEID: 6
   unique: 162, error: 0 (Success), outsize: 136
unique: 163, opcode: LOOKUP (1), nodeid: 1, insize: 54
LOOKUP /something-0.9
   NODEID: 7
   unique: 163, error: 0 (Success), outsize: 136
unique: 164, opcode: LOOKUP (1), nodeid: 1, insize: 54
LOOKUP /something-1.0
   NODEID: 8
   unique: 164, error: 0 (Success), outsize: 136
unique: 165, opcode: LOOKUP (1), nodeid: 1, insize: 65
LOOKUP /something-3rdp-libraries
   NODEID: 9
   unique: 165, error: 0 (Success), outsize: 136
unique: 166, opcode: LOOKUP (1), nodeid: 1, insize: 59
LOOKUP /something-graphics
   NODEID: 10
   unique: 166, error: 0 (Success), outsize: 136
unique: 167, opcode: LOOKUP (1), nodeid: 1, insize: 64
LOOKUP /something-themes-0.7.5p
   NODEID: 11
   unique: 167, error: 0 (Success), outsize: 136
unique: 168, opcode: LOOKUP (1), nodeid: 1, insize: 62
LOOKUP /something-themes-0.9p
   NODEID: 12
   unique: 168, error: 0 (Success), outsize: 136
unique: 169, opcode: LOOKUP (1), nodeid: 1, insize: 61
LOOKUP /something-themes-1.0
   NODEID: 13
   unique: 169, error: 0 (Success), outsize: 136
unique: 170, opcode: GETATTR (3), nodeid: 15, insize: 40
   unique: 170, error: 0 (Success), outsize: 112
unique: 171, opcode: GETATTR (3), nodeid: 16, insize: 40
   unique: 171, error: 0 (Success), outsize: 112
unique: 172, opcode: GETATTR (3), nodeid: 17, insize: 40
   unique: 172, error: 0 (Success), outsize: 112
unique: 173, opcode: STATFS (17), nodeid: 1, insize: 40
   unique: 173, error: 0 (Success), outsize: 96
unique: 174, opcode: GETATTR (3), nodeid: 1, insize: 40
   unique: 174, error: 0 (Success), outsize: 112
unique: 175, opcode: GETATTR (3), nodeid: 1, insize: 40
   unique: 175, error: 0 (Success), outsize: 112
unique: 176, opcode: LOOKUP (1), nodeid: 1, insize: 54
LOOKUP /something-0.9
   NODEID: 7
   unique: 176, error: 0 (Success), outsize: 136
unique: 177, opcode: GETATTR (3), nodeid: 1, insize: 40
   unique: 177, error: 0 (Success), outsize: 112
unique: 178, opcode: GETATTR (3), nodeid: 1, insize: 40
   unique: 178, error: 0 (Success), outsize: 112
unique: 179, opcode: LOOKUP (1), nodeid: 7, insize: 48
LOOKUP /something-0.9/.hidden
* Couldn't find host ftp.somehoster.net in the .netrc file, using defaults
* Re-using existing connection! (#0) with host ftp.somehoster.net
* Connected to ftp.somehoster.net (77.232.67.28) port 21
> CWD /
< 250 CWD command successful
> CWD something-0.9
< 250 CWD command successful
> EPSV
* Connect data stream passively
< 229 Entering Extended Passive Mode (|||56880|)
*   Trying 77.232.67.28... * connected
* Connecting to 77.232.67.28 (77.232.67.28) port 56880
> TYPE A
< 200 Type set to A
> LIST -a
< 150 Opening ASCII mode data connection for file list
* Remembering we are in dir something-0.9/
< 226 Transfer complete.
* Connection #0 to host ftp.somehoster.net left intact
   unique: 179, error: -2 (No such file or directory), outsize: 16
unique: 180, opcode: OPENDIR (27), nodeid: 7, insize: 48
   unique: 180, error: 0 (Success), outsize: 32
unique: 181, opcode: READDIR (28), nodeid: 7, insize: 64
   unique: 181, error: 0 (Success), outsize: 840
unique: 182, opcode: GETATTR (3), nodeid: 7, insize: 40
   unique: 182, error: 0 (Success), outsize: 112
unique: 183, opcode: GETATTR (3), nodeid: 1, insize: 40
   unique: 183, error: 0 (Success), outsize: 112
unique: 184, opcode: LOOKUP (1), nodeid: 7, insize: 50
LOOKUP /something-0.9/.htaccess
   NODEID: 18
   unique: 184, error: 0 (Success), outsize: 136
unique: 185, opcode: OPEN (14), nodeid: 18, insize: 48
* Couldn't find host ftp.somehoster.net in the .netrc file, using defaults
* Re-using existing connection! (#0) with host ftp.somehoster.net
* Connected to ftp.somehoster.net (77.232.67.28) port 21
* Request has same path as previous transfer
> EPSV
* Connect data stream passively
< 229 Entering Extended Passive Mode (|||53042|)
* Expire at 1189582652 / 409756 (300000ms)
*   Trying 77.232.67.28... * Connecting to 77.232.67.28 (77.232.67.28) port 53042
> TYPE I
< 200 Type set to I
> SIZE .htaccess
< 213 255
> RETR .htaccess
< 150 Opening BINARY mode data connection for .htaccess (255 bytes)
* Getting file with size: 255
OPEN[134667480] flags: 0x8000
   unique: 185, error: 0 (Success), outsize: 32
unique: 186, opcode: READ (15), nodeid: 18, insize: 64
READ[134667480] 4096 bytes from 0
* Expire cleared
* Remembering we are in dir something-0.9/
< 226 Transfer complete.
* Connection #0 to host ftp.somehoster.net left intact
   READ[134667480] 255 bytes
   unique: 186, error: 0 (Success), outsize: 271
unique: 187, opcode: FLUSH (25), nodeid: 18, insize: 64
FLUSH[134667480]
   unique: 187, error: 0 (Success), outsize: 16
unique: 188, opcode: RELEASE (18), nodeid: 18, insize: 64
RELEASE[134667480] flags: 0x8000
unique: 189, opcode: LOOKUP (1), nodeid: 7, insize: 50
LOOKUP /something-0.9/Thumbs.db
   NODEID: 19
   unique: 189, error: 0 (Success), outsize: 136
   unique: 188, error: 0 (Success), outsize: 16
unique: 190, opcode: OPEN (14), nodeid: 19, insize: 48
* Couldn't find host ftp.somehoster.net in the .netrc file, using defaults
* Re-using existing connection! (#0) with host ftp.somehoster.net
* Connected to ftp.somehoster.net (77.232.67.28) port 21
* Request has same path as previous transfer
> EPSV
* Connect data stream passively
< 229 Entering Extended Passive Mode (|||55662|)
* Expire at 1189582652 / 564527 (300000ms)
*   Trying 77.232.67.28... * Connecting to 77.232.67.28 (77.232.67.28) port 55662
> TYPE I
< 200 Type set to I
> SIZE Thumbs.db
< 213 10240
> RETR Thumbs.db
< 150 Opening BINARY mode data connection for Thumbs.db (10240 bytes)
* Getting file with size: 10240
OPEN[134667480] flags: 0x8000
   unique: 190, error: 0 (Success), outsize: 32
unique: 191, opcode: READ (15), nodeid: 19, insize: 64
READ[134667480] 12288 bytes from 0
* Expire cleared
* Remembering we are in dir something-0.9/
< 226 Transfer complete.
* Connection #0 to host ftp.somehoster.net left intact
   READ[134667480] 10240 bytes
   unique: 191, error: 0 (Success), outsize: 10256
unique: 192, opcode: FLUSH (25), nodeid: 19, insize: 64
FLUSH[134667480]
   unique: 192, error: 0 (Success), outsize: 16
unique: 193, opcode: RELEASE (18), nodeid: 19, insize: 64
RELEASE[134667480] flags: 0x8000
   unique: 193, error: 0 (Success), outsize: 16
unique: 194, opcode: LOOKUP (1), nodeid: 7, insize: 56
LOOKUP /something-0.9/ajax_wizard.php
   NODEID: 20
   unique: 194, error: 0 (Success), outsize: 136
unique: 195, opcode: LOOKUP (1), nodeid: 7, insize: 44
LOOKUP /something-0.9/art
   NODEID: 21
   unique: 195, error: 0 (Success), outsize: 136
unique: 196, opcode: READLINK (5), nodeid: 21, insize: 40
   unique: 196, error: 0 (Success), outsize: 37
unique: 197, opcode: LOOKUP (1), nodeid: 1, insize: 59
LOOKUP /something-graphics
   NODEID: 10
   unique: 197, error: 0 (Success), outsize: 136
unique: 198, opcode: READLINK (5), nodeid: 21, insize: 40
   unique: 198, error: 0 (Success), outsize: 37
unique: 199, opcode: READLINK (5), nodeid: 21, insize: 40
   unique: 199, error: 0 (Success), outsize: 37
unique: 200, opcode: READLINK (5), nodeid: 21, insize: 40
   unique: 200, error: 0 (Success), outsize: 37
unique: 201, opcode: LOOKUP (1), nodeid: 7, insize: 46
LOOKUP /something-0.9/cache
   NODEID: 22
   unique: 201, error: 0 (Success), outsize: 136
unique: 202, opcode: LOOKUP (1), nodeid: 7, insize: 47
LOOKUP /something-0.9/config
   NODEID: 23
   unique: 202, error: 0 (Success), outsize: 136
unique: 203, opcode: LOOKUP (1), nodeid: 7, insize: 56
LOOKUP /something-0.9/copyrighted.txt
   NODEID: 24
   unique: 203, error: 0 (Success), outsize: 136
unique: 204, opcode: LOOKUP (1), nodeid: 7, insize: 52
LOOKUP /something-0.9/favicon.ico
   NODEID: 25
   unique: 204, error: 0 (Success), outsize: 136
unique: 205, opcode: LOOKUP (1), nodeid: 7, insize: 50
LOOKUP /something-0.9/index.php
   NODEID: 26
   unique: 205, error: 0 (Success), outsize: 136
unique: 206, opcode: LOOKUP (1), nodeid: 7, insize: 48
LOOKUP /something-0.9/install
   NODEID: 27
   unique: 206, error: 0 (Success), outsize: 136
unique: 207, opcode: LOOKUP (1), nodeid: 7, insize: 43
LOOKUP /something-0.9/js
   NODEID: 28
   unique: 207, error: 0 (Success), outsize: 136
unique: 208, opcode: LOOKUP (1), nodeid: 7, insize: 44
LOOKUP /something-0.9/lib
   NODEID: 29
   unique: 208, error: 0 (Success), outsize: 136
unique: 209, opcode: LOOKUP (1), nodeid: 7, insize: 53
LOOKUP /something-0.9/localization
   NODEID: 30
   unique: 209, error: 0 (Success), outsize: 136
unique: 210, opcode: LOOKUP (1), nodeid: 7, insize: 54
LOOKUP /something-0.9/something.css
   NODEID: 31
   unique: 210, error: 0 (Success), outsize: 136
unique: 211, opcode: LOOKUP (1), nodeid: 7, insize: 44
LOOKUP /something-0.9/php
   NODEID: 32
   unique: 211, error: 0 (Success), outsize: 136
unique: 212, opcode: LOOKUP (1), nodeid: 7, insize: 47
LOOKUP /something-0.9/pi.php
   NODEID: 33
   unique: 212, error: 0 (Success), outsize: 136
unique: 213, opcode: LOOKUP (1), nodeid: 7, insize: 46
LOOKUP /something-0.9/tasks
   NODEID: 34
   unique: 213, error: 0 (Success), outsize: 136
unique: 214, opcode: LOOKUP (1), nodeid: 7, insize: 46
LOOKUP /something-0.9/theme
   NODEID: 35
   unique: 214, error: 0 (Success), outsize: 136
unique: 215, opcode: READLINK (5), nodeid: 35, insize: 40
   unique: 215, error: 0 (Success), outsize: 40
unique: 216, opcode: LOOKUP (1), nodeid: 1, insize: 62
LOOKUP /something-themes-0.9p
   NODEID: 12
   unique: 216, error: 0 (Success), outsize: 136
unique: 217, opcode: READLINK (5), nodeid: 35, insize: 40
   unique: 217, error: 0 (Success), outsize: 40
unique: 218, opcode: READLINK (5), nodeid: 35, insize: 40
   unique: 218, error: 0 (Success), outsize: 40
unique: 219, opcode: READLINK (5), nodeid: 35, insize: 40
   unique: 219, error: 0 (Success), outsize: 40
unique: 220, opcode: LOOKUP (1), nodeid: 7, insize: 49
LOOKUP /something-0.9/v0.9.txt
   NODEID: 36
   unique: 220, error: 0 (Success), outsize: 136
unique: 221, opcode: LOOKUP (1), nodeid: 7, insize: 51
LOOKUP /something-0.9/wizard.php
   NODEID: 37
   unique: 221, error: 0 (Success), outsize: 136
unique: 222, opcode: LOOKUP (1), nodeid: 7, insize: 59
LOOKUP /something-0.9/wizard_process.php
   NODEID: 38
   unique: 222, error: 0 (Success), outsize: 136
unique: 223, opcode: READDIR (28), nodeid: 7, insize: 64
   unique: 223, error: 0 (Success), outsize: 16
unique: 224, opcode: RELEASEDIR (29), nodeid: 7, insize: 64
   unique: 224, error: 0 (Success), outsize: 16
unique: 225, opcode: READLINK (5), nodeid: 21, insize: 40
   unique: 225, error: 0 (Success), outsize: 37
unique: 226, opcode: OPENDIR (27), nodeid: 10, insize: 48
   unique: 226, error: 0 (Success), outsize: 32
unique: 227, opcode: READDIR (28), nodeid: 10, insize: 64
   unique: 227, error: 0 (Success), outsize: 296
unique: 228, opcode: READDIR (28), nodeid: 10, insize: 64
   unique: 228, error: 0 (Success), outsize: 16
unique: 229, opcode: RELEASEDIR (29), nodeid: 10, insize: 64
   unique: 229, error: 0 (Success), outsize: 16
unique: 230, opcode: OPENDIR (27), nodeid: 22, insize: 48
   unique: 230, error: 0 (Success), outsize: 32
unique: 231, opcode: READDIR (28), nodeid: 22, insize: 64
* Couldn't find host ftp.somehoster.net in the .netrc file, using defaults
* Re-using existing connection! (#0) with host ftp.somehoster.net
* Connected to ftp.somehoster.net (77.232.67.28) port 21
> CWD /
< 250 CWD command successful
> CWD something-0.9
< 250 CWD command successful
> CWD cache
< 250 CWD command successful
> EPSV
* Connect data stream passively
unique: 232, opcode: STATFS (17), nodeid: 7, insize: 40
   unique: 232, error: 0 (Success), outsize: 96
unique: 233, opcode: GETATTR (3), nodeid: 7, insize: 40
   unique: 233, error: 0 (Success), outsize: 112
unique: 234, opcode: GETATTR (3), nodeid: 1, insize: 40
   unique: 234, error: 0 (Success), outsize: 112
< 229 Entering Extended Passive Mode (|||55665|)
*   Trying 77.232.67.28... unique: 235, opcode: OPEN (14), nodeid: 25, insize: 48
* connected
* Connecting to 77.232.67.28 (77.232.67.28) port 55665
> TYPE A
< 200 Type set to A
> LIST -a
< 150 Opening ASCII mode data connection for file list
* Remembering we are in dir something-0.9/cache/
< 226 Transfer complete.
* Connection #0 to host ftp.somehoster.net left intact
* Couldn't find host ftp.somehoster.net in the .netrc file, using defaults
* Re-using existing connection! (#0) with host ftp.somehoster.net
* Connected to ftp.somehoster.net (77.232.67.28) port 21
> CWD /
   unique: 231, error: 0 (Success), outsize: 184
unique: 236, opcode: READDIR (28), nodeid: 22, insize: 64
   unique: 236, error: 0 (Success), outsize: 16
unique: 237, opcode: RELEASEDIR (29), nodeid: 22, insize: 64
   unique: 237, error: 0 (Success), outsize: 16
< 250 CWD command successful
> CWD something-0.9
< 250 CWD command successful
> EPSV
* Connect data stream passively
< 229 Entering Extended Passive Mode (|||65137|)
* Expire at 1189582653 / 433390 (300000ms)
*   Trying 77.232.67.28... * Connecting to 77.232.67.28 (77.232.67.28) port 65137
> TYPE I
< 200 Type set to I
> SIZE favicon.ico
< 213 2238
> RETR favicon.ico
< 150 Opening BINARY mode data connection for favicon.ico (2238 bytes)
* Getting file with size: 2238
OPEN[134867688] flags: 0x8000
   unique: 235, error: 0 (Success), outsize: 32
unique: 238, opcode: READ (15), nodeid: 25, insize: 64
READ[134867688] 4096 bytes from 0
* Expire cleared
* Remembering we are in dir something-0.9/
< 226 Transfer complete.
* Connection #0 to host ftp.somehoster.net left intact
   READ[134867688] 2238 bytes
   unique: 238, error: 0 (Success), outsize: 2254
unique: 239, opcode: FLUSH (25), nodeid: 25, insize: 64
FLUSH[134867688]
   unique: 239, error: 0 (Success), outsize: 16
unique: 240, opcode: RELEASE (18), nodeid: 25, insize: 64
RELEASE[134867688] flags: 0x8000
   unique: 240, error: 0 (Success), outsize: 16
unique: 241, opcode: LOOKUP (1), nodeid: 1, insize: 54
LOOKUP /something-0.9
   NODEID: 7
   unique: 241, error: 0 (Success), outsize: 136
unique: 242, opcode: LOOKUP (1), nodeid: 1, insize: 54
LOOKUP /something-0.9
   NODEID: 7
   unique: 242, error: 0 (Success), outsize: 136
unique: 243, opcode: OPENDIR (27), nodeid: 23, insize: 48
   unique: 243, error: 0 (Success), outsize: 32
unique: 244, opcode: READDIR (28), nodeid: 23, insize: 64
* Couldn't find host ftp.somehoster.net in the .netrc file, using defaults
* Re-using existing connection! (#0) with host ftp.somehoster.net
* Connected to ftp.somehoster.net (77.232.67.28) port 21
> CWD /
unique: 245, opcode: STATFS (17), nodeid: 7, insize: 40
   unique: 245, error: 0 (Success), outsize: 96
unique: 246, opcode: GETATTR (3), nodeid: 1, insize: 40
   unique: 246, error: 0 (Success), outsize: 112
< 250 CWD command successful
> CWD something-0.9
< 250 CWD command successful
> CWD config
< 250 CWD command successful
> EPSV
* Connect data stream passively
< 229 Entering Extended Passive Mode (|||59185|)
*   Trying 77.232.67.28... * connected
* Connecting to 77.232.67.28 (77.232.67.28) port 59185
> TYPE A
< 200 Type set to A
> LIST -a
< 150 Opening ASCII mode data connection for file list
* Remembering we are in dir something-0.9/config/
< 226 Transfer complete.
* Connection #0 to host ftp.somehoster.net left intact
   unique: 244, error: 0 (Success), outsize: 656
unique: 247, opcode: READDIR (28), nodeid: 23, insize: 64
   unique: 247, error: 0 (Success), outsize: 16
unique: 248, opcode: RELEASEDIR (29), nodeid: 23, insize: 64
   unique: 248, error: 0 (Success), outsize: 16
unique: 249, opcode: STATFS (17), nodeid: 7, insize: 40
   unique: 249, error: 0 (Success), outsize: 96
unique: 250, opcode: LOOKUP (1), nodeid: 7, insize: 56
LOOKUP /something-0.9/copyrighted.txt
   NODEID: 24
   unique: 250, error: 0 (Success), outsize: 136
unique: 251, opcode: GETATTR (3), nodeid: 1, insize: 40
   unique: 251, error: 0 (Success), outsize: 112
unique: 252, opcode: OPEN (14), nodeid: 24, insize: 48
* Couldn't find host ftp.somehoster.net in the .netrc file, using defaults
* Re-using existing connection! (#0) with host ftp.somehoster.net
* Connected to ftp.somehoster.net (77.232.67.28) port 21
> CWD /
< 250 CWD command successful
> CWD something-0.9
< 250 CWD command successful
> EPSV
* Connect data stream passively
< 229 Entering Extended Passive Mode (|||54775|)
* Expire at 1189582653 / 851096 (300000ms)
*   Trying 77.232.67.28... * Connecting to 77.232.67.28 (77.232.67.28) port 54775
> TYPE I
< 200 Type set to I
> SIZE copyrighted.txt
< 213 1063
> RETR copyrighted.txt
< 150 Opening BINARY mode data connection for copyrighted.txt (1063 bytes)
* Getting file with size: 1063
OPEN[134887488] flags: 0x8000
   unique: 252, error: 0 (Success), outsize: 32
unique: 253, opcode: READ (15), nodeid: 24, insize: 64
READ[134887488] 4096 bytes from 0
* Expire cleared
* Remembering we are in dir something-0.9/
< 226 Transfer complete.
* Connection #0 to host ftp.somehoster.net left intact
   READ[134887488] 1063 bytes
   unique: 253, error: 0 (Success), outsize: 1079
unique: 254, opcode: STATFS (17), nodeid: 7, insize: 40
   unique: 254, error: 0 (Success), outsize: 96
unique: 255, opcode: FLUSH (25), nodeid: 24, insize: 64
FLUSH[134887488]
   unique: 255, error: 0 (Success), outsize: 16
unique: 256, opcode: GETATTR (3), nodeid: 1, insize: 40
   unique: 256, error: 0 (Success), outsize: 112
unique: 257, opcode: RELEASE (18), nodeid: 24, insize: 64
RELEASE[134887488] flags: 0x8000
   unique: 257, error: 0 (Success), outsize: 16
unique: 258, opcode: LOOKUP (1), nodeid: 7, insize: 48
LOOKUP /something-0.9/install
   NODEID: 27
   unique: 258, error: 0 (Success), outsize: 136
unique: 259, opcode: OPENDIR (27), nodeid: 27, insize: 48
   unique: 259, error: 0 (Success), outsize: 32
unique: 260, opcode: READDIR (28), nodeid: 27, insize: 64
* Couldn't find host ftp.somehoster.net in the .netrc file, using defaults
* Re-using existing connection! (#0) with host ftp.somehoster.net
* Connected to ftp.somehoster.net (77.232.67.28) port 21
> CWD /
< 250 CWD command successful
> CWD something-0.9
< 250 CWD command successful
> CWD install
< 250 CWD command successful
> EPSV
* Connect data stream passively
< 229 Entering Extended Passive Mode (|||61786|)
*   Trying 77.232.67.28... * connected
* Connecting to 77.232.67.28 (77.232.67.28) port 61786
> TYPE A
< 200 Type set to A
> LIST -a
< 150 Opening ASCII mode data connection for file list
* Remembering we are in dir something-0.9/install/
< 226 Transfer complete.
* Connection #0 to host ftp.somehoster.net left intact
   unique: 260, error: 0 (Success), outsize: 536
unique: 261, opcode: READDIR (28), nodeid: 27, insize: 64
   unique: 261, error: 0 (Success), outsize: 16
unique: 262, opcode: RELEASEDIR (29), nodeid: 27, insize: 64
   unique: 262, error: 0 (Success), outsize: 16
unique: 263, opcode: STATFS (17), nodeid: 7, insize: 40
   unique: 263, error: 0 (Success), outsize: 96
unique: 264, opcode: LOOKUP (1), nodeid: 7, insize: 43
LOOKUP /something-0.9/js
   NODEID: 28
   unique: 264, error: 0 (Success), outsize: 136
unique: 265, opcode: GETATTR (3), nodeid: 1, insize: 40
   unique: 265, error: 0 (Success), outsize: 112
unique: 266, opcode: OPENDIR (27), nodeid: 28, insize: 48
   unique: 266, error: 0 (Success), outsize: 32
unique: 267, opcode: READDIR (28), nodeid: 28, insize: 64
* Couldn't find host ftp.somehoster.net in the .netrc file, using defaults
* Re-using existing connection! (#0) with host ftp.somehoster.net
* Connected to ftp.somehoster.net (77.232.67.28) port 21
> CWD /
< 250 CWD command successful
> CWD something-0.9
< 250 CWD command successful
> CWD js
< 250 CWD command successful
> EPSV
* Connect data stream passively
< 229 Entering Extended Passive Mode (|||59525|)
*   Trying 77.232.67.28... * connected
* Connecting to 77.232.67.28 (77.232.67.28) port 59525
> TYPE A
< 200 Type set to A
> LIST -a
< 150 Opening ASCII mode data connection for file list
* Remembering we are in dir something-0.9/js/
< 226 Transfer complete.
* Connection #0 to host ftp.somehoster.net left intact
   unique: 267, error: 0 (Success), outsize: 2000
unique: 268, opcode: READDIR (28), nodeid: 28, insize: 64
   unique: 268, error: 0 (Success), outsize: 16
unique: 269, opcode: RELEASEDIR (29), nodeid: 28, insize: 64
   unique: 269, error: 0 (Success), outsize: 16
unique: 270, opcode: STATFS (17), nodeid: 7, insize: 40
   unique: 270, error: 0 (Success), outsize: 96
unique: 271, opcode: LOOKUP (1), nodeid: 7, insize: 44
LOOKUP /something-0.9/lib
   NODEID: 29
   unique: 271, error: 0 (Success), outsize: 136
unique: 272, opcode: GETATTR (3), nodeid: 1, insize: 40
   unique: 272, error: 0 (Success), outsize: 112
unique: 273, opcode: OPENDIR (27), nodeid: 29, insize: 48
   unique: 273, error: 0 (Success), outsize: 32
unique: 274, opcode: READDIR (28), nodeid: 29, insize: 64
* Couldn't find host ftp.somehoster.net in the .netrc file, using defaults
* Re-using existing connection! (#0) with host ftp.somehoster.net
* Connected to ftp.somehoster.net (77.232.67.28) port 21
> CWD /
< 250 CWD command successful
> CWD something-0.9
< 250 CWD command successful
> CWD lib
< 250 CWD command successful
> EPSV
* Connect data stream passively
< 229 Entering Extended Passive Mode (|||60148|)
*   Trying 77.232.67.28... * connected
* Connecting to 77.232.67.28 (77.232.67.28) port 60148
> TYPE A
< 200 Type set to A
> LIST -a
< 150 Opening ASCII mode data connection for file list
* Remembering we are in dir something-0.9/lib/
< 226 Transfer complete.
* Connection #0 to host ftp.somehoster.net left intact
   unique: 274, error: 0 (Success), outsize: 1400
unique: 275, opcode: READDIR (28), nodeid: 29, insize: 64
   unique: 275, error: 0 (Success), outsize: 16
unique: 276, opcode: RELEASEDIR (29), nodeid: 29, insize: 64
   unique: 276, error: 0 (Success), outsize: 16
unique: 277, opcode: LOOKUP (1), nodeid: 1, insize: 54
LOOKUP /something-0.9
   NODEID: 7
   unique: 277, error: 0 (Success), outsize: 136
unique: 278, opcode: LOOKUP (1), nodeid: 1, insize: 54
LOOKUP /something-0.9
   NODEID: 7
   unique: 278, error: 0 (Success), outsize: 136
unique: 279, opcode: STATFS (17), nodeid: 7, insize: 40
   unique: 279, error: 0 (Success), outsize: 96
unique: 280, opcode: LOOKUP (1), nodeid: 7, insize: 53
LOOKUP /something-0.9/localization
   NODEID: 30
   unique: 280, error: 0 (Success), outsize: 136
unique: 281, opcode: GETATTR (3), nodeid: 1, insize: 40
   unique: 281, error: 0 (Success), outsize: 112
unique: 282, opcode: OPENDIR (27), nodeid: 30, insize: 48
   unique: 282, error: 0 (Success), outsize: 32
unique: 283, opcode: READDIR (28), nodeid: 30, insize: 64
* Couldn't find host ftp.somehoster.net in the .netrc file, using defaults
* Re-using existing connection! (#0) with host ftp.somehoster.net
* Connected to ftp.somehoster.net (77.232.67.28) port 21
> CWD /
< 250 CWD command successful
> CWD something-0.9
< 250 CWD command successful
> CWD localization
< 250 CWD command successful
> EPSV
* Connect data stream passively
< 229 Entering Extended Passive Mode (|||57812|)
*   Trying 77.232.67.28... * connected
* Connecting to 77.232.67.28 (77.232.67.28) port 57812
> TYPE A
< 200 Type set to A
> LIST -a
< 150 Opening ASCII mode data connection for file list
* Remembering we are in dir something-0.9/localization/
< 226 Transfer complete.
* Connection #0 to host ftp.somehoster.net left intact
   unique: 283, error: 0 (Success), outsize: 112
unique: 284, opcode: READDIR (28), nodeid: 30, insize: 64
   unique: 284, error: 0 (Success), outsize: 16
unique: 285, opcode: RELEASEDIR (29), nodeid: 30, insize: 64
   unique: 285, error: 0 (Success), outsize: 16
unique: 286, opcode: STATFS (17), nodeid: 7, insize: 40
   unique: 286, error: 0 (Success), outsize: 96
unique: 287, opcode: LOOKUP (1), nodeid: 7, insize: 54
LOOKUP /something-0.9/something.css
   NODEID: 31
   unique: 287, error: 0 (Success), outsize: 136
unique: 288, opcode: GETATTR (3), nodeid: 1, insize: 40
   unique: 288, error: 0 (Success), outsize: 112
unique: 289, opcode: OPEN (14), nodeid: 31, insize: 48
* Couldn't find host ftp.somehoster.net in the .netrc file, using defaults
* Re-using existing connection! (#0) with host ftp.somehoster.net
* Connected to ftp.somehoster.net (77.232.67.28) port 21
> CWD /
< 250 CWD command successful
> CWD something-0.9
< 250 CWD command successful
> EPSV
* Connect data stream passively
< 229 Entering Extended Passive Mode (|||63589|)
* Expire at 1189582654 / 998683 (300000ms)
*   Trying 77.232.67.28... * Connecting to 77.232.67.28 (77.232.67.28) port 63589
> TYPE I
< 200 Type set to I
> SIZE something.css
< 213 2969
> RETR something.css
< 150 Opening BINARY mode data connection for something.css (2969 bytes)
* Getting file with size: 2969
OPEN[134872104] flags: 0x8000
   unique: 289, error: 0 (Success), outsize: 32
unique: 290, opcode: READ (15), nodeid: 31, insize: 64
READ[134872104] 4096 bytes from 0
* Expire cleared
* Remembering we are in dir something-0.9/
< 226 Transfer complete.
* Connection #0 to host ftp.somehoster.net left intact
   READ[134872104] 2969 bytes
   unique: 290, error: 0 (Success), outsize: 2985
unique: 292, opcode: FLUSH (25), nodeid: 31, insize: 64
FLUSH[134872104]
   unique: 292, error: 0 (Success), outsize: 16
unique: 293, opcode: LOOKUP (1), nodeid: 7, insize: 44
LOOKUP /something-0.9/php
   NODEID: 32
   unique: 293, error: 0 (Success), outsize: 136
unique: 291, opcode: STATFS (17), nodeid: 7, insize: 40
   unique: 291, error: 0 (Success), outsize: 96
unique: 294, opcode: RELEASE (18), nodeid: 31, insize: 64
RELEASE[134872104] flags: 0x8000
   unique: 294, error: 0 (Success), outsize: 16
unique: 295, opcode: OPENDIR (27), nodeid: 32, insize: 48
   unique: 295, error: 0 (Success), outsize: 32
unique: 296, opcode: GETATTR (3), nodeid: 1, insize: 40
   unique: 296, error: 0 (Success), outsize: 112
unique: 297, opcode: READDIR (28), nodeid: 32, insize: 64
* Couldn't find host ftp.somehoster.net in the .netrc file, using defaults
* Re-using existing connection! (#0) with host ftp.somehoster.net
* Connected to ftp.somehoster.net (77.232.67.28) port 21
> CWD /
< 250 CWD command successful
> CWD something-0.9
< 250 CWD command successful
> CWD php
< 250 CWD command successful
> EPSV
* Connect data stream passively
< 229 Entering Extended Passive Mode (|||52625|)
*   Trying 77.232.67.28... * connected
* Connecting to 77.232.67.28 (77.232.67.28) port 52625
> TYPE A
< 200 Type set to A
> LIST -a
< 150 Opening ASCII mode data connection for file list
* Remembering we are in dir something-0.9/php/
< 226 Transfer complete.
* Connection #0 to host ftp.somehoster.net left intact
   unique: 297, error: 0 (Success), outsize: 4112
unique: 298, opcode: READDIR (28), nodeid: 32, insize: 64
   unique: 298, error: 0 (Success), outsize: 3632
unique: 299, opcode: READDIR (28), nodeid: 32, insize: 64
   unique: 299, error: 0 (Success), outsize: 16
unique: 300, opcode: RELEASEDIR (29), nodeid: 32, insize: 64
   unique: 300, error: 0 (Success), outsize: 16
unique: 301, opcode: STATFS (17), nodeid: 7, insize: 40
   unique: 301, error: 0 (Success), outsize: 96
unique: 302, opcode: GETATTR (3), nodeid: 1, insize: 40
   unique: 302, error: 0 (Success), outsize: 112
unique: 303, opcode: LOOKUP (1), nodeid: 7, insize: 46
LOOKUP /something-0.9/tasks
   NODEID: 34
   unique: 303, error: 0 (Success), outsize: 136
unique: 304, opcode: OPENDIR (27), nodeid: 34, insize: 48
   unique: 304, error: 0 (Success), outsize: 32
unique: 305, opcode: READDIR (28), nodeid: 34, insize: 64
* Couldn't find host ftp.somehoster.net in the .netrc file, using defaults
* Re-using existing connection! (#0) with host ftp.somehoster.net
* Connected to ftp.somehoster.net (77.232.67.28) port 21
> CWD /
< 250 CWD command successful
> CWD something-0.9
< 250 CWD command successful
> CWD tasks
< 250 CWD command successful
> EPSV
* Connect data stream passively
< 229 Entering Extended Passive Mode (|||63617|)
*   Trying 77.232.67.28... * connected
* Connecting to 77.232.67.28 (77.232.67.28) port 63617
> TYPE A
< 200 Type set to A
> LIST -a
< 150 Opening ASCII mode data connection for file list
* Remembering we are in dir something-0.9/tasks/
< 226 Transfer complete.
* Connection #0 to host ftp.somehoster.net left intact
   unique: 305, error: 0 (Success), outsize: 176
unique: 306, opcode: READDIR (28), nodeid: 34, insize: 64
   unique: 306, error: 0 (Success), outsize: 16
unique: 307, opcode: RELEASEDIR (29), nodeid: 34, insize: 64
   unique: 307, error: 0 (Success), outsize: 16
unique: 308, opcode: LOOKUP (1), nodeid: 1, insize: 54
LOOKUP /something-0.9
   NODEID: 7
   unique: 308, error: 0 (Success), outsize: 136
unique: 309, opcode: LOOKUP (1), nodeid: 1, insize: 54
LOOKUP /something-0.9
   NODEID: 7
   unique: 309, error: 0 (Success), outsize: 136
unique: 310, opcode: STATFS (17), nodeid: 7, insize: 40
   unique: 310, error: 0 (Success), outsize: 96
unique: 311, opcode: LOOKUP (1), nodeid: 7, insize: 46
LOOKUP /something-0.9/theme
   NODEID: 35
   unique: 311, error: 0 (Success), outsize: 136
unique: 312, opcode: GETATTR (3), nodeid: 1, insize: 40
   unique: 312, error: 0 (Success), outsize: 112
unique: 313, opcode: READLINK (5), nodeid: 35, insize: 40
   unique: 313, error: 0 (Success), outsize: 40
unique: 314, opcode: LOOKUP (1), nodeid: 1, insize: 62
LOOKUP /something-themes-0.9p
   NODEID: 12
   unique: 314, error: 0 (Success), outsize: 136
unique: 315, opcode: OPENDIR (27), nodeid: 12, insize: 48
   unique: 315, error: 0 (Success), outsize: 32
unique: 316, opcode: READDIR (28), nodeid: 12, insize: 64
   unique: 316, error: 0 (Success), outsize: 384
unique: 317, opcode: READDIR (28), nodeid: 12, insize: 64
   unique: 317, error: 0 (Success), outsize: 16
unique: 318, opcode: RELEASEDIR (29), nodeid: 12, insize: 64
   unique: 318, error: 0 (Success), outsize: 16
unique: 319, opcode: STATFS (17), nodeid: 7, insize: 40
   unique: 319, error: 0 (Success), outsize: 96
unique: 320, opcode: LOOKUP (1), nodeid: 7, insize: 49
LOOKUP /something-0.9/v0.9.txt
   NODEID: 36
   unique: 320, error: 0 (Success), outsize: 136
unique: 322, opcode: OPEN (14), nodeid: 36, insize: 48
* Couldn't find host ftp.somehoster.net in the .netrc file, using defaults
* Re-using existing connection! (#0) with host ftp.somehoster.net
* Connected to ftp.somehoster.net (77.232.67.28) port 21
> CWD /
unique: 321, opcode: GETATTR (3), nodeid: 1, insize: 40
   unique: 321, error: 0 (Success), outsize: 112
< 250 CWD command successful
> CWD something-0.9
< 250 CWD command successful
> EPSV
* Connect data stream passively
< 229 Entering Extended Passive Mode (|||58248|)
* Expire at 1189582655 / 821071 (300000ms)
*   Trying 77.232.67.28... * Connecting to 77.232.67.28 (77.232.67.28) port 58248
> TYPE I
< 200 Type set to I
> SIZE v0.9.txt
< 213 0
> RETR v0.9.txt
< 150 Opening BINARY mode data connection for v0.9.txt
* Getting file with size: -1
* Expire cleared
* Remembering we are in dir something-0.9/
< 226 Transfer complete.
* Connection #0 to host ftp.somehoster.net left intact
OPEN[134868896] flags: 0x8000
   unique: 322, error: 0 (Success), outsize: 32
unique: 323, opcode: LOOKUP (1), nodeid: 7, insize: 44
LOOKUP /something-0.9/art
   NODEID: 21
   unique: 323, error: 0 (Success), outsize: 136
unique: 324, opcode: FLUSH (25), nodeid: 36, insize: 64
FLUSH[134868896]
   unique: 324, error: 0 (Success), outsize: 16
unique: 325, opcode: READLINK (5), nodeid: 21, insize: 40
   unique: 325, error: 0 (Success), outsize: 37
unique: 326, opcode: RELEASE (18), nodeid: 36, insize: 64
RELEASE[134868896] flags: 0x8000
   unique: 326, error: 0 (Success), outsize: 16
unique: 327, opcode: LOOKUP (1), nodeid: 1, insize: 59
LOOKUP /something-graphics
   NODEID: 10
   unique: 327, error: 0 (Success), outsize: 136
unique: 328, opcode: LOOKUP (1), nodeid: 7, insize: 46
LOOKUP /something-0.9/cache
   NODEID: 22
   unique: 328, error: 0 (Success), outsize: 136
unique: 329, opcode: LOOKUP (1), nodeid: 7, insize: 47
LOOKUP /something-0.9/config
   NODEID: 23
   unique: 329, error: 0 (Success), outsize: 136
unique: 330, opcode: LOOKUP (1), nodeid: 7, insize: 48
LOOKUP /something-0.9/install
   NODEID: 27
   unique: 330, error: 0 (Success), outsize: 136
unique: 331, opcode: LOOKUP (1), nodeid: 7, insize: 43
LOOKUP /something-0.9/js
   NODEID: 28
   unique: 331, error: 0 (Success), outsize: 136
unique: 332, opcode: LOOKUP (1), nodeid: 7, insize: 44
LOOKUP /something-0.9/lib
   NODEID: 29
   unique: 332, error: 0 (Success), outsize: 136
unique: 333, opcode: LOOKUP (1), nodeid: 7, insize: 53
LOOKUP /something-0.9/localization
   NODEID: 30
   unique: 333, error: 0 (Success), outsize: 136
unique: 334, opcode: GETATTR (3), nodeid: 32, insize: 40
   unique: 334, error: 0 (Success), outsize: 112
unique: 335, opcode: GETATTR (3), nodeid: 34, insize: 40
   unique: 335, error: 0 (Success), outsize: 112
unique: 336, opcode: READLINK (5), nodeid: 35, insize: 40
   unique: 336, error: 0 (Success), outsize: 40
unique: 337, opcode: GETATTR (3), nodeid: 12, insize: 40
   unique: 337, error: 0 (Success), outsize: 112
unique: 338, opcode: STATFS (17), nodeid: 7, insize: 40
   unique: 338, error: 0 (Success), outsize: 96
unique: 339, opcode: GETATTR (3), nodeid: 1, insize: 40
   unique: 339, error: 0 (Success), outsize: 112
unique: 340, opcode: LOOKUP (1), nodeid: 1, insize: 54
LOOKUP /something-0.9
   NODEID: 7
   unique: 340, error: 0 (Success), outsize: 136
unique: 341, opcode: LOOKUP (1), nodeid: 7, insize: 52
LOOKUP /something-0.9/favicon.ico
   NODEID: 25
   unique: 341, error: 0 (Success), outsize: 136
unique: 342, opcode: LOOKUP (1), nodeid: 1, insize: 62
LOOKUP /something-themes-0.9p
   NODEID: 12
   unique: 342, error: 0 (Success), outsize: 136
unique: 343, opcode: LOOKUP (1), nodeid: 12, insize: 48
LOOKUP /something-themes-0.9p/.hidden
* Couldn't find host ftp.somehoster.net in the .netrc file, using defaults
* Re-using existing connection! (#0) with host ftp.somehoster.net
* Connected to ftp.somehoster.net (77.232.67.28) port 21
> CWD /
< 250 CWD command successful
> CWD something-themes-0.9p
< 250 CWD command successful
> EPSV
* Connect data stream passively
< 229 Entering Extended Passive Mode (|||53171|)
*   Trying 77.232.67.28... * connected
* Connecting to 77.232.67.28 (77.232.67.28) port 53171
> TYPE A
< 200 Type set to A
> LIST -a
< 150 Opening ASCII mode data connection for file list
* Remembering we are in dir something-themes-0.9p/
< 226 Transfer complete.
* Connection #0 to host ftp.somehoster.net left intact
   unique: 343, error: -2 (No such file or directory), outsize: 16
unique: 344, opcode: OPENDIR (27), nodeid: 12, insize: 48
   unique: 344, error: 0 (Success), outsize: 32
unique: 345, opcode: READDIR (28), nodeid: 12, insize: 64
   unique: 345, error: 0 (Success), outsize: 384
unique: 346, opcode: GETATTR (3), nodeid: 12, insize: 40
   unique: 346, error: 0 (Success), outsize: 112
unique: 347, opcode: GETATTR (3), nodeid: 1, insize: 40
   unique: 347, error: 0 (Success), outsize: 112
unique: 348, opcode: LOOKUP (1), nodeid: 12, insize: 43
LOOKUP /something-themes-0.9p/PT
   NODEID: 39
   unique: 348, error: 0 (Success), outsize: 136
unique: 349, opcode: LOOKUP (1), nodeid: 12, insize: 75
LOOKUP /something-themes-0.9p/SITE_speakTheUnspoken.info_darkish
   NODEID: 40
   unique: 349, error: 0 (Success), outsize: 136
unique: 350, opcode: LOOKUP (1), nodeid: 12, insize: 70
LOOKUP /something-themes-0.9p/SITE_testsomething.veerman.ws
   NODEID: 41
   unique: 350, error: 0 (Success), outsize: 136
unique: 351, opcode: LOOKUP (1), nodeid: 12, insize: 56
LOOKUP /something-themes-0.9p/darkstarFashion
   NODEID: 42
   unique: 351, error: 0 (Success), outsize: 136
unique: 352, opcode: LOOKUP (1), nodeid: 12, insize: 60
LOOKUP /something-themes-0.9p/something_greyTiles
   NODEID: 43
   unique: 352, error: 0 (Success), outsize: 136
unique: 353, opcode: LOOKUP (1), nodeid: 12, insize: 48
LOOKUP /something-themes-0.9p/modesto
   NODEID: 44
   unique: 353, error: 0 (Success), outsize: 136
unique: 354, opcode: LOOKUP (1), nodeid: 12, insize: 48
LOOKUP /something-themes-0.9p/proBeer
   NODEID: 45
   unique: 354, error: 0 (Success), outsize: 136
unique: 355, opcode: READDIR (28), nodeid: 12, insize: 64
   unique: 355, error: 0 (Success), outsize: 16
unique: 356, opcode: RELEASEDIR (29), nodeid: 12, insize: 64
   unique: 356, error: 0 (Success), outsize: 16
unique: 357, opcode: GETATTR (3), nodeid: 12, insize: 40
   unique: 357, error: 0 (Success), outsize: 112
unique: 358, opcode: LOOKUP (1), nodeid: 1, insize: 54
LOOKUP /something-0.9
   NODEID: 7
   unique: 358, error: 0 (Success), outsize: 136
unique: 359, opcode: STATFS (17), nodeid: 7, insize: 40
   unique: 359, error: 0 (Success), outsize: 96
unique: 360, opcode: GETATTR (3), nodeid: 1, insize: 40
   unique: 360, error: 0 (Success), outsize: 112
unique: 361, opcode: LOOKUP (1), nodeid: 1, insize: 62
LOOKUP /something-themes-0.9p
   NODEID: 12
   unique: 361, error: 0 (Success), outsize: 136
unique: 362, opcode: LOOKUP (1), nodeid: 12, insize: 56
LOOKUP /something-themes-0.9p/darkstarFashion
   NODEID: 42
   unique: 362, error: 0 (Success), outsize: 136
unique: 363, opcode: LOOKUP (1), nodeid: 1, insize: 54
LOOKUP /something-0.9
   NODEID: 7
   unique: 363, error: 0 (Success), outsize: 136
unique: 364, opcode: GETATTR (3), nodeid: 1, insize: 40
   unique: 364, error: 0 (Success), outsize: 112
unique: 365, opcode: LOOKUP (1), nodeid: 42, insize: 48
LOOKUP /something-themes-0.9p/darkstarFashion/.hidden
* Couldn't find host ftp.somehoster.net in the .netrc file, using defaults
* Re-using existing connection! (#0) with host ftp.somehoster.net
* Connected to ftp.somehoster.net (77.232.67.28) port 21
> CWD /
< 250 CWD command successful
> CWD something-themes-0.9p
< 250 CWD command successful
> CWD darkstarFashion
< 250 CWD command successful
> EPSV
* Connect data stream passively
< 229 Entering Extended Passive Mode (|||57252|)
*   Trying 77.232.67.28... * connected
* Connecting to 77.232.67.28 (77.232.67.28) port 57252
> TYPE A
< 200 Type set to A
> LIST -a
< 150 Opening ASCII mode data connection for file list
* Remembering we are in dir something-themes-0.9p/darkstarFashion/
< 226 Transfer complete.
* Connection #0 to host ftp.somehoster.net left intact
   unique: 365, error: -2 (No such file or directory), outsize: 16
unique: 366, opcode: OPENDIR (27), nodeid: 42, insize: 48
   unique: 366, error: 0 (Success), outsize: 32
unique: 367, opcode: READDIR (28), nodeid: 42, insize: 64
* Couldn't find host ftp.somehoster.net in the .netrc file, using defaults
* Re-using existing connection! (#0) with host ftp.somehoster.net
* Connected to ftp.somehoster.net (77.232.67.28) port 21
* Request has same path as previous transfer
> EPSV
* Connect data stream passively
< 229 Entering Extended Passive Mode (|||56687|)
*   Trying 77.232.67.28... * connected
* Connecting to 77.232.67.28 (77.232.67.28) port 56687
> TYPE A
< 200 Type set to A
> LIST -a
< 150 Opening ASCII mode data connection for file list
* Remembering we are in dir something-themes-0.9p/darkstarFashion/
< 226 Transfer complete.
* Connection #0 to host ftp.somehoster.net left intact
   unique: 367, error: 0 (Success), outsize: 736
unique: 368, opcode: GETATTR (3), nodeid: 42, insize: 40
   unique: 368, error: 0 (Success), outsize: 112
unique: 369, opcode: LOOKUP (1), nodeid: 42, insize: 59
LOOKUP /something-themes-0.9p/darkstarFashion/ajax_get_stuff.php
   NODEID: 46
   unique: 369, error: 0 (Success), outsize: 136
unique: 370, opcode: READLINK (5), nodeid: 46, insize: 40
   unique: 370, error: 0 (Success), outsize: 58
unique: 371, opcode: LOOKUP (1), nodeid: 7, insize: 44
LOOKUP /something-0.9/php
   NODEID: 32
   unique: 371, error: 0 (Success), outsize: 136
unique: 372, opcode: LOOKUP (1), nodeid: 32, insize: 59
LOOKUP /something-0.9/php/ajax_get_stuff.php
   NODEID: 47
   unique: 372, error: 0 (Success), outsize: 136
unique: 373, opcode: READLINK (5), nodeid: 46, insize: 40
   unique: 373, error: 0 (Success), outsize: 58
unique: 374, opcode: READLINK (5), nodeid: 46, insize: 40
   unique: 374, error: 0 (Success), outsize: 58
unique: 375, opcode: READLINK (5), nodeid: 46, insize: 40
   unique: 375, error: 0 (Success), outsize: 58
unique: 376, opcode: LOOKUP (1), nodeid: 42, insize: 53
LOOKUP /something-themes-0.9p/darkstarFashion/articles.css
   NODEID: 48
   unique: 376, error: 0 (Success), outsize: 136
unique: 377, opcode: LOOKUP (1), nodeid: 42, insize: 53
LOOKUP /something-themes-0.9p/darkstarFashion/darkstar.png
   NODEID: 49
   unique: 377, error: 0 (Success), outsize: 136
unique: 378, opcode: LOOKUP (1), nodeid: 42, insize: 59
LOOKUP /something-themes-0.9p/darkstarFashion/darkstar_white.gif
   NODEID: 50
   unique: 378, error: 0 (Success), outsize: 136
unique: 379, opcode: LOOKUP (1), nodeid: 42, insize: 59
LOOKUP /something-themes-0.9p/darkstarFashion/darkstar_white.png
   NODEID: 51
   unique: 379, error: 0 (Success), outsize: 136
unique: 380, opcode: LOOKUP (1), nodeid: 42, insize: 65
LOOKUP /something-themes-0.9p/darkstarFashion/editor_articles_css3.css
   NODEID: 52
   unique: 380, error: 0 (Success), outsize: 136
unique: 381, opcode: LOOKUP (1), nodeid: 42, insize: 64
LOOKUP /something-themes-0.9p/darkstarFashion/editor_articles_ie5.css
   NODEID: 53
   unique: 381, error: 0 (Success), outsize: 136
unique: 382, opcode: LOOKUP (1), nodeid: 42, insize: 76
LOOKUP /something-themes-0.9p/darkstarFashion/graph_visitor_log.mbGraph_theme.ini
   NODEID: 54
   unique: 382, error: 0 (Success), outsize: 136
unique: 383, opcode: OPEN (14), nodeid: 54, insize: 48
* Couldn't find host ftp.somehoster.net in the .netrc file, using defaults
* Re-using existing connection! (#0) with host ftp.somehoster.net
* Connected to ftp.somehoster.net (77.232.67.28) port 21
* Request has same path as previous transfer
> EPSV
* Connect data stream passively
< 229 Entering Extended Passive Mode (|||60160|)
* Expire at 1189582662 / 650159 (300000ms)
*   Trying 77.232.67.28... * Connecting to 77.232.67.28 (77.232.67.28) port 60160
> TYPE I
< 200 Type set to I
> SIZE graph_visitor_log.mbGraph_theme.ini
< 213 819
> RETR graph_visitor_log.mbGraph_theme.ini
< 150 Opening BINARY mode data connection for graph_visitor_log.mbGraph_theme.ini (819 bytes)
* Getting file with size: 819
OPEN[134944848] flags: 0x8000
   unique: 383, error: 0 (Success), outsize: 32
unique: 384, opcode: READ (15), nodeid: 54, insize: 64
READ[134944848] 4096 bytes from 0
* Expire cleared
* Remembering we are in dir something-themes-0.9p/darkstarFashion/
< 226 Transfer complete.
* Connection #0 to host ftp.somehoster.net left intact
   READ[134944848] 819 bytes
   unique: 384, error: 0 (Success), outsize: 835
unique: 385, opcode: FLUSH (25), nodeid: 54, insize: 64
FLUSH[134944848]
   unique: 385, error: 0 (Success), outsize: 16
unique: 386, opcode: RELEASE (18), nodeid: 54, insize: 64
RELEASE[134944848] flags: 0x8000
   unique: 386, error: 0 (Success), outsize: 16
unique: 387, opcode: LOOKUP (1), nodeid: 42, insize: 50
LOOKUP /something-themes-0.9p/darkstarFashion/index.php
   NODEID: 55
   unique: 387, error: 0 (Success), outsize: 136
unique: 388, opcode: LOOKUP (1), nodeid: 42, insize: 51
LOOKUP /something-themes-0.9p/darkstarFashion/latest.css
   NODEID: 56
   unique: 388, error: 0 (Success), outsize: 136
unique: 389, opcode: LOOKUP (1), nodeid: 42, insize: 60
LOOKUP /something-themes-0.9p/darkstarFashion/something_theme.css
   NODEID: 57
   unique: 389, error: 0 (Success), outsize: 136
unique: 390, opcode: LOOKUP (1), nodeid: 42, insize: 60
LOOKUP /something-themes-0.9p/darkstarFashion/something_theme.ini
   NODEID: 58
   unique: 390, error: 0 (Success), outsize: 136
unique: 391, opcode: OPEN (14), nodeid: 58, insize: 48
* Couldn't find host ftp.somehoster.net in the .netrc file, using defaults
* Re-using existing connection! (#0) with host ftp.somehoster.net
* Connected to ftp.somehoster.net (77.232.67.28) port 21
* Request has same path as previous transfer
> EPSV
* Connect data stream passively
< 229 Entering Extended Passive Mode (|||55345|)
* Expire at 1189582663 / 42342 (300000ms)
*   Trying 77.232.67.28... * Connecting to 77.232.67.28 (77.232.67.28) port 55345
> TYPE I
< 200 Type set to I
> SIZE something_theme.ini
< 213 156
> RETR something_theme.ini
< 150 Opening BINARY mode data connection for something_theme.ini (156 bytes)
* Getting file with size: 156
OPEN[134944848] flags: 0x8000
   unique: 391, error: 0 (Success), outsize: 32
unique: 392, opcode: READ (15), nodeid: 58, insize: 64
READ[134944848] 4096 bytes from 0
* Expire cleared
* Remembering we are in dir something-themes-0.9p/darkstarFashion/
< 226 Transfer complete.
* Connection #0 to host ftp.somehoster.net left intact
   READ[134944848] 156 bytes
   unique: 392, error: 0 (Success), outsize: 172
unique: 393, opcode: FLUSH (25), nodeid: 58, insize: 64
FLUSH[134944848]
   unique: 393, error: 0 (Success), outsize: 16
unique: 395, opcode: LOOKUP (1), nodeid: 42, insize: 65
LOOKUP /something-themes-0.9p/darkstarFashion/something_theme_css3.css
   NODEID: 59
   unique: 395, error: 0 (Success), outsize: 136
unique: 394, opcode: RELEASE (18), nodeid: 58, insize: 64
RELEASE[134944848] flags: 0x8000
   unique: 394, error: 0 (Success), outsize: 16
unique: 396, opcode: LOOKUP (1), nodeid: 42, insize: 64
LOOKUP /something-themes-0.9p/darkstarFashion/something_theme_ie5.css
   NODEID: 60
   unique: 396, error: 0 (Success), outsize: 136
unique: 397, opcode: READDIR (28), nodeid: 42, insize: 64
   unique: 397, error: 0 (Success), outsize: 16
unique: 398, opcode: RELEASEDIR (29), nodeid: 42, insize: 64
   unique: 398, error: 0 (Success), outsize: 16
unique: 400, opcode: LOOKUP (1), nodeid: 1, insize: 62
unique: 399, opcode: LOOKUP (1), nodeid: 1, insize: 62
LOOKUP /something-themes-0.9p
   NODEID: 12
   unique: 399, error: 0 (Success), outsize: 136
LOOKUP /something-themes-0.9p
   NODEID: 12
   unique: 400, error: 0 (Success), outsize: 136
unique: 401, opcode: LOOKUP (1), nodeid: 12, insize: 56
LOOKUP /something-themes-0.9p/darkstarFashion
   NODEID: 42
   unique: 401, error: 0 (Success), outsize: 136
unique: 402, opcode: OPEN (14), nodeid: 48, insize: 48
unique: 403, opcode: OPEN (14), nodeid: 49, insize: 48
* Couldn't find host ftp.somehoster.net in the .netrc file, using defaults
* Re-using existing connection! (#0) with host ftp.somehoster.net
* Connected to ftp.somehoster.net (77.232.67.28) port 21
* Request has same path as previous transfer
> EPSV
* Connect data stream passively
< 229 Entering Extended Passive Mode (|||64444|)
* Expire at 1189582663 / 294390 (300000ms)
*   Trying 77.232.67.28... * Connecting to 77.232.67.28 (77.232.67.28) port 64444
> TYPE I
< 200 Type set to I
> SIZE articles.css
< 213 1129
> RETR articles.css
< 150 Opening BINARY mode data connection for articles.css (1129 bytes)
* Getting file with size: 1129
OPEN[134944848] flags: 0x8000
   unique: 402, error: 0 (Success), outsize: 32
* Expire cleared
* Remembering we are in dir something-themes-0.9p/darkstarFashion/
< 226 Transfer complete.
* Connection #0 to host ftp.somehoster.net left intact
* Couldn't find host ftp.somehoster.net in the .netrc file, using defaults
* Re-using existing connection! (#0) with host ftp.somehoster.net
* Connected to ftp.somehoster.net (77.232.67.28) port 21
* Request has same path as previous transfer
> EPSV
* Connect data stream passively
< 229 Entering Extended Passive Mode (|||50122|)
* Expire at 1189582663 / 461217 (300000ms)
*   Trying 77.232.67.28... * Connecting to 77.232.67.28 (77.232.67.28) port 50122
> TYPE I
< 200 Type set to I
> SIZE darkstar.png
< 213 5020
> RETR darkstar.png
< 150 Opening BINARY mode data connection for darkstar.png (5020 bytes)
* Getting file with size: 5020
OPEN[134905360] flags: 0x8000
   unique: 403, error: 0 (Success), outsize: 32
unique: 404, opcode: READ (15), nodeid: 49, insize: 64
READ[134905360] 8192 bytes from 0
* Expire cleared
* Remembering we are in dir something-themes-0.9p/darkstarFashion/
< 226 Transfer complete.
* Connection #0 to host ftp.somehoster.net left intact

```

---

### Post by Rene7705 on 2007-09-12
Didn't spot this warning on the [curlftpfs homepage]("http://curlftpfs.sourceforge.net/") earlier: 

    * CurlFtpFS just hangs. What should I do?
      There is a bug with curl 7.15.5 and 7.16.0, please use another version. See: [http://sourceforge.net/tracker/index.php?func=detail&aid=1618359&group_id=976&atid=100976](http://sourceforge.net/tracker/index.php?func=detail&aid=1618359&group_id=976&atid=100976).
      If this is not the problem, run the program with -d -v -o ftpfs_debug in a separate terminal, repeat the commands that make it crash and file an issue posting the output.

rene@goose:~$ sudo dpkg -l | grep curl
ii  curlftpfs                                  0.9-2                                  filesystem to access FTP hosts based on FUSE
ii  libcurl3                                   7.15.5-1ubuntu2.1                      Multi-protocol file transfer library
ii  libcurl3-gnutls                            7.15.5-1ubuntu2.1                      Multi-protocol file transfer library
rene@goose:~$ 


Guess my question has changed to: how to replace a package with another version of it, and how to sort out the conflicts it might create (with other installed apps / packages)...

---

### Post by Rene7705 on 2007-09-12
Using the normal FTP-with-login connect from the top menubar "Places | Connect to server", I get a connection that doesnt propegate login details properly to apps trying to open files on that share.

For instance, GVim asks for a password, but logs in with the local username (not the remote one specified in "Connect to server"). So I can't use vim, unless you have a tip that LARTs GVim into using the default keyring..

The default Text Editor opens files on the share read-only, and I can't change that.

---

### Post by Rene7705 on 2007-09-12
thread continues here: [http://ubuntuforums.org/showthread.php?p=3354181#post3354181](http://ubuntuforums.org/showthread.php?p=3354181#post3354181)

---

