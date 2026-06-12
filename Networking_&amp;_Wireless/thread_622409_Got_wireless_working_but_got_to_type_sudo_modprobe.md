---
title: "Got wireless working but got to type sudo modprobe bcm43xx"
date: 2007-11-24
forum: Networking &amp; Wireless
---

### Post by statue12 on 2007-11-24
I have finaly got my broadcom wireless working but for some reason i got to keep typing sudo modprobe bcm43xx into the terminal to enable my wireless, it doesnt do it automatic.  Anyone know what the issue might be.

Thanks

---

### Post by kevdog on 2007-11-24
echo bcm43xx | sudo tee -a /etc/modules

Remove the blacklist line in /etc/modprobe.d/blacklist for the bcm43xx driver

---

### Post by statue12 on 2007-11-25
that worked great, thanks:)

---

