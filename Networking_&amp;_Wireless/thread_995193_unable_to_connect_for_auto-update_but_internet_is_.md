---
title: "unable to connect for auto-update but internet is ok..."
date: 2008-11-27
forum: Networking &amp; Wireless
---

### Post by Sopkip on 2008-11-27
I am unable to automatically update or refresh the list with software. I get an error :

for example

W: Ophalen van [http://archive.ubuntu.com/ubuntu/dists/intrepid/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/intrepid/Release.gpg) Kon niet verbinden met 255.255.255.0:8080 (255.255.255.0), de verbinding verliep is mislukt

W: Ophalen van [http://archive.ubuntu.com/ubuntu/dists/intrepid/main/i18n/Translation-nl.bz2](http://archive.ubuntu.com/ubuntu/dists/intrepid/main/i18n/Translation-nl.bz2) Kan niet verbinden met 255.255.255.0 8080: is mislukt

W: Ophalen van [http://archive.ubuntu.com/ubuntu/dists/intrepid/restricted/i18n/Translation-nl.bz2](http://archive.ubuntu.com/ubuntu/dists/intrepid/restricted/i18n/Translation-nl.bz2) Kan niet verbinden met 255.255.255.0 8080: is mislukt

W: Ophalen van [http://archive.ubuntu.com/ubuntu/dists/intrepid/universe/i18n/Translation-nl.bz2](http://archive.ubuntu.com/ubuntu/dists/intrepid/universe/i18n/Translation-nl.bz2) Kan niet verbinden met 255.255.255.0 8080: is mislukt

W: Ophalen van [http://archive.ubuntu.com/ubuntu/dists/intrepid/multiverse/i18n/Translation-nl.bz2](http://archive.ubuntu.com/ubuntu/dists/intrepid/multiverse/i18n/Translation-nl.bz2) Kan niet verbinden met 255.255.255.0 8080: is mislukt

W: Ophalen van [http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/Release.gpg) Kan niet verbinden met 255.255.255.0 8080: is mislukt

W: Ophalen van [http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/main/i18n/Translation-nl.bz2](http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/main/i18n/Translation-nl.bz2) Kan niet verbinden met 255.255.255.0 8080: is mislukt

W: Ophalen van [http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/restricted/i18n/Translation-nl.bz2](http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/restricted/i18n/Translation-nl.bz2) Kan niet verbinden met 255.255.255.0 8080: is mislukt

W: Ophalen van [http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/universe/i18n/Translation-nl.bz2](http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/universe/i18n/Translation-nl.bz2) Kan niet verbinden met 255.255.255.0 8080: is mislukt

W: Ophalen van [http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/multiverse/i18n/Translation-nl.bz2](http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/multiverse/i18n/Translation-nl.bz2) Kan niet verbinden met 255.255.255.0 8080: is mislukt

W: Ophalen van [http://archive.ubuntu.com/ubuntu/dists/intrepid-security/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/intrepid-security/Release.gpg) Kan niet verbinden met 255.255.255.0 8080: is mislukt

W: Ophalen van [http://archive.ubuntu.com/ubuntu/dists/intrepid-security/main/i18n/Translation-nl.bz2](http://archive.ubuntu.com/ubuntu/dists/intrepid-security/main/i18n/Translation-nl.bz2) Kan niet verbinden met 255.255.255.0 8080: is mislukt

W: Ophalen van [http://archive.ubuntu.com/ubuntu/dists/intrepid-security/restricted/i18n/Translation-nl.bz2](http://archive.ubuntu.com/ubuntu/dists/intrepid-security/restricted/i18n/Translation-nl.bz2) Kan niet verbinden met 255.255.255.0 8080: is mislukt

W: Ophalen van [http://archive.ubuntu.com/ubuntu/dists/intrepid-security/universe/i18n/Translation-nl.bz2](http://archive.ubuntu.com/ubuntu/dists/intrepid-security/universe/i18n/Translation-nl.bz2) Kan niet verbinden met 255.255.255.0 8080: is mislukt

W: Ophalen van [http://archive.ubuntu.com/ubuntu/dists/intrepid-security/multiverse/i18n/Translation-nl.bz2](http://archive.ubuntu.com/ubuntu/dists/intrepid-security/multiverse/i18n/Translation-nl.bz2) Kan niet verbinden met 255.255.255.0 8080: is mislukt

W: Ophalen van [http://wine.budgetdedicated.com/apt/dists/intrepid/Release.gpg](http://wine.budgetdedicated.com/apt/dists/intrepid/Release.gpg) Kon niet verbinden met 255.255.255.0:8080 (255.255.255.0), de verbinding verliep is mislukt

W: Ophalen van [http://wine.budgetdedicated.com/apt/dists/intrepid/main/i18n/Translation-nl.bz2](http://wine.budgetdedicated.com/apt/dists/intrepid/main/i18n/Translation-nl.bz2) Kan niet verbinden met 255.255.255.0 8080: is mislukt

W: Ophalen van sommige indexbestanden is mislukt, deze zijn of genegeerd, of er zijn oudere versies van gebruikt.

I can access the internet without problem but cannot remove this 255.255.255.0 address to have the system use the active and working internet connecting (wireless)

Anybody any idea? mail me or respond to the thread , 

Many thanks!!!

---

### Post by frankleeee on 2008-11-27
Go to software sources in system administration and change the server, to see if this is the problem. Also check to see if the cd portion on the same screen is ticked off.

---

### Post by Sopkip on 2008-11-30
Many thanks but I still get the same error after changing the server:

W: Ophalen van [http://ftp.tiscali.nl/ubuntu/dists/intrepid/Release.gpg](http://ftp.tiscali.nl/ubuntu/dists/intrepid/Release.gpg) Kon niet verbinden met 255.255.255.0:8080 (255.255.255.0), de verbinding verliep is mislukt

W: Ophalen van [http://ftp.tiscali.nl/ubuntu/dists/intrepid/main/i18n/Translation-nl.bz2](http://ftp.tiscali.nl/ubuntu/dists/intrepid/main/i18n/Translation-nl.bz2) Kan niet verbinden met 255.255.255.0 8080: is mislukt

W: Ophalen van [http://ftp.tiscali.nl/ubuntu/dists/intrepid/restricted/i18n/Translation-nl.bz2](http://ftp.tiscali.nl/ubuntu/dists/intrepid/restricted/i18n/Translation-nl.bz2) Kan niet verbinden met 255.255.255.0 8080: is mislukt

W: Ophalen van [http://ftp.tiscali.nl/ubuntu/dists/intrepid/universe/i18n/Translation-nl.bz2](http://ftp.tiscali.nl/ubuntu/dists/intrepid/universe/i18n/Translation-nl.bz2) Kan niet verbinden met 255.255.255.0 8080: is mislukt

W: Ophalen van [http://ftp.tiscali.nl/ubuntu/dists/intrepid/multiverse/i18n/Translation-nl.bz2](http://ftp.tiscali.nl/ubuntu/dists/intrepid/multiverse/i18n/Translation-nl.bz2) Kan niet verbinden met 255.255.255.0 8080: is mislukt

W: Ophalen van [http://ftp.tiscali.nl/ubuntu/dists/intrepid-updates/Release.gpg](http://ftp.tiscali.nl/ubuntu/dists/intrepid-updates/Release.gpg) Kan niet verbinden met 255.255.255.0 8080: is mislukt

W: Ophalen van [http://ftp.tiscali.nl/ubuntu/dists/intrepid-updates/main/i18n/Translation-nl.bz2](http://ftp.tiscali.nl/ubuntu/dists/intrepid-updates/main/i18n/Translation-nl.bz2) Kan niet verbinden met 255.255.255.0 8080: is mislukt

W: Ophalen van [http://ftp.tiscali.nl/ubuntu/dists/intrepid-updates/restricted/i18n/Translation-nl.bz2](http://ftp.tiscali.nl/ubuntu/dists/intrepid-updates/restricted/i18n/Translation-nl.bz2) Kan niet verbinden met 255.255.255.0 8080: is mislukt

W: Ophalen van [http://ftp.tiscali.nl/ubuntu/dists/intrepid-updates/universe/i18n/Translation-nl.bz2](http://ftp.tiscali.nl/ubuntu/dists/intrepid-updates/universe/i18n/Translation-nl.bz2) Kan niet verbinden met 255.255.255.0 8080: is mislukt

W: Ophalen van [http://ftp.tiscali.nl/ubuntu/dists/intrepid-updates/multiverse/i18n/Translation-nl.bz2](http://ftp.tiscali.nl/ubuntu/dists/intrepid-updates/multiverse/i18n/Translation-nl.bz2) Kan niet verbinden met 255.255.255.0 8080: is mislukt

W: Ophalen van [http://ftp.tiscali.nl/ubuntu/dists/intrepid-security/Release.gpg](http://ftp.tiscali.nl/ubuntu/dists/intrepid-security/Release.gpg) Kan niet verbinden met 255.255.255.0 8080: is mislukt

W: Ophalen van [http://ftp.tiscali.nl/ubuntu/dists/intrepid-security/main/i18n/Translation-nl.bz2](http://ftp.tiscali.nl/ubuntu/dists/intrepid-security/main/i18n/Translation-nl.bz2) Kan niet verbinden met 255.255.255.0 8080: is mislukt

W: Ophalen van [http://ftp.tiscali.nl/ubuntu/dists/intrepid-security/restricted/i18n/Translation-nl.bz2](http://ftp.tiscali.nl/ubuntu/dists/intrepid-security/restricted/i18n/Translation-nl.bz2) Kan niet verbinden met 255.255.255.0 8080: is mislukt

W: Ophalen van [http://ftp.tiscali.nl/ubuntu/dists/intrepid-security/universe/i18n/Translation-nl.bz2](http://ftp.tiscali.nl/ubuntu/dists/intrepid-security/universe/i18n/Translation-nl.bz2) Kan niet verbinden met 255.255.255.0 8080: is mislukt

W: Ophalen van [http://ftp.tiscali.nl/ubuntu/dists/intrepid-security/multiverse/i18n/Translation-nl.bz2](http://ftp.tiscali.nl/ubuntu/dists/intrepid-security/multiverse/i18n/Translation-nl.bz2) Kan niet verbinden met 255.255.255.0 8080: is mislukt

W: Ophalen van [http://wine.budgetdedicated.com/apt/dists/intrepid/Release.gpg](http://wine.budgetdedicated.com/apt/dists/intrepid/Release.gpg) Kon niet verbinden met 255.255.255.0:8080 (255.255.255.0), de verbinding verliep is mislukt

W: Ophalen van [http://wine.budgetdedicated.com/apt/dists/intrepid/main/i18n/Translation-nl.bz2](http://wine.budgetdedicated.com/apt/dists/intrepid/main/i18n/Translation-nl.bz2) Kan niet verbinden met 255.255.255.0 8080: is mislukt

W: Ophalen van sommige indexbestanden is mislukt, deze zijn of genegeerd, of er zijn oudere versies van gebruikt.

Any further idea's?

Thanks

---

### Post by Sopkip on 2008-11-30
I got it to work. I pushed a button Apply System wide concerning the network options. Many thanks for your help!:)

---

