---
title: "patching rtl8187 + aircrack"
date: 2007-08-16
forum: Networking &amp; Wireless
---

### Post by salvatore001 on 2007-08-16
hi

i installed xubuntu and trying to get the r8187 patched module to work following these instructions

[http://www.aircrack-ng.org/doku.php?id=r8187&DokuWiki=735177530b674cc6ca5632ac62f4dbbd]("http://www.aircrack-ng.org/doku.php?id=r8187&DokuWiki=735177530b674cc6ca5632ac62f4dbbd")

i accomplished all the steps above withouth problems but when i modprobe the modules i get the 'unknow symbol in module, or unknown parameter' error


i already tried this

```
cd beta-8187
rm -f Modules.symvers
ln -s ../ieee80211/Modules.symvers Modules.symvers
### NOTE versions of GCC may require this instead: ln -s ../ieee80211/Module.symvers Module.symvers
cd ..
sh makedrvbk
```

but still get the same error
can you help me with this one?

kernel installed is 2.6.20-16-generic

thanks

---

### Post by salvatore001 on 2007-08-22
anyone? :(

---

