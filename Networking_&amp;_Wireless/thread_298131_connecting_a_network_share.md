---
title: "connecting a network share"
date: 2006-11-12
forum: Networking &amp; Wireless
---

### Post by numbers1thru9 on 2006-11-12
I am running ubuntu edgy server and I would like it to connect to a share on my windows server 2003 machine. The filesystem is NTFS and I have smbclient installed and all I want it to do is read the files I dont need it to write but when I use the smbclient -L hostip i get the following error: Error returning browse list: NT_STATUS_ACCESS_DENIED and I have my permissions on my 2003 box set correctly for anonymous read access but can anyone help me because Im still new to linux and I want to learn command line only for a while. Thanks

---

### Post by numbers1thru9 on 2006-11-12
Ok i got it to list the shares now, I want to mount the ntfs file system but if i try to use smbmount it says that the command could not be found. Any ideas on how to get it to mount?

---

### Post by numbers1thru9 on 2006-11-12
also if i try to use sudo mount -t //ip/sharename /mnt/sharemountfolder/ -t ntfs it tells me that the special device //ip/sharename does not exist

---

### Post by Jeremiah478 on 2006-11-18
This may not be right but I thought when connecting to a network drive the file system type went right after the -t.  So it would be:

sudo mount -t  ntfs //ip/sharename /mnt/sharemountfolder/

Something like that, and I'm not so sure about the -t ntfs afterwards, that would be saying the your linux partition is ntfs.

Hope this helps some.

---

