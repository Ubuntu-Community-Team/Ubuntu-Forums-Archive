---
title: "strange error message for nautilus"
date: 2010-10-19
forum: New to Ubuntu
---

### Post by rcbinwi on 2010-10-19
I'm running 9.10 on a Dell Inspiron e1405.  Since I upgraded to 9.10 over the weekend, some strange things have been happening.  This is one of them.

When I run sudo nautilus, it runs.  But I get the following error message:
```
(nautilus:2707): Eel-CRITICAL **: eel_preferences_get_boolean: assertion `preferences_is_initialized ()' failed
richard@richard-laptop:~$ sudo nautilus

(nautilus:2719): Eel-CRITICAL **: eel_preferences_get_boolean: assertion `preferences_is_initialized ()' failed

** (nautilus:2719): WARNING **: No marshaller for signature of signal 'UploadFinished'

** (nautilus:2719): WARNING **: No marshaller for signature of signal 'DownloadFinished'

** (nautilus:2719): WARNING **: No marshaller for signature of signal 'ShareCreateError'
Initializing nautilus-gdu extension
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

```

Can someone explain this?

---

### Post by robsoles on 2010-10-19
I think those errors relate to something you've installed, like a download manager - I'd feel foolish to try to explain it beyond that without more info.

I would like to advise you to use```
gksudo 'nautilus --no-desktop'
``` and pretty much ignore error messages if a nautilus window happens to open as root with root permissions.

The terminal in which the command is executed may appear to 'hang' after you close the copy of nautilus that opens for the command but just press [CTRL]+[C] with the terminal focussed and it should become responsive again.

HTH

---

