---
title: "ttySHSF0 Permission Reset after boot"
date: 2005-05-30
forum: Networking &amp; Wireless
---

### Post by adajar99 on 2005-05-30
Hello,

I am a linux newbie and have installed Ubuntu Hoary in my PC.  I have managed to get it up and running except for a minor item which I hope someone can explain to me.

I am using an hsf modem (conexant) and I installed the driver from Linuxant.  After installation, I had a problem with permissions on ttySHSF0.  So I did a chmod, and was able to connect.  However, after I rebooted the computer, I got the same error message, and when I looked, it was as if I didn't do a chmod earlier.  I have also tried chown, but after rebooting, the file permissions were reset.

Can anyone please explain to me why it is so and what I can do to remedy this problem? (other than buying a "real" modem).

Thank you very much.

---

### Post by adajar99 on 2005-05-30
Hello,

I found out what happens.  The system resets the permissions to the devices tty* and others during boot up.  The permissions are defined in the file /etc/udev/permissions.d.  I just entered a line at the end of the file changing file permissions so that any user can access the modem.

---

