---
title: "Ubuntu Mint login trouble"
date: 2010-05-31
forum: New to Ubuntu
---

### Post by myolbug on 2010-05-31
Ok, I have just installed Mint 9 64bit Live DVD on a new hardrive. I have a Systemax PC with an AMD 4400+ dual core 64bit proc and 4G ram. It works great but the login is not the usual GUI, rather it is the black screen/white letters terminal style. I have to enter in the user name, then password, then I have to enter in startx to get the actual OS up. 

What changes do I need to make to have the splash show and get this automated. All updates are current. This applies to all users on this machine.

---

### Post by cariboo on 2010-05-31
Once you log in, try:

```
sudo /etc/init.d/gdm start
```

If that doesn't work, you need to install gdm:

```
sudo apt-get install gdm
```

---

