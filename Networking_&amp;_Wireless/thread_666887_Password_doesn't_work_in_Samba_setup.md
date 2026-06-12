---
title: "Password doesn't work in Samba setup?"
date: 2008-01-13
forum: Networking &amp; Wireless
---

### Post by budmaester on 2008-01-13
I am trying to setup a share using Samba for a network printer attached to my Ubuntu station. I intend to use the printer with a Windows 2000 station on the network hard wired to the router and a laptop XP-Pro via a wireless connection. I am able to see the Ubuntu system and access the files. I can see the PDF printer, but I cannot get the HP to show up as a share.  After setting up the share, Samba asks for my user password, but does not recognize it. What am I missing? Is there a default password for Samba?  Any suggestions would be welcomed.

Thankyou.

:guitar:Budmaester

---

### Post by zero-9376 on 2008-01-13
if you are talking about the windows client asking for your user/pass have you

sudo smbpasswd -a yourusername #add user
enter password
sudo smbpasswd -e yourusername #enable user

---

### Post by budmaester on 2008-01-13
the password prompt appears in the samba screen. Will I have to create my user name and pw in Samba.

---

### Post by zero-9376 on 2008-01-14
what application specifically are you using to set up the share? the printing app under system>admin or something else.
i am not sure if you will have to create the user/pass in samba, if the pdf printer is working and you can access your shares i would say it is already working, I am just used to it from previous systems it may not be required in gutsy
maybe posting your /etc/samba/smb.conf would help, although I am no expert I will try to help and others will probably have helpful answers for you

---

