---
title: "Files sharing between Ubuntu and OpenSuse"
date: 2008-12-30
forum: New to Ubuntu
---

### Post by vasiauvi on 2008-12-30
Hello all!
I want to share some folders from my PC on witch i have Ubuntu 8.10 and my laptop with OpenSuse. Can anyone help me with this? 
Thank you!

---

### Post by Sarmacid on 2008-12-30
Since both are linux, you might want to look into setting up NFS [https://help.ubuntu.com/community/SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo)

Also you can also set up shared folders with samba, and these would be visible to a windows box
[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

---

### Post by scorp123 on 2008-12-30
> **vasiauvi said:**
> Hello all!
I want to share some folders from my PC on witch i have Ubuntu 8.10 and my laptop with OpenSuse. Can anyone help me with this? 
Thank you! Use SSH.
[http://ubuntuforums.org/showthread.php?p=6450967#post6450967](http://ubuntuforums.org/showthread.php?p=6450967#post6450967)

---

### Post by vasiauvi on 2008-12-31
Thank you.It's working with SSH. But and other question: I have installed vsftpd but i can't manage to put the Default directory, when i put on Firefox my IP: 192.168...(i have a router) nothing appears.I use this tutorial :[http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch15_:_Linux_FTP_Server_Setup](http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch15_:_Linux_FTP_Server_Setup)  .I want to make an ftp server because i want to share some folders witch are on NTFS drive (on WindowsXP). Somebody have a tutorial where to explain in more detail (step by step) how to configure a ftp server, how to download files from that ftp.
I am sure that on the internet are a lot of tutorials like this but if somebody knows one tutorial for begginers.
Thank you and wish you HAPPY NEW YEAR!!!!!!!!!

---

