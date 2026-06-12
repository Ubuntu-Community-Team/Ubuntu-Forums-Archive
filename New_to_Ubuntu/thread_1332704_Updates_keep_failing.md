---
title: "Updates keep failing"
date: 2009-11-20
forum: New to Ubuntu
---

### Post by cmcanulty on 2009-11-20
```
GPG error: http://ppa.launchpad.net karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 8F66051A3A258030Failed to fetch cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)/dists/jaunty/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)/dists/jaunty/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch http://ppa.launchpad.net/amule-releases/ppa/ubuntu/dists/karmic/main/binary-i386/Packages.gz  404  Not Found
Failed to fetch http://ppa.launchpad.net/chmsee/jaunty/ubuntu/dists/karmic/main/binary-i386/Packages.gz  404  Not Found
Failed to fetch http://wine.budgetdedicated.com/apt/dists/karmic/main/binary-i386/Packages.gz  404  Not Found
Some index files failed to download, they have been ignored, or old ones used instead.[CODE]
```[/CODE]

Can someone give some help on why I keep getting update error messages like the above? I am running Karmic. Now I always have an orange warning triangle on the top bar, thanks

---

### Post by phillw on 2009-11-20
> **cmcanulty said:**
> ```
GPG error: http://ppa.launchpad.net karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 8F66051A3A258030Failed to fetch cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)/dists/jaunty/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)/dists/jaunty/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch http://ppa.launchpad.net/amule-releases/ppa/ubuntu/dists/karmic/main/binary-i386/Packages.gz  404  Not Found
Failed to fetch http://ppa.launchpad.net/chmsee/jaunty/ubuntu/dists/karmic/main/binary-i386/Packages.gz  404  Not Found
Failed to fetch http://wine.budgetdedicated.com/apt/dists/karmic/main/binary-i386/Packages.gz  404  Not Found
Some index files failed to download, they have been ignored, or old ones used instead.
```Can someone give some help on why I keep getting update error messages like the above? I am running Karmic. Now I always have an orange warning triangle on the top bar, thanks


Try this thread, change the key you need to the one your system is seeking.

[http://ubuntuforums.org/showthread.php?t=1332630](http://ubuntuforums.org/showthread.php?t=1332630)

Regards,

Phill.

---

### Post by wilee-nilee on 2009-11-20
You may be missing keys for confirmation, but it looks more like a need for a different repository. Go to software sources click on other in download from in the 1st tab then select best server then try the one it highlights.

---

### Post by wojox on 2009-11-20
You also need to click on other software and uncheck the cd-rom.

---

### Post by wilee-nilee on 2009-11-20
It is easy to start a double thread if you can't find the original.
[http://ubuntuforums.org/showthread.php?t=1332708](http://ubuntuforums.org/showthread.php?t=1332708)

---

