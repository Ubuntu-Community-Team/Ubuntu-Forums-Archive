---
title: "[SOLVED] File Access Over Network"
date: 2008-06-08
forum: Networking &amp; Wireless
---

### Post by talking Llama on 2008-06-08
Hey. I've set up a network and everything and i'm trying to share files over the network. Now on my laptop (Ubuntu 8.04) I can see the shared folder but when I try to access it it says "Unable to mount location: FAiled to mount Windows share", however on my desktop (Ubuntu 8.04) I can see the files being shared from the laptop and access them and copy them etc etc. Any help on what's going wrong on the laptop?

---

### Post by ilrudie on 2008-06-08
Unless you have a windows computer that must be able to get files off your Ubuntu boxes I would recommend using NFS instead of Samba/Windows file sharing.  Check out this how-to: [https://help.ubuntu.com/community/SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo)

---

### Post by superprash2003 on 2008-06-08
right.. but if you have windows pcs.. then in your laptop type smb://(ip of share) under places->Computer in the location area

---

### Post by talking Llama on 2008-06-09
Thanks for all your help guys but I think there was just something wrong with the access permissions on some of the folders. Silly me. :(. Thank you very much for replying though! :D

---

