---
title: "can't fix broken packages"
date: 2009-01-25
forum: New to Ubuntu
---

### Post by Shay Andrews on 2009-01-25
I got a notice about broken packages after updating to Intrepid Ibex. Trying to fix them with the package manager yields these errors:

E: /var/cache/apt/archives/libcupsimage2_1.3.9-2ubuntu6.1_i386.deb: subprocess dpkg-deb --fsys-tarfile returned error exit status 2
E: /var/cache/apt/archives/openoffice.org-common_1%3a2.4.1-11ubuntu2.1_all.deb: short read in buffer_copy (backend dpkg-deb during `./usr/lib/openoffice/share/gallery/sounds/space2.wav')
E: /var/cache/apt/archives/openssl_0.9.8g-10.1ubuntu2.1_i386.deb: short read in buffer_copy (backend dpkg-deb during `./usr/bin/openssl')
E: /var/cache/apt/archives/audacious-plugins_1.5.1-2ubuntu2_i386.deb: short read in buffer_copy (backend dpkg-deb during `./usr/lib/audacious/Input/aac.so')
E: /var/cache/apt/archives/hplip_2.8.7-0ubuntu6_i386.deb: subprocess dpkg-deb --fsys-tarfile returned error exit status 2
E: /var/cache/apt/archives/hplip-data_2.8.7-0ubuntu6_all.deb: short read in buffer_copy (backend dpkg-deb during `./usr/share/hplip/base/vcard.py')
E: /var/cache/apt/archives/cups-common_1.3.9-2ubuntu6.1_all.deb: short read in buffer_copy (backend dpkg-deb during `./usr/share/cups/charmaps/euc-tw.txt')
E: /var/cache/apt/archives/evolution-exchange_2.24.2-0ubuntu1_i386.deb: short read in buffer_copy (backend dpkg-deb during `./usr/share/gtk-doc/html/evolution-exchange/ximian-connector-delegation.html')
E: /var/cache/apt/archives/evolution_2.24.2-0ubuntu1_i386.deb: conflicting packages - not installing evolution

What should I do?

---

### Post by taurus on 2009-01-25
Try

```
sudo apt-get clean
sudo apt-get -f install
sudo dpkg --config -a
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by Shay Andrews on 2009-01-25
I got through the second command, but then it gives me

Errors were encountered while processing:
 linux-image-2.6.24-21-generic
 linux-ubuntu-modules-2.6.24-21-generic
 linux-restricted-modules-2.6.24-21-generic
 brltty
 brltty-x11
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by MaindotC on 2009-02-17
Having the same problem with open-jdk-6-jre and some other packages...

---

