---
title: "Samba Share access via FTP"
date: 2008-06-06
forum: Networking &amp; Wireless
---

### Post by rusher81572 on 2008-06-06
I need help. My co-worker has a windows share(On Desktop) on his Ubuntu server and is trying to download files from the share on the server via FTP. When he tried to download from the ftp server, the files will say operation not permitted. His current permissions are 755 and everything looks good.He is using Ubuntu Server with ProftpD Server. Access to other files in the FTP folder download and upload perfectly. He is only having issues with the mounted samba share from FTP.

Fstab File:
//server1/allmusic /home/FTP-shared/allmusic cifs exec,credentials=/etc/cifspw,file_mode=0777,dir_mode=0777 0 0

---

### Post by rusher81572 on 2008-06-06
Your assistance is greatly appreciated.

---

