---
title: "[SOLVED] Nas drive &amp;quot;mount error 13&amp;quot;"
date: 2008-08-13
forum: Networking &amp; Wireless
---

### Post by DamonChyld on 2008-08-13
I just installed hardy and am getting a "mount error 13" when trying to mount my lacie 1tb nas drive after following my cheat sheet here

```
synaptic-package-manager

samba

smbfs

sudo gedit /root/.credentials

username=<usr on nas>

password=<pw on nas>

sudo chmod 777 /root/.credentials

cd /

sudo mkdir bigdisk

sudo gedit /etc/fstab

//192.168.0.66/bigdisk /bigdisk cifs credentials=/root/.credentials,rw,auto,uid=dna,gid=dna 0 0

sudo ln -s /etc/init.d/umountnfs.sh /etc/rc0.d/K15umountnfs.sh

sudo ln -s /etc/init.d/umountnfs.sh /etc/rc6.d/K15umountnfs.sh

sudo mount -a (or restart)
```

I did not do any configuring with samba so the problem is probably there?

---

### Post by DamonChyld on 2008-08-13
Also, bodhi.zaden was helping me with this a while back ([http://ubuntuforums.org/showthread.php?t=792096](http://ubuntuforums.org/showthread.php?t=792096)), and then my hard drive went down.

I can mount using 
```
sudo mount -t cifs //192.168.0.66/bigdisk /bigdisk -o username=<usr>,password=<pass>

```

and have added my user to samba with 
```
sudo smbpasswd -a <usr>
```

---

### Post by DamonChyld on 2008-08-14
Kindly bump, I am at a loss ;)

---

### Post by DamonChyld on 2008-08-19
Hmm, no ideas?

---

### Post by jimv on 2008-08-19
I never really understood the point of using a credentials file in your /etc/fstab.  If someone can get to that, they can go look in the credentials file too.  So my advice?  Put the login/password in the fstab to keep things simple.

---

### Post by DamonChyld on 2008-08-19
Heh... well that did it ;)

---

