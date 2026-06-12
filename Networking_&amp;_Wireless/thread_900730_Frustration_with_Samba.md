---
title: "Frustration with Samba"
date: 2008-08-25
forum: Networking &amp; Wireless
---

### Post by chrisn8cuh on 2008-08-25
I set up SWAT hoping to make my configuring of Samba a little easier. I only get these options though when open SWAT...

I am not sure if I maybe installed SWAT in the wrong folder... :( Anyhow, none of the general links at the bottom of the page work.. They just 404 out. I need some advice :)

[IMG]http://chrisn8cuh.googlepages.com/samba.jpg[/IMG]

:confused:
:confused:
:confused:

---

### Post by jeannemp on 2008-08-25
chrisn8cuh,

I had the same problem and this site helped [https://help.ubuntu.com/community/Swat]("https://help.ubuntu.com/community/Swat").  In general you need to need to share the Samba conf file, smb.conf using the following command:

**sudo chmod 777 /etc/samba/smb.conf**

Hope this helps.

---

### Post by chrisn8cuh on 2008-08-25
Thanks! That is exactly what I needed.

---

### Post by dmizer on 2008-08-25
Be sure you also performed these commands:
```
sudo chmod g+w /etc/samba/smb.conf
sudo chgrp adm /etc/samba/smb.conf
```
Otherwise you have world read/write/execute permissions (anyone/anything can make changes to it) to /etc/samba/smb.conf. The above commands only make this marginally better, but it's certainly better than straight 777 permissions.

---

### Post by chrisn8cuh on 2008-08-25
> **dmizer said:**
> Be sure you also performed these commands:
```
sudo chmod g+w /etc/samba/smb.conf
sudo chgrp adm /etc/samba/smb.conf
```
Otherwise you have world read/write/execute permissions (anyone/anything can make changes to it) to /etc/samba/smb.conf. The above commands only make this marginally better, but it's certainly better than straight 777 permissions.

I am having trouble with the permission reverting back to normal. Anyone got any idea why this would happen? I will remove a folder and all of a sudden I cannot get back to SWAT. I am really confused about what the major important permissions are and what overrides what.

---

### Post by dmizer on 2008-08-25
> **chrisn8cuh said:**
> I am having trouble with the permission reverting back to normal. Anyone got any idea why this would happen? I will remove a folder and all of a sudden I cannot get back to SWAT. I am really confused about what the major important permissions are and what overrides what.

I'm not sure exactly why your permissions are reverting, but this is probably a good thing.

Try fixing this by adding yourself to the samba group with the following two commands:
```
sudo smbpasswd -L -a ubuntu_username
sudo smbpasswd -L -e ubuntu_username
```

Please let me know if this fixes things for you, because I'd like to change the howto.

Here's several reasons why permissions on smb.conf are so important:

Anyone gaining access to your computer by remote (yes this is possible in linux), or locally can edit the smb.conf file without even getting challenged with a password. This is dangerous because:
1) By manipulating the smb.conf, they can give themselves an account on your computer from which they can do whatever they like without your knowledge.
2) They can change the smb.conf file to share any part of your computer they like, and subsequently delete or manipulate it.
3) Possibly inject malicious code into your system.
4) Easily use your system as a platform for launching attacks anonymously on the internet.

Or in other words: They could damage your system, delete your data, and/or damage other people's systems.

Permissions are in place on Ubuntu for good reasons. It's a good idea to seriously consider this any time you make changes to permissions levels.

Edit:
Found this link: [http://linuxtnt.wordpress.com/2007/08/12/starting-swat-on-ubuntu/](http://linuxtnt.wordpress.com/2007/08/12/starting-swat-on-ubuntu/)

---

