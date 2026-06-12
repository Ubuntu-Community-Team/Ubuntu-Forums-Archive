---
title: "Wubi - login failure after hard reboot"
date: 2009-05-06
forum: New to Ubuntu
---

### Post by bitrocker on 2009-05-06
Hello,

after a hard reboot I can`t login in anymore. The login screen appeares, but when I enter my password, it just reloads the screen. Login via console is still possible.

As mentoioned in [https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20access%20the%20Windows%20drives?]("https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20access%20the%20Windows%20drives?")
I tryed to run chkdsk, but that changed nothing. I guess it might be helpful to access /var/log/Xorg.0.log but I don`t know how to.

Hope someone has suggestions.

---

### Post by Nxion on 2009-05-08
Well lets try this. Boot to Ubuntu, try to log in. When it kicks you out log in via the console.

When you get in post the output of these commands here:

```
dmesg
```

```
cat /etc/X11/xorg.conf
```

```
cat /var/log/Xorg.0.log
```

---

