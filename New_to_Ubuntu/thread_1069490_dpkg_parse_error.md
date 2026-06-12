---
title: "dpkg parse error"
date: 2009-02-14
forum: New to Ubuntu
---

### Post by F.R Mostert on 2009-02-14
Hi I get this message when I want to install updates I have run dpkg install -f and dpkg configure -a but do not know how to go furture.

dpkg: parse error, in file `/var/lib/dpkg/status' near line 23583 package `hostname':
 duplicate value for user-defined field `Original-Maintainer'
E: Sub-process /usr/bin/dpkg returned an error code (2)



Re:confused:gards

---

### Post by sisco311 on 2009-02-14
try:```
sudo cp /var/lib/dpkg/status-old /var/lib/dpkg/status
```
```
sudo apt-get update
```

---

### Post by F.R Mostert on 2009-02-14
I just did and this is the output.

Reading package lists... Error!
E: Problem parsing dependency Depends
E: Error occurred while processing libcamel1.2-10 (NewVersion1)
E: Problem with MergeList /var/lib/dpkg/status
E: The package lists or status file could not be parsed or opened.

---

### Post by sisco311 on 2009-02-14
uh. please post the output of:
```
ls /var/backups/dpkg.status.*.gz
```

---

### Post by F.R Mostert on 2009-02-14
Here it is 

etta@etta-desktop:~$ ls /var/backups/dpkg.status.*.gz
/var/backups/dpkg.status.1.gz  /var/backups/dpkg.status.4.gz
/var/backups/dpkg.status.2.gz  /var/backups/dpkg.status.5.gz
/var/backups/dpkg.status.3.gz  /var/backups/dpkg.status.6.gz

---

### Post by sisco311 on 2009-02-14
```
sudo gunzip /var/backups/dpkg.status.*.gz
```then```
sudo cp /var/backups/dpkg.status.0 /var/lib/dpkg/status[FONT=monospace]
[/FONT]sudo aptitude update
```if that doesn't work, then try:

```
sudo cp /var/backups/dpkg.status.1 /var/lib/dpkg/status[FONT=monospace]
[/FONT]sudo aptitude update
```and so on.

---

### Post by F.R Mostert on 2009-02-14
Every thing else work except this one

etta@etta-desktop:~$ ls /var/backups/dpkg.status.*.gz
/var/backups/dpkg.status.3.gz
etta@etta-desktop:~$ sudo gunzip /var/backups/dpkg.status.3.gz

gzip: /var/backups/dpkg.status.3.gz: unexpected end of file

---

### Post by sisco311 on 2009-02-14
skip that file.

try to replace the "status" file with one of the backups and see if that solves the problem:
```
sudo cp /var/backups/dpkg.status.0 /var/lib/dpkg/status[FONT=monospace]
[/FONT]sudo aptitude update
```

---

### Post by F.R Mostert on 2009-02-14
This is the output I hope I understood correctly.

etta@etta-desktop:~$ sudo cp /var/backups/dpkg.status.0 /var/lib/dpkg/status
etta@etta-desktop:~$ sudo apt-get update
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) gutsy-backports Release.gpg
Ign [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) gutsy-backports/main Translation-en_ZA        
Ign [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) gutsy-backports/restricted Translation-en_ZA  
Ign [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) gutsy-backports/universe Translation-en_ZA    
Ign [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) gutsy-backports/multiverse Translation-en_ZA  
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) gutsy-backports Release                       
Err [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) hardy Release.gpg                             
  Could not resolve 'medibuntu.sos-sts.com'
Err [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) hardy/free Translation-en_ZA                  
  Could not resolve 'medibuntu.sos-sts.com'
Err [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) hardy/non-free Translation-en_ZA              
  Could not resolve 'medibuntu.sos-sts.com'
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) gutsy-backports/main Packages                 
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) gutsy-backports/restricted Packages
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) gutsy-backports/universe Packages   
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) gutsy-backports/multiverse Packages 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy Release.gpg                      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Translation-en_ZA
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/restricted Translation-en_ZA
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) hardy Release.gpg
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) hardy/main Translation-en_ZA
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe Translation-en_ZA
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/multiverse Translation-en_ZA
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/main Translation-en_ZA
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/restricted Translation-en_ZA
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/universe Translation-en_ZA
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/multiverse Translation-en_ZA
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/main Translation-en_ZA
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/restricted Translation-en_ZA
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) hardy Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/universe Translation-en_ZA
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/multiverse Translation-en_ZA
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy Release    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates Release
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) hardy/main Packages             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security Release
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) hardy/main Packages             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/multiverse Sources
Reading package lists... Done
W: Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/hardy/Release.gpg](http://medibuntu.sos-sts.com/repo/dists/hardy/Release.gpg)  Could not resolve 'medibuntu.sos-sts.com'

W: Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/hardy/free/i18n/Translation-en_ZA.bz2](http://medibuntu.sos-sts.com/repo/dists/hardy/free/i18n/Translation-en_ZA.bz2)  Could not resolve 'medibuntu.sos-sts.com'

W: Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/hardy/non-free/i18n/Translation-en_ZA.bz2](http://medibuntu.sos-sts.com/repo/dists/hardy/non-free/i18n/Translation-en_ZA.bz2)  Could not resolve 'medibuntu.sos-sts.com'

W: Some index files failed to download, they have been ignored, or old ones used instead.
W: You may want to run apt-get update to correct these problems

---

### Post by sisco311 on 2009-02-14
The problem with the "status" file is sorted out. 

Now comes the sources.list. :)
post:```
cat /etc/apt/sources.list
```

---

### Post by F.R Mostert on 2009-02-14
This is the output

etta@etta-desktop:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-security main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-security main restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-security universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-security universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-security multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-security multiverse
deb [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) hardy free non-free
deb [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) hardy free non-free
etta@etta-desktop:~$

---

### Post by sisco311 on 2009-02-14
Comment out the gutsy and medibuntu repositories in the sources.list:
```
gksu gedit /etc/apt/sources.list
```
> # deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
[B]#deb [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
[/B]# deb-src [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-security main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-security main restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-security universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-security universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-security multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-security multiverse
[B]#deb [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) hardy free non-free
#deb [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) hardy free non-free[/B]


and follow the instructions on [uhelp]community/Medibuntu[/uhelp] to add the medibuntu repositories.(don't forget to add the GPG key)

---

### Post by F.R Mostert on 2009-02-14
please help with gpg key I do not know howto.

Sorry for been a pain in your neck you have been a great help.

Best Regards

---

### Post by drs305 on 2009-02-14
> **F.R Mostert said:**
> please help with gpg key I do not know howto.

Sorry for been a pain in your neck you have been a great help.

Best Regards

Open a terminal and:

If you are running Intrepid, run these commands. They will add the medibuntu repository and import the security key:
```
sudo wget http://www.medibuntu.org/sources.list.d/intrepid.list --output-document=/etc/apt/sources.list.d/medibuntu.list
wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add - && sudo apt-get update
```

If you are running Hardy, run these commands:
If you don't have the medibuntu repository installed and enabled or you are having problems with it?
```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list --output-document=/etc/apt/sources.list.d/medibuntu.list
wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add - && sudo apt-get update
```

---

### Post by F.R Mostert on 2009-02-14
This is still a problem

etta@etta-desktop:~$ sudo dpkg --configure -a
dpkg: parse error, in file `/var/lib/dpkg/available' near line 40203 package `ruby1.8-dev':
 `Depends' field, syntax error after reference to package `libruby1.8'

---

### Post by drs305 on 2009-02-14
There is a backup *available* file (available-old) just as there is for *status*. You can try the same command cisco gave you in post #2, substituting *available* for *status*  If it doesn't work, I don't believe the system creates a .gz file in /var/backups as it does for *status* but you could check.

---

### Post by F.R Mostert on 2009-02-14
Thank you very much everything is solved now.

best regards

---

