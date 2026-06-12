---
title: "Lost Root Password"
date: 2010-02-21
forum: New to Ubuntu
---

### Post by DarleneGurr on 2010-02-21
I have lost the root password.  The instructions at [http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword) are clear until the sentence "In this case, you want the Drop to root shell prompt option so press the Down arrow to get to that option, and then press Enter to select it".  Well, what exactly do I type then?  Thanks for all help!

---

### Post by spiky001 on 2010-02-21
You have to go into root this alows you to make the  changes so you have to follow what it sayes on screen, so you will be given 4 options looks like 3rd one is what you want Root then follow instructions

---

### Post by mikewhatever on 2010-02-21
Ubuntu doesn't have root password by default. If you changed that, and setup root password, you can't use the psychocats' guide, cause you have no way to login.

---

### Post by mcduck on 2010-02-21
Did you really loose the _root_ password, or the normal *user* password that admin users use (with sudo) for administration tasks?

If it really was actual root password (whcih you really shouldn't even have set), then you are out of luck, that guide isn't going to help you. If you have set the root password you need that password to access recovery mode..

---

### Post by DarleneGurr on 2010-02-21
To mcduck:  It is the admin password that I have lost.  This means that if I am in Terminal and want to use apt-get to update my computer or get new codecs etc I cannot use sudo without the admin password. ( I get a response saying that I cannot execute apt-get as root)  I thought that admin password and root password meant the same thing.  Thanks!

---

### Post by bodhi.zazen on 2010-02-21
If you set a root password, and lost sudo access and forgot the root password, you will need to boot alive CD.

You would then mount your partition at /mnt, using sda1 as an example,

```
sudo mount /dev/sda1 /mnt
```

You then chroot in and change the password

```
sudo chroot /mnt
```

then passwd or passwd <user>

---

