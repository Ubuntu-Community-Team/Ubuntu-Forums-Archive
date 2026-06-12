---
title: "Module, bcm43xx"
date: 2007-03-28
forum: Networking &amp; Wireless
---

### Post by o0Jerry0o on 2007-03-28
I am currently using a broadcom linksys card my internet works perfect!
My only problem is having to run modprobe bcm43xx everytime I boot, is there a way I can make the system boot this module itself at startup?

---

### Post by Floppyjoe on 2007-03-28
Add bcm43xx to /etc/modules.
Are you using an older version of Ubuntu?

---

### Post by o0Jerry0o on 2007-03-29
Nope, i'm using Ubuntu 6.10. I'll try adding bcm43xx to /etc/modules, or should I add bcm43xx-firmware?

---

### Post by Floppyjoe on 2007-03-30
> **o0Jerry0o said:**
> Nope, i'm using Ubuntu 6.10. I'll try adding bcm43xx to /etc/modules, or should I add bcm43xx-firmware?
Usually Ubuntu will automatically load the bcm43xx module at startup but if you add that to /etc/modules it should load at startup if it does not already.

---

### Post by o0Jerry0o on 2007-04-02
Well.. I added it but it still won't load bcm43xx by itself... hmm

---

### Post by spd106 on 2007-04-02
Check that you haven't blacklisted it by mistake, look in the /etc/modprobe.d/blacklist
file.

Do you receive any error messages after running modprobe bcm43xx? Does dmesg show anything?

---

### Post by o0Jerry0o on 2007-04-06
Worked perfect, Thank you

---

