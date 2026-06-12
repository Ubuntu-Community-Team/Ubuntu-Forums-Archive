---
title: "Cannot remove Frostwire!!!"
date: 2010-12-12
forum: New to Ubuntu
---

### Post by thisisjay on 2010-12-12
Every piece of information on the web says to search for "Frostwire" in the package manager or to uninstall it from the terminal using the command "sudo apt-get remove frostwire".

My problem is that nothing comes up when I search for "Frostwire" and in terminal I am told that there is no such package, but I have Frostwire working, so it must be there somewhere.

---

### Post by tad1073 on 2010-12-12
open a terminl and type:
```

whereis frostwire
then type
sudo nautilus

```
then browse to those folder and delete them

---

### Post by thisisjay on 2010-12-12
dad@dad-bedroom:~$ whereis frostwire
frostwire: /usr/bin/frostwire /usr/lib/frostwire /usr/lib64/frostwire
dad@dad-bedroom:~$ sudo nautilus
[sudo] password for dad: 
Initializing nautilus-gdu extension

** (nautilus:12450): WARNING **: Failed to get the current CK session: GDBus.Error:org.freedesktop.ConsoleKit.Manager.GeneralError: Unable to lookup session information for process '12450'

(nautilus:12450): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

---

### Post by HermanAB on 2010-12-12
Howdy,

Sudo rm can delete anything...

---

