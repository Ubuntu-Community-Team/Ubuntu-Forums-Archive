---
title: "Thunderbird"
date: 2009-11-15
forum: New to Ubuntu
---

### Post by UlleG on 2009-11-15
Hi,

Just installed Ubuntu 9.10 and everything went fine except the Thunderbird installation.

After first install it seemed fine. I started to insert the first to user accounts, tried to download messages, closed the program, reopened and Thunderbird turned gray and froze.

Used Ubunto Software Center to uninstall and reinstall...several times same outcome. 
I know, I could use somekind of other email application but I am kind of stubborn on this.

Anybody any ideas? The former edited user accounts are maybe still around and mess the new installation up?

---

### Post by mad-kow on 2009-11-15
To remove thunderbird and all configuration files type:

```
sudo apt-get remove --purge thunderbird
```

To remove all profiles just delete or move the .mozilla-thunderbird folder in your home directory.

```
mv ~/.mozilla-thunderbird ~/.mozilla-thunderbird.old
```

---

### Post by UlleG on 2009-11-15
Ok, tried that and after reinstall same problem.

Thunderbird tries to start up and aborts itself after some seconds. Second try to start after that, Thunderbird opens and freezes.

---

### Post by UlleG on 2009-11-17
Hi,

attached the startup procedure from Thunderbird. Thried to start Thunderbird two times without success.

Hope someone finds a reason.

---

### Post by UlleG on 2009-11-17
Deleted .mozilla-thunderbird manually, now Thunderbird starts again.

---

