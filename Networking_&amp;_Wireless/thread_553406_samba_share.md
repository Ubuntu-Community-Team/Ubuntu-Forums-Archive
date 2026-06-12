---
title: "samba share"
date: 2007-09-17
forum: Networking &amp; Wireless
---

### Post by gishaust on 2007-09-17
hi everyone 

I have windows 2000 server in a workgroup environment. I also have  a samba server that i have set up so that I can share the folders on it. 

when I smbclient -L ipadress -U% I get that the 2000 server is master. that is correct. I then create a share with the samba server.

My problem is that the whole network sees the samba machine.  Then I goto put the share name it sees it. But it will not allow me to use the username and password to access the share.

does anyone have an idea on what I am doing worng?

Gishaust

---

### Post by wjp.reg on 2007-09-17
> **gishaust said:**
> hi everyone 

I have windows 2000 server in a workgroup environment. I also have  a samba server that i have set up so that I can share the folders on it. 

when I smbclient -L ipadress -U% I get that the 2000 server is master. that is correct. I then create a share with the samba server.

My problem is that the whole network sees the samba machine.  Then I goto put the share name it sees it. But it will not allow me to use the username and password to access the share.

does anyone have an idea on what I am doing worng?

Gishaust

did you..
```
sudo smbpasswd -a username
``` on the samba server?  This adds a user and password permission to use the share(s) created on your samba server.

---

### Post by gishaust on 2007-09-17
Thanks for the tip 

I so went to this page [https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)
and followed the "Configuring your computer as a server"

when i get to this command 

sudo smbpasswd -a username

I get this response
Unable to modify TDB passwd ! Error: Record exists
 occured while storing the RID index (RID_00000bb8)
Failed to add entry for user fbs.
Failed to modify password entry for user fbs

Do you know why this is happening,

gishaust

---

### Post by gishaust on 2007-09-18
I fixed it the following is what i did

First placed in the bottom  smb.conf the following

path = /home
available = yes
browsable = yes
public = yes
writable = yes
force user = fbs

Then  i saved it
 
sudo smbpasswd -a fbs
change the passwords

Restarted smb
sudo /etc/init.d/samba restart

I was able to access it from the whole network straight way.

I have one question do you have to have an usr account so that you can smbpassword 
Gishaust

---

### Post by wjp.reg on 2007-09-18
> 
I have one question do you have to have an usr account so that you can smbpassword 

See the following..

[Intro to SAMBA]("http://www.fredshack.com/docs/samba.html")


Every user that connects to the Samba server must have a user account.

cheers!

---

### Post by gishaust on 2007-09-22
thank you for your respnse i  will have a look

---

