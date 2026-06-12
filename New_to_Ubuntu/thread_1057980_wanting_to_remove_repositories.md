---
title: "wanting to remove repositories"
date: 2009-02-02
forum: New to Ubuntu
---

### Post by Achilles124 on 2009-02-02
I want to remove repositories from my third party software list.
I have used the remove button to delete them from the list and I have removed the authentication key.
But it didn't work. The repositories keep reappearing on the list.

After opening the terminal I run the command locate:

/etc/apt/source.list.akiradbackup
/etc/apt/sources.list.d/akirad.list
/etc/apt/sources.list.d/akirad.list.save
/etc/init.d/akiradrelease
/etc/rc0.d/K20akiradrelease
/etc/rc1.d/K20akiradrelease
/etc/rc2.d/S20akiradrelease
/etc/rc3.d/S20akiradrelease
/etc/rc4.d/S20akiradrelease
/etc/rc5.d/S20akiradrelease
/etc/rc6.d/K20akiradrelease
/usr/share/aptlists/mirror-akirad.list
/usr/share/doc/akirad-keyring
/usr/share/doc/akirad-keyring/changelog
/usr/share/doc/akirad-keyring/copyright
/usr/share/keyrings/akirad-keyring.gpg
/var/lib/dpkg/info/akirad-keyring-and-mirrors.list
/var/lib/dpkg/info/akirad-keyring-and-mirrors.postinst
/var/lib/dpkg/info/akirad-keyring-and-mirrors.prerm

What files do I have to remove?

---

### Post by taurus on 2009-02-02
Are you talking about removing the /etc/apt/sources.list.d/**akirad.list**?  Just remove it from a terminal.

Applications -> Accessories -> Terminal
```
sudo rm /etc/apt/sources.list.d/akirad.list
```

---

### Post by Achilles124 on 2009-02-02
Thank you for answering. Can I safely remove the rest of the files too?

---

