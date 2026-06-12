---
title: "Samba Share REFUSES to mount in windows"
date: 2008-01-17
forum: Networking &amp; Wireless
---

### Post by lenswipe on 2008-01-17
Hi all

i have a windows xp home computer and an ubuntu gutsy computer. I shared a folder on the ubuntu computer and it worked well. But when i try and mount the share in windows it asks me for a username and password. When i type the username and password i have for  my account on the computer (yes i am a computer administrator on the ubuntu machine) it wont accept it. Nor will it accept the root username and password (i changed the root password) neither will it accept the samba password.

Anyone got any ideas?

EDIT: When i try and mount a samba share in windows it asks me for a password. I have tried all the passwords on my samba server but it will not accept any of them - it just keeps saying they are incorrect. What password am i looking for?

---

### Post by Ocxic on 2008-01-17
make sure your firewall has the samba ports open, try installing "webmin" great al round admin tool. go to 127.0.0.1:10000 in firefox after install.
that will let you setup users and such so that you can share your stuff prolly easier then right now.

---

### Post by lenswipe on 2008-01-17
> **Ocxic said:**
> make sure your firewall has the samba ports open, try installing "webmin" great al round admin tool. go to 127.0.0.1:10000 in firefox after install.
that will let you setup users and such so that you can share your stuff prolly easier then right now.

it doesnt seem to be anything to do with the firewall....

its letting me try to connect. It just wont accept the password...

---

### Post by peitschie on 2008-01-17
Hi lenswip,

You will find this link useful: [https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

Specifically,  you need to run the following in a terminal to add a new samba user:
```

sudo  smbpasswd -a username

```

This will allow you to create a new samba username/password that you'll be able to use to log in from windows :)

---

### Post by lenswipe on 2008-01-23
AWESOME!!!!! THANK YOU THANK YOU THANK YOU TIMES 10000000000000000000000000000000000000000

IVE BEEN TRYING TO GET THIS WORKING FOR AGES!!

*presses the thank you button*

---

### Post by peitschie on 2008-01-23
My pleasure :).  I hope you find your Ubuntu experience as satisfying as i have found mine :D

---

