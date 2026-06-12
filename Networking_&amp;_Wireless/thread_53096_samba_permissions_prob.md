---
title: "samba permissions prob"
date: 2005-07-30
forum: Networking &amp; Wireless
---

### Post by mikefeil on 2005-07-30
Hi I have a fileserver with ubuntu which is wirelessly connected to my home network through dhcp. I'm trying to get my main box which uses xp to access my files on my file server. I have set up samba,using the HOWTO guide  (I had got it to work right on my laptop which had ubuntu).

I cant see it in my network neighbourhood, but I can acess it by going \\fileserver, I then get the user pass dialog, I type in the right passwords (account on this computer) but it says its not right. Anyway help would be great.

---

### Post by drummer on 2005-07-30
You need to add a user to samba by doing```
sudo smbpasswd -a user
```where user is a user account on the server. You can add a new user to the system primarily to use to login using samba or use the existing account (not root though, don't think that would work, or be a good idea). Then```
sudo nano /etc/samba/smbusers
```and enter into the new file```
user = "user"
```

Ubuntuguide.org instructions for adding users to system/samba:
[http://ubuntuguide.org/#addeditdeletesystemusers](http://ubuntuguide.org/#addeditdeletesystemusers)
[http://ubuntuguide.org/#addeditdeletenetworkusers](http://ubuntuguide.org/#addeditdeletenetworkusers)

There's instructions in the samba section on ubuntuguide.org on sharing home folders and public shares, etc.

After you're finished configging, restart samba:```
sudo /etc/init.d/samba restart
```and you should be able to login from XP with the username and password you entered in smbpasswd.

---

### Post by mikefeil on 2005-07-31
thanx alot mate :D worked perfect

---

