---
title: "Transmission &quot;Couldn't add corrupt torrent&quot;"
date: 2009-02-15
forum: New to Ubuntu
---

### Post by Calfaile on 2009-02-15
Hi,

I'm having a problem with transmission 1.42 (7495).  I have it watching a folder and automatically adding torrents that I drop in there.  However, when I drop in a torrent file, I get the following error in Transmission: "Couldn't add corrupt torrent <file>".  If I drag the torrent file into transmission manually, it adds as expected.

I don't know if it's significant, but in the error message the file name is slightly different. If the file name is "my.cat.videos.torrent", the error message would be "Couldn't add corrupt torrent ._my.cat.videos.torrent"

Has anyone else seen this?

---

### Post by supersonicdarky on 2009-02-15
[try upgading to latest](http://www.transmissionbt.com/download.php) (1.50) and see if it still happens

---

### Post by Calfaile on 2009-02-20
I upgraded and it still happens.  What's interesting is that it doesn't happen when my torrent downloader adds torrents, but does when I add torrents over the network and when transmission restarts.

---

### Post by flamingpolo on 2009-06-06
Hi,

I am seeing the same issue. However, it does not prevent Transmission from starting the torrent and downloading it.

Couldn't this be caused by Firefox creating temporary files when downloading something, Transmission then trying to download the temp file?

---

### Post by rudie152 on 2010-04-12
I have the same problem. I am using a mac to save torrent files with firefox to ubuntu server. The hard drive at the server is linux ext4, and its strange because I was not getting this error before I changed the hard drive from fat32 to ext4. Does anyone know a fix?

---

### Post by vectorm12 on 2010-09-09
Having the same issue using dropfolders and using macs to drop the torrentfiles onto the ubuntuserver running 10.04

However if I use a WinXP machine to drop the files I get no such error message.

Dropping files from mac still start and seem to work but for some reason I can tell that all torrentfiles I drop from mac show up as 1MB when they are in fact about 50kB.

So it would seem this is either related to the SMB service in ubuntu or the smb/cifs client in OS X.

Going to keep testing ideas until I come up with an answer to what might be causing this behavior. it's working just fine but I hate getting errormessages in my log.

---

### Post by tedrogers on 2011-03-02
Uncheck "automatically add torrents" from whatever folder you have specified in preferences.

This solved it for me.

---

