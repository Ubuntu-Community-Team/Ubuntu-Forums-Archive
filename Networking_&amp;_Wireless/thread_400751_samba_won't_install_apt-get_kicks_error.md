---
title: "samba won't install apt-get kicks error"
date: 2007-04-03
forum: Networking &amp; Wireless
---

### Post by acidblue on 2007-04-03
Using Dappper.

Here is the error apt-get gives when i try to 'apt-get install samba'

Setting up samba (3.0.22-1ubuntu3.2) ...
update-rc.d: warning: /etc/rc2.d/K09samba is not a link to ../init.d/samba or /etc/init.d/samba
update-rc.d: warning: /etc/rc3.d/K09samba is not a link to ../init.d/samba or /etc/init.d/samba
invoke-rc.d: dangling symlink: /etc/rc2.d/K09samba
dpkg: error processing samba (--configure):
 subprocess post-installation script returned error exit status 102

It won't uninstall either kicks simular error messg.

---

### Post by bruenig on 2007-04-03
Perhaps
```
sudo rm /etc/rc2.d/K09samba
```

---

