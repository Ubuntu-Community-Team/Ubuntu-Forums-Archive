---
title: "sysctl.conf write permision with root privileges"
date: 2009-10-31
forum: New to Ubuntu
---

### Post by vasiauvi on 2009-10-31
Hello all, 
I have made some modification on sysctl.conf file and after reboot it's not entering in the X sesion. I've booted in safe mode and tried to modify woth root privileges and nano the sysctl.conf file but it's says that the file is "read only".
I've entered also with a live cd and is courious that is want a password. A live Cd asks a password?!?

Do you know an other methode to change the sysctl.conf file? I have a backup but also the the mv (move) command doesn't work.

I have Ubuntu 9.04.
Thanks!

---

### Post by Waappu on 2009-10-31
Hi,

Did you try give write permission ?
```
sudo chmod ug+x sysctl.conf
```

---

### Post by vasiauvi on 2009-10-31
> **Waappu said:**
> Hi,

Did you try give write permission ?
```
sudo chmod ug+x sysctl.conf
```

Finally I've managed to enter with LiveCd and changed the file like it was. But is not working and is telling me to look in the syslog file. I've looked and didn't understood nothing, or better said I don't see nothing usefull in that file.

---

### Post by vasiauvi on 2009-10-31
I've used this tutorial in hope to speed a little bit my Ubuntu but I did it more wrong!:( [http://www.tuxradar.com/content/make-linux-faster-and-lighter](http://www.tuxradar.com/content/make-linux-faster-and-lighter)

I've changed:
 /etc/fstab 
/etc/hosts 
/etc/sysctl.conf 

sysctl.conf I've changed it like before. Now I want to change the other 2 files...hope it's working. If not I will come back here for some ideas!

---

### Post by vasiauvi on 2009-10-31
> **vasiauvi said:**
> I've used this tutorial in hope to speed a little bit my Ubuntu but I did it more wrong!:( [http://www.tuxradar.com/content/make-linux-faster-and-lighter](http://www.tuxradar.com/content/make-linux-faster-and-lighter)

I've changed:
 /etc/fstab 
/etc/hosts 
/etc/sysctl.conf 

sysctl.conf I've changed it like before. Now I want to change the other 2 files...hope it's working. If not I will come back here for some ideas!

No I'am here with LiveCd and changed the fstab and hosts. I will reboot and hope to work!

---

