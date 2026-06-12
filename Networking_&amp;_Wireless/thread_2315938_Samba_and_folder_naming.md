---
title: "Samba and folder naming"
date: 2016-03-03
forum: Networking &amp; Wireless
---

### Post by azteca_04 on 2016-03-03
Hi,

i have install Samba 4.1.6 on a ubuntu server 14.0.4 and i have created a folder name KMS also on the smb configuration everything is in upper case, but when i acess it from a Windows 7 computer the folder name is kms i would want it to be in upper case like i said i also have somo folder with upper and lower cases and they appear as they are created, but i cannot see why this wount work 

an annyone help me please?

---

### Post by bab1 on 2016-03-03
> **azteca_04 said:**
> Hi,

i have install Samba 4.1.6 on a ubuntu server 14.0.4 and i have created a folder name KMS also on the smb configuration everything is in upper case, but when i acess it from a Windows 7 computer the folder name is kms i would want it to be in upper case like i said i also have somo folder with upper and lower cases and they appear as they are created, but i cannot see why this wount work 

an annyone help me please?
The folder name is not what you see.  What you should see is the Share Name.  All of my folders on the server are lowercase.  The share names are like this [Share Name].  The SMB resource is always //SERVER_NAME/Share_Name.

---

### Post by azteca_04 on 2016-03-04
Yes, an on the Samba configuration file i have it like 

[KMS]
 comment = KMS
 path = /../KMS

and still on the windows is like kms i want it also to appear in capital letters

---

