---
title: "Samba requires password? Help please..."
date: 2007-02-24
forum: Networking &amp; Wireless
---

### Post by boobooq88 on 2007-02-24
Ok well... I'm running Linux Mint 2.2 Bianca (Ubuntu with all multimedia codecs installed) on my laptop.  I set up samba last night so I can access the shared folders on my desktop.  The desktop runs Windows XP (cuz my mom doesn't listen to me bout computers... oh well).  The thing is.. I can look at the shared folders on the desktop just fine using my laptop.  However, when I try to use the desktop to access my shared folders on my laptop it asks for a username and password.  And for the life of me I can't figure what they are.

Thanks.

---

### Post by pebo on 2007-02-24
[Here]("https://help.ubuntu.com/community/SettingUpSamba") is a tutorial on how to set up samba. Basically you need to set a password on the server like this: ```
sudo  smbpasswd -a [your username on the client]
```Set the password. Then you can log in on the client machine.
hth!

---

### Post by boobooq88 on 2007-02-24
Alright.  Awsome!  It worked.  Thank you much.  :)

---

