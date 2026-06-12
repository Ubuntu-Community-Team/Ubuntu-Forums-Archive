---
title: "Corrupt Header"
date: 2010-03-06
forum: New to Ubuntu
---

### Post by Commisar Jimp on 2010-03-06
Hi
for the last week, every time I install an automatic update, I get this error message:
> E: /var/cache/apt/archives/linux-headers-2.6.31-20_2.6.31-20.57_all.deb: corrupted filesystem tarfile - corrupted package archive
because of this, some of the updates won't apply. I went to synaptic, and ran a "broken" filter, then found the corrupt headers and tried to reinstall them, but I got the same error message. Because of this problem I have been unable to install some security updates, does anyone know what I should do?

---

### Post by Bachstelze on 2010-03-06
Try

```
sudo rm /var/cache/apt/archives/linux-headers-2.6.31-20_2.6.31-20.57_all.deb
sudo apt-get -f install
```

---

### Post by PFN on 2010-03-06
Open a Terminal and run:
```
sudo apt-cache clean
```
and enter your password when prompt.
Then try to reinstall the broken packages.
Hope this may help.

---

