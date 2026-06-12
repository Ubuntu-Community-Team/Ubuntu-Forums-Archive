---
title: "apt-get update with errors (ver 8.04)"
date: 2009-09-28
forum: New to Ubuntu
---

### Post by condor uruguay on 2009-09-28
hi i got problems when i want to install some programs. I put:

**sudo apt-get update**

Ign cdrom://Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1) hardy/main Translation-es
Ign cdrom://Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1) hardy/restricted Translation-es
Err [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg                      
  No pude resolver 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-es              
  No pude resolver 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Translation-es        
  No pude resolver 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Translation-es          
  No pude resolver 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Translation-es        
  No pude resolver 'security.ubuntu.com'
Err [http://uy.archive.ubuntu.com](http://uy.archive.ubuntu.com) hardy Release.gpg                             
  No pude resolver 'uy.archive.ubuntu.com'
Err [http://uy.archive.ubuntu.com](http://uy.archive.ubuntu.com) hardy/main Translation-es                     
  No pude resolver 'uy.archive.ubuntu.com'
Err [http://uy.archive.ubuntu.com](http://uy.archive.ubuntu.com) hardy/restricted Translation-es       
  No pude resolver 'uy.archive.ubuntu.com'
Err [http://uy.archive.ubuntu.com](http://uy.archive.ubuntu.com) hardy/universe Translation-es         
  No pude resolver 'uy.archive.ubuntu.com'
Err [http://uy.archive.ubuntu.com](http://uy.archive.ubuntu.com) hardy/multiverse Translation-es       
  No pude resolver 'uy.archive.ubuntu.com'
Err [http://uy.archive.ubuntu.com](http://uy.archive.ubuntu.com) hardy-updates Release.gpg             
  No pude resolver 'uy.archive.ubuntu.com'
Err [http://uy.archive.ubuntu.com](http://uy.archive.ubuntu.com) hardy-updates/main Translation-es             
  No pude resolver 'uy.archive.ubuntu.com'
Err [http://uy.archive.ubuntu.com](http://uy.archive.ubuntu.com) hardy-updates/restricted Translation-es       
  No pude resolver 'uy.archive.ubuntu.com'
Err [http://uy.archive.ubuntu.com](http://uy.archive.ubuntu.com) hardy-updates/universe Translation-es         
  No pude resolver 'uy.archive.ubuntu.com'
Err [http://uy.archive.ubuntu.com](http://uy.archive.ubuntu.com) hardy-updates/multiverse Translation-es       
  No pude resolver 'uy.archive.ubuntu.com'
Err [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid Release.gpg                         
  No pude resolver 'packages.medibuntu.org'
Err [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/free Translation-es         
  No pude resolver 'packages.medibuntu.org'
Err [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/non-free Translation-es
  No pude resolver 'packages.medibuntu.org'
Err [http://lgp203.free.fr](http://lgp203.free.fr) hardy Release.gpg
  No pude resolver 'lgp203.free.fr'
Err [http://lgp203.free.fr](http://lgp203.free.fr) hardy/universe Translation-es
  No pude resolver 'lgp203.free.fr'
Leyendo lista de paquetes... Hecho
W: Imposible obtener [http://uy.archive.ubuntu.com/ubuntu/dists/hardy/Release.gpg](http://uy.archive.ubuntu.com/ubuntu/dists/hardy/Release.gpg)  No pude resolver 'uy.archive.ubuntu.com'

W: Imposible obtener [http://uy.archive.ubuntu.com/ubuntu/dists/hardy/main/i18n/Translation-es.bz2](http://uy.archive.ubuntu.com/ubuntu/dists/hardy/main/i18n/Translation-es.bz2)  No pude resolver 'uy.archive.ubuntu.com'

W: Imposible obtener [http://uy.archive.ubuntu.com/ubuntu/dists/hardy/restricted/i18n/Translation-es.bz2](http://uy.archive.ubuntu.com/ubuntu/dists/hardy/restricted/i18n/Translation-es.bz2)  No pude resolver 'uy.archive.ubuntu.com'

W: Imposible obtener [http://uy.archive.ubuntu.com/ubuntu/dists/hardy/universe/i18n/Translation-es.bz2](http://uy.archive.ubuntu.com/ubuntu/dists/hardy/universe/i18n/Translation-es.bz2)  No pude resolver 'uy.archive.ubuntu.com'

W: Imposible obtener [http://uy.archive.ubuntu.com/ubuntu/dists/hardy/multiverse/i18n/Translation-es.bz2](http://uy.archive.ubuntu.com/ubuntu/dists/hardy/multiverse/i18n/Translation-es.bz2)  No pude resolver 'uy.archive.ubuntu.com'

W: Imposible obtener [http://uy.archive.ubuntu.com/ubuntu/dists/hardy-updates/Release.gpg](http://uy.archive.ubuntu.com/ubuntu/dists/hardy-updates/Release.gpg)  No pude resolver 'uy.archive.ubuntu.com'

W: Imposible obtener [http://uy.archive.ubuntu.com/ubuntu/dists/hardy-updates/main/i18n/Translation-es.bz2](http://uy.archive.ubuntu.com/ubuntu/dists/hardy-updates/main/i18n/Translation-es.bz2)  No pude resolver 'uy.archive.ubuntu.com'

W: Imposible obtener [http://uy.archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/i18n/Translation-es.bz2](http://uy.archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/i18n/Translation-es.bz2)  No pude resolver 'uy.archive.ubuntu.com'

W: Imposible obtener [http://uy.archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/i18n/Translation-es.bz2](http://uy.archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/i18n/Translation-es.bz2)  No pude resolver 'uy.archive.ubuntu.com'

W: Imposible obtener [http://uy.archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/i18n/Translation-es.bz2](http://uy.archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/i18n/Translation-es.bz2)  No pude resolver 'uy.archive.ubuntu.com'

W: Imposible obtener [http://security.ubuntu.com/ubuntu/dists/hardy-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/hardy-security/Release.gpg)  No pude resolver 'security.ubuntu.com'

W: Imposible obtener [http://security.ubuntu.com/ubuntu/dists/hardy-security/main/i18n/Translation-es.bz2](http://security.ubuntu.com/ubuntu/dists/hardy-security/main/i18n/Translation-es.bz2)  No pude resolver 'security.ubuntu.com'

W: Imposible obtener [http://security.ubuntu.com/ubuntu/dists/hardy-security/restricted/i18n/Translation-es.bz2](http://security.ubuntu.com/ubuntu/dists/hardy-security/restricted/i18n/Translation-es.bz2)  No pude resolver 'security.ubuntu.com'

W: Imposible obtener [http://security.ubuntu.com/ubuntu/dists/hardy-security/universe/i18n/Translation-es.bz2](http://security.ubuntu.com/ubuntu/dists/hardy-security/universe/i18n/Translation-es.bz2)  No pude resolver 'security.ubuntu.com'

W: Imposible obtener [http://security.ubuntu.com/ubuntu/dists/hardy-security/multiverse/i18n/Translation-es.bz2](http://security.ubuntu.com/ubuntu/dists/hardy-security/multiverse/i18n/Translation-es.bz2)  No pude resolver 'security.ubuntu.com'

W: Imposible obtener [http://lgp203.free.fr/ubuntu/dists/hardy/Release.gpg](http://lgp203.free.fr/ubuntu/dists/hardy/Release.gpg)  No pude resolver 'lgp203.free.fr'

W: Imposible obtener [http://lgp203.free.fr/ubuntu/dists/hardy/universe/i18n/Translation-es.bz2](http://lgp203.free.fr/ubuntu/dists/hardy/universe/i18n/Translation-es.bz2)  No pude resolver 'lgp203.free.fr'

W: Imposible obtener [http://packages.medibuntu.org/dists/intrepid/Release.gpg](http://packages.medibuntu.org/dists/intrepid/Release.gpg)  No pude resolver 'packages.medibuntu.org'

W: Imposible obtener [http://packages.medibuntu.org/dists/intrepid/free/i18n/Translation-es.bz2](http://packages.medibuntu.org/dists/intrepid/free/i18n/Translation-es.bz2)  No pude resolver 'packages.medibuntu.org'

W: Imposible obtener [http://packages.medibuntu.org/dists/intrepid/non-free/i18n/Translation-es.bz2](http://packages.medibuntu.org/dists/intrepid/non-free/i18n/Translation-es.bz2)  No pude resolver 'packages.medibuntu.org'

W: Algunos archivos de índice no se han podido descargar, se han ignorado,
o se ha utilizado unos antiguos en su lugar.
W: Duplicate sources.list entry [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/free Packages (/var/lib/apt/lists/packages.medibuntu.org_dists_intrepid_free_binary-i386_Packages)
W: Duplicate sources.list entry [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/non-free Packages (/var/lib/apt/lists/packages.medibuntu.org_dists_intrepid_non-free_binary-i386_Packages)
W: Tal vez quiera ejecutar 'apt-get update' para corregir estos problemas

This not solve the problem
**sudo apt-get -f update**

**Here is mi sources.list**

# deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/ hardy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1)]/ hardy main restricted
deb [http://uy.archive.ubuntu.com/ubuntu/](http://uy.archive.ubuntu.com/ubuntu/) hardy main restricted
deb-src [http://uy.archive.ubuntu.com/ubuntu/](http://uy.archive.ubuntu.com/ubuntu/) hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://uy.archive.ubuntu.com/ubuntu/](http://uy.archive.ubuntu.com/ubuntu/) hardy-updates main restricted
deb-src [http://uy.archive.ubuntu.com/ubuntu/](http://uy.archive.ubuntu.com/ubuntu/) hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://uy.archive.ubuntu.com/ubuntu/](http://uy.archive.ubuntu.com/ubuntu/) hardy universe
deb-src [http://uy.archive.ubuntu.com/ubuntu/](http://uy.archive.ubuntu.com/ubuntu/) hardy universe
deb [http://uy.archive.ubuntu.com/ubuntu/](http://uy.archive.ubuntu.com/ubuntu/) hardy-updates universe
deb-src [http://uy.archive.ubuntu.com/ubuntu/](http://uy.archive.ubuntu.com/ubuntu/) hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://uy.archive.ubuntu.com/ubuntu/](http://uy.archive.ubuntu.com/ubuntu/) hardy multiverse
deb-src [http://uy.archive.ubuntu.com/ubuntu/](http://uy.archive.ubuntu.com/ubuntu/) hardy multiverse
deb [http://uy.archive.ubuntu.com/ubuntu/](http://uy.archive.ubuntu.com/ubuntu/) hardy-updates multiverse
deb-src [http://uy.archive.ubuntu.com/ubuntu/](http://uy.archive.ubuntu.com/ubuntu/) hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://uy.archive.ubuntu.com/ubuntu/](http://uy.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
# deb-src [http://uy.archive.ubuntu.com/ubuntu/](http://uy.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse

## Code::Block sources
deb [http://lgp203.free.fr/ubuntu/](http://lgp203.free.fr/ubuntu/) hardy universe

## ojo, comente los repositos gutsy

## Repository for codeblocks IDE and wxWidgets 2.8.6
## Note: from revision 4592, the nightly builds will depend/based upon wxWidgets 2.8.6.
## deb [http://lgp203.free.fr/ubuntu/](http://lgp203.free.fr/ubuntu/) gutsy  universe
## deb [http://apt.wxwidgets.org/](http://apt.wxwidgets.org/) gutsy-wx main

## ESSENTIAL PACKAGES (multimedia & video) (los agrege yo)
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) intrepid free non-free
deb-src [http://packages.medibuntu.org/](http://packages.medibuntu.org/) intrepid free non-free

Sorry for my english and the huge problem.
By the way , i tried to install eclipse and mysql.

thanks !

---

### Post by jerrrys on 2009-09-28
comment out (#) this line in your sources list

deb cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1)]/ hardy main restricted

---

### Post by condor uruguay on 2009-09-28
thanks, i try this:
deb cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1)]/ hardy main restricted 

give this now:

Ign cdrom://Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423) hardy Release.gpg
Ign cdrom://Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423) hardy/main Translation-es
Ign cdrom://Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423) hardy/restricted Translation-es
Ign cdrom://Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1) hardy/main Translation-es            
Ign cdrom://Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1) hardy/restricted Translation-es      
Ign cdrom://Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423) hardy Release                            
Ign cdrom://Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423) hardy/main Packages                      
Ign cdrom://Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423) hardy/restricted Packages                                                      
Err cdrom://Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423) hardy/main Packages                                                                         
  Por favor utilice apt-cdrom para hacer que APT reconozca este CD. apt-get update  no se puede usar para agregar nuevos CDs
Err cdrom://Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423) hardy/restricted Packages                                                                   
  Por favor utilice apt-cdrom para hacer que APT reconozca este CD. apt-get update  no se puede usar para agregar nuevos CDs
Err [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg                                                                                                   
  No pude resolver 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-es                                                                              
  No pude resolver 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Translation-es                                     
  No pude resolver 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Translation-es                                       
  No pude resolver 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Translation-es                                     
  No pude resolver 'security.ubuntu.com'
Err [http://lgp203.free.fr](http://lgp203.free.fr) hardy Release.gpg                                                                 
  No pude resolver 'lgp203.free.fr'
Err [http://lgp203.free.fr](http://lgp203.free.fr) hardy/universe Translation-es                                                     
  No pude resolver 'lgp203.free.fr'
Err [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid Release.gpg                        
  No pude resolver 'packages.medibuntu.org'
Err [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/free Translation-es                
  No pude resolver 'packages.medibuntu.org'
Err [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/non-free Translation-es
  No pude resolver 'packages.medibuntu.org'
Err [http://uy.archive.ubuntu.com](http://uy.archive.ubuntu.com) hardy Release.gpg
  No pude resolver 'uy.archive.ubuntu.com'
Err [http://uy.archive.ubuntu.com](http://uy.archive.ubuntu.com) hardy/main Translation-es
  No pude resolver 'uy.archive.ubuntu.com'
Err [http://uy.archive.ubuntu.com](http://uy.archive.ubuntu.com) hardy/restricted Translation-es
  No pude resolver 'uy.archive.ubuntu.com'
Err [http://uy.archive.ubuntu.com](http://uy.archive.ubuntu.com) hardy/universe Translation-es
  No pude resolver 'uy.archive.ubuntu.com'
Err [http://uy.archive.ubuntu.com](http://uy.archive.ubuntu.com) hardy/multiverse Translation-es
  No pude resolver 'uy.archive.ubuntu.com'
Err [http://uy.archive.ubuntu.com](http://uy.archive.ubuntu.com) hardy-updates Release.gpg
  No pude resolver 'uy.archive.ubuntu.com'
Err [http://uy.archive.ubuntu.com](http://uy.archive.ubuntu.com) hardy-updates/main Translation-es
  No pude resolver 'uy.archive.ubuntu.com'
Err [http://uy.archive.ubuntu.com](http://uy.archive.ubuntu.com) hardy-updates/restricted Translation-es
  No pude resolver 'uy.archive.ubuntu.com'
Err [http://uy.archive.ubuntu.com](http://uy.archive.ubuntu.com) hardy-updates/universe Translation-es
  No pude resolver 'uy.archive.ubuntu.com'
Err [http://uy.archive.ubuntu.com](http://uy.archive.ubuntu.com) hardy-updates/multiverse Translation-es
  No pude resolver 'uy.archive.ubuntu.com'
Leyendo lista de paquetes... Hecho
W: Imposible obtener [http://uy.archive.ubuntu.com/ubuntu/dists/hardy/Release.gpg](http://uy.archive.ubuntu.com/ubuntu/dists/hardy/Release.gpg)  No pude resolver 'uy.archive.ubuntu.com'

W: Imposible obtener [http://uy.archive.ubuntu.com/ubuntu/dists/hardy/main/i18n/Translation-es.bz2](http://uy.archive.ubuntu.com/ubuntu/dists/hardy/main/i18n/Translation-es.bz2)  No pude resolver 'uy.archive.ubuntu.com'

W: Imposible obtener [http://uy.archive.ubuntu.com/ubuntu/dists/hardy/restricted/i18n/Translation-es.bz2](http://uy.archive.ubuntu.com/ubuntu/dists/hardy/restricted/i18n/Translation-es.bz2)  No pude resolver 'uy.archive.ubuntu.com'

W: Imposible obtener [http://uy.archive.ubuntu.com/ubuntu/dists/hardy/universe/i18n/Translation-es.bz2](http://uy.archive.ubuntu.com/ubuntu/dists/hardy/universe/i18n/Translation-es.bz2)  No pude resolver 'uy.archive.ubuntu.com'

W: Imposible obtener [http://uy.archive.ubuntu.com/ubuntu/dists/hardy/multiverse/i18n/Translation-es.bz2](http://uy.archive.ubuntu.com/ubuntu/dists/hardy/multiverse/i18n/Translation-es.bz2)  No pude resolver 'uy.archive.ubuntu.com'

W: Imposible obtener [http://uy.archive.ubuntu.com/ubuntu/dists/hardy-updates/Release.gpg](http://uy.archive.ubuntu.com/ubuntu/dists/hardy-updates/Release.gpg)  No pude resolver 'uy.archive.ubuntu.com'

W: Imposible obtener [http://uy.archive.ubuntu.com/ubuntu/dists/hardy-updates/main/i18n/Translation-es.bz2](http://uy.archive.ubuntu.com/ubuntu/dists/hardy-updates/main/i18n/Translation-es.bz2)  No pude resolver 'uy.archive.ubuntu.com'

W: Imposible obtener [http://uy.archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/i18n/Translation-es.bz2](http://uy.archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/i18n/Translation-es.bz2)  No pude resolver 'uy.archive.ubuntu.com'

W: Imposible obtener [http://uy.archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/i18n/Translation-es.bz2](http://uy.archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/i18n/Translation-es.bz2)  No pude resolver 'uy.archive.ubuntu.com'

W: Imposible obtener [http://uy.archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/i18n/Translation-es.bz2](http://uy.archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/i18n/Translation-es.bz2)  No pude resolver 'uy.archive.ubuntu.com'

W: Imposible obtener [http://security.ubuntu.com/ubuntu/dists/hardy-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/hardy-security/Release.gpg)  No pude resolver 'security.ubuntu.com'

W: Imposible obtener [http://security.ubuntu.com/ubuntu/dists/hardy-security/main/i18n/Translation-es.bz2](http://security.ubuntu.com/ubuntu/dists/hardy-security/main/i18n/Translation-es.bz2)  No pude resolver 'security.ubuntu.com'

W: Imposible obtener [http://security.ubuntu.com/ubuntu/dists/hardy-security/restricted/i18n/Translation-es.bz2](http://security.ubuntu.com/ubuntu/dists/hardy-security/restricted/i18n/Translation-es.bz2)  No pude resolver 'security.ubuntu.com'

W: Imposible obtener [http://security.ubuntu.com/ubuntu/dists/hardy-security/universe/i18n/Translation-es.bz2](http://security.ubuntu.com/ubuntu/dists/hardy-security/universe/i18n/Translation-es.bz2)  No pude resolver 'security.ubuntu.com'

W: Imposible obtener [http://security.ubuntu.com/ubuntu/dists/hardy-security/multiverse/i18n/Translation-es.bz2](http://security.ubuntu.com/ubuntu/dists/hardy-security/multiverse/i18n/Translation-es.bz2)  No pude resolver 'security.ubuntu.com'

W: Imposible obtener [http://lgp203.free.fr/ubuntu/dists/hardy/Release.gpg](http://lgp203.free.fr/ubuntu/dists/hardy/Release.gpg)  No pude resolver 'lgp203.free.fr'

W: Imposible obtener [http://lgp203.free.fr/ubuntu/dists/hardy/universe/i18n/Translation-es.bz2](http://lgp203.free.fr/ubuntu/dists/hardy/universe/i18n/Translation-es.bz2)  No pude resolver 'lgp203.free.fr'

W: Imposible obtener [http://packages.medibuntu.org/dists/intrepid/Release.gpg](http://packages.medibuntu.org/dists/intrepid/Release.gpg)  No pude resolver 'packages.medibuntu.org'

W: Imposible obtener [http://packages.medibuntu.org/dists/intrepid/free/i18n/Translation-es.bz2](http://packages.medibuntu.org/dists/intrepid/free/i18n/Translation-es.bz2)  No pude resolver 'packages.medibuntu.org'

W: Imposible obtener [http://packages.medibuntu.org/dists/intrepid/non-free/i18n/Translation-es.bz2](http://packages.medibuntu.org/dists/intrepid/non-free/i18n/Translation-es.bz2)  No pude resolver 'packages.medibuntu.org'

W: Imposible obtener cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/dists/hardy/main/binary-i386/Packages.gz  Por favor utilice apt-cdrom para hacer que APT reconozca este CD. apt-get update  no se puede usar para agregar nuevos CDs

W: Imposible obtener cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/dists/hardy/restricted/binary-i386/Packages.gz  Por favor utilice apt-cdrom para hacer que APT reconozca este CD. apt-get update  no se puede usar para agregar nuevos CDs

W: Algunos archivos de índice no se han podido descargar, se han ignorado,
o se ha utilizado unos antiguos en su lugar.
W: Duplicate sources.list entry [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/free Packages (/var/lib/apt/lists/packages.medibuntu.org_dists_intrepid_free_binary-i386_Packages)
W: Duplicate sources.list entry [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/non-free Packages (/var/lib/apt/lists/packages.medibuntu.org_dists_intrepid_non-free_binary-i386_Packages)
W: Tal vez quiera ejecutar 'apt-get update' para corregir estos problemas

---

### Post by 3rdalbum on 2009-09-28
It's saying that it can't "resolve" any URLs in your package list. I assume you can access websites on that computer?

If you are behind a proxy you may need to configure your Apt system to use the proxy. I don't personally know how to do this, but you can check if I'm right by putting your proxy details into Synaptic Package Manager and seeing if Synaptic can now update your package list.

---

