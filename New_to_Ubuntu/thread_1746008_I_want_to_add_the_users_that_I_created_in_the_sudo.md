---
title: "I want to add the users that I created in the sudoers file?"
date: 2011-05-01
forum: New to Ubuntu
---

### Post by Imesmi on 2011-05-01
I want to add the users of the linux in the sudoers file but I have a problem i don't know which is the root password :( :( . Can someone please ,please help me .
How can i find out the root password because I can't connect to the internet and i really need to connect to the net .

---

### Post by sisco311 on 2011-05-04
The root account password is locked by default. The first user created during the installation is allowed to run any command as root. See: [uhelp]community/RootSudo[/uhelp]

If you want to allow another user to use sudo, simply add it to the admin group:
```
sudo gpasswd -a **username** admin
```
where **username** is the login name of the user.

---

