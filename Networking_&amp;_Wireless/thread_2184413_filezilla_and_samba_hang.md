---
title: "filezilla and samba hang"
date: 2013-10-29
forum: Networking &amp; Wireless
---

### Post by Newbunto on 2013-10-29
I have the filezilla GUI FTP client running on Ubuntu. If I retrieve a file from an FTP server, saving the file 'locally' in a directory that is accessed via Samba (mounted via GVFS) then filezilla just seems to hang after retrieving and writing some data and the filezilla window goes grey. I have to 'Force Quit' filezilla. The file has been saved up to the point of the hang.

If I retrieve the same file, saving it, for example, on my desktop, or other genuinely local directory it works correctly.

The Samba server is on the LAN. The FTP server is out there on the internet.

filezilla 3.5.3
ubuntu 12.04 LTS (kernel 3.2.0-55)

Edit: PS The file being retrieved is about 500KB, so nothing too demanding.

---

### Post by Newbunto on 2013-11-01
bump

---

### Post by Newbunto on 2013-11-08
Upgraded to Ubuntu 13.10 which provides FileZilla 3.7.3

Unfortunately still the same result. :-(

---

### Post by Newbunto on 2013-12-02
bump

---

### Post by Newbunto on 2014-01-09
Some further information ...

* The ftp command line client does not experience any issues retrieving the same remote file from the same remote server to the same local directory, thereby tentatively ruling out a whole lot of potential problem areas.

* When filezilla hangs it has Status "Running" but Waiting Channel "futex_wait_queue_me". I don't know whether that is significant at all.

* filezilla has no problem transferring the same file in the opposite direction.

---

