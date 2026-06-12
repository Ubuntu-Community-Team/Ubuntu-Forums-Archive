---
title: "Virtualbox-ose-guest-source on 8.10 fails"
date: 2008-12-15
forum: New to Ubuntu
---

### Post by skajotde on 2008-12-15
Hi 

First I checked google and Ubuntu Forums for two days. There are solutions for not-ose virtualbox and for Ubuntu 8.04 but I dont find solution on Ubuntu 8.10.

I try install virtualbox-ose on Ubuntu 8.10. VirtualBox runs windows XP successful ;> but there is problem with virtualbox-ose-guest-utils as seen below so shared folders doesn't work.

 * VirtualBox Additions Disabled, not in a Virtual Machine...  

```
demecki@kde:/rg/dev/instalacja-linux/01-virtualbox$ sudo apt-get install  virtualbox-ose virtualbox-ose-source virtualbox-ose-guest-utils virtualbox-ose-guest-source
Czytanie list pakietów... Gotowe
Budowanie drzewa zale&#380;no&#347;ci       
Odczyt informacji o stanie... Gotowe
Polecane pakiety:
  virtualbox-ose-guest-modules
Zostan&#261; zainstalowane nast&#281;puj&#261;ce NOWE pakiety:
  virtualbox-ose virtualbox-ose-guest-source virtualbox-ose-guest-utils virtualbox-ose-source
0 aktualizowanych, 4 nowo instalowanych, 0 usuwanych i 0 nieaktualizowanych.
Konieczne pobranie 0B/7802kB archiwów.
Po tej operacji zostanie dodatkowo u&#380;yte 28,1MB miejsca na dysku.
Zaznaczenie poprzednio niezaznaczonego pakietu virtualbox-ose.
(Odczytywanie bazy danych ... 117949 plików i katalogów obecnie zainstalowanych.)
Rozpakowanie virtualbox-ose (z .../virtualbox-ose_2.0.4-dfsg-0ubuntu1_amd64.deb) ...
Zaznaczenie poprzednio niezaznaczonego pakietu virtualbox-ose-source.
Rozpakowanie virtualbox-ose-source (z .../virtualbox-ose-source_2.0.4-dfsg-0ubuntu1_all.deb) ...
Zaznaczenie poprzednio niezaznaczonego pakietu virtualbox-ose-guest-source.
Rozpakowanie virtualbox-ose-guest-source (z .../virtualbox-ose-guest-source_2.0.4-dfsg-0ubuntu1_all.deb) ...
Zaznaczenie poprzednio niezaznaczonego pakietu virtualbox-ose-guest-utils.
Rozpakowanie virtualbox-ose-guest-utils (z .../virtualbox-ose-guest-utils_2.0.4-dfsg-0ubuntu1_amd64.deb) ...
Przetwarzanie wyzwalaczy dla menu...
Konfigurowanie virtualbox-ose (2.0.4-dfsg-0ubuntu1) ...
Starting VirtualBox host networking * Starting VirtualBox kernel module vboxdrv                                                      
 * No suitable module for running kernel found.

Konfigurowanie virtualbox-ose-source (2.0.4-dfsg-0ubuntu1) ...
 * Reloading kernel event manager...                                                                                          [ OK ] 
Adding Module to DKMS build system
Doing initial module build
Installing initial module
Done.
 * Stopping VirtualBox kernel module vboxdrv                                                                                  [ OK ] 
 * Starting VirtualBox kernel module vboxdrv                                                                                  [ OK ] 

Konfigurowanie virtualbox-ose-guest-source (2.0.4-dfsg-0ubuntu1) ...
 * Reloading kernel event manager...                                                                                          [ OK ] 
Adding Module to DKMS build system
Doing initial module build

Error! Bad return status for module build on kernel: 2.6.27-9-generic (x86_64)
Consult the make.log in the build directory
/var/lib/dkms/virtualbox-ose-guest/2.0.4/build/ for more information.
Installing initial module

Error! Could not locate vboxadd.ko for module virtualbox-ose-guest in the DKMS tree.
You must run a dkms build for kernel 2.6.27-9-generic (x86_64) first.
Done.
invoke-rc.d: unknown initscript, /etc/init.d/virtualbox-ose-guest-utils not found.

Konfigurowanie virtualbox-ose-guest-utils (2.0.4-dfsg-0ubuntu1) ...
 * VirtualBox Additions Disabled, not in a Virtual Machine...                                                                 [fail] 

Przetwarzanie wyzwalaczy dla menu...
```

I appreciate any help
Thanks.

---

### Post by skajotde on 2008-12-15
I have found that sharing by windows network works, so typing \\komp_name give access to folders. Earlier I tried \\vboxsvr but it didn't work even on sun binaries (sudo apt-get install virtualbox-2.0)

Problem with Virtualbox-ose-guest-source is all the time, but for me sharing is ok via windows network.

---

### Post by Colin@oxford on 2009-03-31
This still appears to be the case.  Guest additions are not found when I attempt to load them into my virtual XP machine.  Following a disk crash, my machine now has 8.10 on it and I can't get the guest additions to work.  Previously I had 8.04 and all worked very well. Does anyone know anything about this?

---

### Post by card_ace on 2009-04-01
did you download virtualbox from the repositories?  if so then shared folders between hosts and guests don't work.  i had this same problem.  go to the virtualbox website and download it through there if you want to be able to access your ubuntu documents in your virtual XP.  heres a link to the linux distro download area of the site.

[http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)

good luck!

---

### Post by Colin@oxford on 2009-04-01
Yes, that is what I did eventually. This is annoying because I would prefer to stick to Open Source code.  The version on Hardy worked OK - something appears to be amiss with the guest additions for the OSE version.

---

