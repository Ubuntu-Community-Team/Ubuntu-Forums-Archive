---
title: "sftp client for xubuntu"
date: 2011-09-04
forum: New to Ubuntu
---

### Post by Frozen Forest on 2011-09-04
Is there an sftp client for Xubuntu that support keys with password and non-standard port? Looking for something similar to WinSCP on windows. In Ubuntu is this done easly, simply but private and public key in ~/.ssh and use the address 'sftp://username@ssh-server:port' could there maybe be something similar in Xubuntu?

---

### Post by spiky001 on 2011-09-04
If you install ssh you can sftp from window manager, (mote I use ubuntu with nautilus) i presume it will work with Xbubuntu window manager

---

### Post by Frozen Forest on 2011-09-04
> **spiky001 said:**
> If you install ssh you can sftp from window manager, (mote I use ubuntu with nautilus) i presume it will work with Xbubuntu window manager
When you are able to login using nautilus are you using gnome-keyring, but there might be something similar in Xubuntu so you might be right.

---

### Post by spiky001 on 2011-09-04
It asks for password, also you can change the port as well

---

### Post by spiky001 on 2011-09-04
[http://ubuntuforums.org/archive/index.php/t-30709.html](http://ubuntuforums.org/archive/index.php/t-30709.html)

---

### Post by Frozen Forest on 2011-09-04
Noticed that it's actually 'seahorse' that manage the ssh keys and I think Xubuntu has it installed and hopefully will Thunar make use of it. I'm not the one using Xubuntu but a friend with little computer knowledge.

---

### Post by Frozen Forest on 2011-09-04
Tried to connect to the sftp server using Thunar, is it possible to get nautilus to work in xubuntu as it does in ubuntu.

---

### Post by spiky001 on 2011-09-05
If you installed ssh server can you ssh into it from term ```
ssh username@ipaddress
```

---

### Post by Frozen Forest on 2011-09-05
> **spiky001 said:**
> If you installed ssh server can you ssh into it from term ```
ssh username@ipaddress
```
I know how to use ssh, I use it regularly problem is to find a good **sftp** client for Xubuntu, Filezilla wont work since it doesn't support ssh keys with password, it would be nice with something similar to WinSCP. With Ubuntu you get nautilus and seahorse that will identify SSH keys and therefore make it possible to connect to sftp, start 'seahorse' in terminal, but this only work if both the public and the private key is present in ~/.ssh. The question is if installing seahorse and nautilus on Xubuntu 10.04 make it possible to connect to sftp shares as it's done in Ubuntu? I know that 'sshfs' can be used to mount an sftp, but the person that is supposed to connect to the sftp (chrooted)  lack the knowledge for that.

---

