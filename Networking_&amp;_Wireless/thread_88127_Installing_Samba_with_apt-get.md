---
title: "Installing Samba with apt-get"
date: 2005-11-09
forum: Networking &amp; Wireless
---

### Post by toktok on 2005-11-09
My box is running 5.04
I'm trying to install Samba with the following command
sudo apt-get install samba

but this is what I get:
:confused: 
"Could not load file; message from server: Failed to open file."

Anybody got any ideas??? Thanks


For the complete output look here:  (sorry most of the lines are in dutch)

Pakketlijsten worden ingelezen... Klaar
Boom van vereisten wordt opgebouwd... Klaar
De volgende extra pakketten zullen geïnstalleerd worden:
  samba-common smbclient
Voorgestelde pakketten:
  samba-doc smbfs
De volgende NIEUWE pakketten zullen geïnstalleerd worden:
  samba
De volgende pakketten zullen opgewaardeerd worden:
  samba-common smbclient
2 pakketten opgewaardeerd, 1 nieuwe pakketten geïnstalleerd, 0 verwijderen en 136 niet opgewaardeerd.
Er moeten 7036kB aan archieven opgehaald worden.
Na het uitpakken zal er 6490kB extra schijfruimte gebruikt worden.
Wilt u doorgaan [J/n]? J
WAARSCHUWING: De volgende pakketten kunnen niet geauthenticeerd worden:
  smbclient samba-common samba
Wilt u deze pakketten installeren zonder verificatie [j/N]? j
Ophalen:1 [ftp://ftp2.caliu.info](ftp://ftp2.caliu.info) hoary-backports/main smbclient 3.0.14a-3ubuntu3~5.04ubp1 [2532kB]
Fout [ftp://ftp2.caliu.info](ftp://ftp2.caliu.info) hoary-backports/main smbclient 3.0.14a-3ubuntu3~5.04ubp1
  Kan bestand niet ophalen; bericht van server: Failed to open file.
Ophalen:2 [ftp://ftp2.caliu.info](ftp://ftp2.caliu.info) hoary-backports/main samba-common 3.0.14a-3ubuntu3~5.04ubp1 [1986kB]
Fout [ftp://ftp2.caliu.info](ftp://ftp2.caliu.info) hoary-backports/main samba-common 3.0.14a-3ubuntu3~5.04ubp1
  Kan bestand niet ophalen; bericht van server: Failed to open file.
Ophalen:3 [ftp://ftp2.caliu.info](ftp://ftp2.caliu.info) hoary-backports/main samba 3.0.14a-3ubuntu3~5.04ubp1 [2518kB]
Fout [ftp://ftp2.caliu.info](ftp://ftp2.caliu.info) hoary-backports/main samba 3.0.14a-3ubuntu3~5.04ubp1
  Kan bestand niet ophalen; bericht van server: Failed to open file.
Ophalen van [ftp://ftp2.caliu.info/backports/dists/hoary-backports/main/binary-i386/smbclient_3.0.14a-3ubuntu3~5.04ubp1_i386.deb](ftp://ftp2.caliu.info/backports/dists/hoary-backports/main/binary-i386/smbclient_3.0.14a-3ubuntu3~5.04ubp1_i386.deb) Kan bestand niet ophalen; bericht van server: Failed to open file. is mislukt
Ophalen van [ftp://ftp2.caliu.info/backports/dists/hoary-backports/main/binary-i386/samba-common_3.0.14a-3ubuntu3~5.04ubp1_i386.deb](ftp://ftp2.caliu.info/backports/dists/hoary-backports/main/binary-i386/samba-common_3.0.14a-3ubuntu3~5.04ubp1_i386.deb) Kan bestand niet ophalen; bericht van server: Failed to open file. is mislukt
Ophalen van [ftp://ftp2.caliu.info/backports/dists/hoary-backports/main/binary-i386/samba_3.0.14a-3ubuntu3~5.04ubp1_i386.deb](ftp://ftp2.caliu.info/backports/dists/hoary-backports/main/binary-i386/samba_3.0.14a-3ubuntu3~5.04ubp1_i386.deb) Kan bestand niet ophalen; bericht van server: Failed to open file. is mislukt
E: Kon sommige archieven niet ophalen, misschien kunt u 'apt-get update' of --fix-missing proberen?

---

### Post by aysiu on 2005-11-09
Maybe don't use the backports mirrors.
See the first link in my sig.

---

### Post by toktok on 2005-11-10
Yeah!!! it works fine now! Thanks.

---

