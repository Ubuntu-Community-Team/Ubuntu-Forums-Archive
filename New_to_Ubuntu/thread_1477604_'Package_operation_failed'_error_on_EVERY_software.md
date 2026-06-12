---
title: "'Package operation failed' error on EVERY software install attempt"
date: 2010-05-08
forum: New to Ubuntu
---

### Post by dvaldes21 on 2010-05-08
Hi guys,
This is actually my first post on here, and I'm a new Ubuntu user....

I'm having a problem when trying to install or otherwise modify packages. It gets to about 90% complete, then I get the following error:

>  Package operation failed. The installation or removal of a software package failed.

installArchives() failed: Selecting previously deselected package kmix. 
(Reading database ...  (Reading database ... 5% (Reading database ... 10% (Reading database ... 15% (Reading database ... 20% (Reading database ... 25% (Reading database ... 30% (Reading database ... 35% (Reading database ... 40% (Reading database ... 45% (Reading database ... 50% (Reading database ... 55% (Reading database ... 60% (Reading database ... 65% (Reading database ... 70% (Reading database ... 75% (Reading database ... 80% (Reading database ... 85% (Reading database ... 90% (Reading database ... 95% (Reading database ... 100% (Reading database ... 162994 files and directories currently installed.) 
Unpacking kmix (from .../kmix_4%3a4.4.2-0ubuntu3_amd64.deb) ... 
Processing triggers for desktop-file-utils ... 
Processing triggers for python-gmenu ... 
Rebuilding /usr/share/applications/desktop.en_US.UTF8.cache... 
Processing triggers for hicolor-icon-theme ... 
Processing triggers for python-support ... 
Setting up nspluginwrapper (1.2.2-0ubuntu6) ... 
plugin dirs: 
Auto-update plugins from /usr/lib/mozilla/plugins 
Looking for plugins in /usr/lib/mozilla/plugins 
Segmentation fault 
dpkg: error processing nspluginwrapper (--configure): 
 subprocess installed post-installation script returned error exit status 139 
Setting up kmix (4:4.4.2-0ubuntu3) ... 
Errors were encountered while processing: 
 nspluginwrapper 
Setting up nspluginwrapper (1.2.2-0ubuntu6) ... 
plugin dirs: 
Auto-update plugins from /usr/lib/mozilla/plugins 
Looking for plugins in /usr/lib/mozilla/plugins 
Segmentation fault 
dpkg: error processing nspluginwrapper (--configure): 
 subprocess installed post-installation script returned error exit status 139 

It seems that the problem is the nspluginwrapper...but I've tried to uninstall and reinstall the package and it doesn't seem to fix to problem. 

Any advice?

---

### Post by Sealbhach on 2010-05-08
Try running:

```
sudo dpkg --configure -a
```

.

---

### Post by dvaldes21 on 2010-05-08
> **Sealbhach said:**
> Try running:

```
sudo dpkg --configure -a
```.

Here's what I get as a reply....

> Setting up nspluginwrapper (1.2.2-0ubuntu6) ...
plugin dirs:
Auto-update plugins from /usr/lib/mozilla/plugins
Looking for plugins in /usr/lib/mozilla/plugins
Segmentation fault
dpkg: error processing nspluginwrapper (--configure):
 subprocess installed post-installation script returned error exit status 139
Errors were encountered while processing:
 nspluginwrapper


---

### Post by Sealbhach on 2010-05-08
> **dvaldes21 said:**
> Here's what I get as a reply....

OK, try this:

```
sudo dpkg --configure nspluginwrapper
```


.

---

### Post by dvaldes21 on 2010-05-09
> **Sealbhach said:**
> OK, try this:

```
sudo dpkg --configure nspluginwrapper
```
.

Another error...is this a common problem? Maybe something went wrong during install?

> Auto-update plugins from /usr/lib/mozilla/plugins
Looking for plugins in /usr/lib/mozilla/plugins
Segmentation fault
dpkg: error processing nspluginwrapper (--configure):
 subprocess installed post-installation script returned error exit status 139
Errors were encountered while processing:
 nspluginwrapper
danny@danny-desktop:~$ ^C


---

### Post by Sealbhach on 2010-05-09
OK, I found a suggested solution [here]("http://swiss.ubuntuforums.org/showthread.php?t=387817")

sudo rm -f /var/lib/dpkg/info/nspluginwrapper.postrm
sudo rm -f /var/lib/dpkg/info/nspluginwrapper.prerm
sudo apt-get remove nspluginwrapper

Essentially you just rip out all reference in dpkg to nspluginwrapper and remove it.

.

---

### Post by amir_pasha on 2010-06-11
I have more or less the same problem. I think with package "GNOME-DO", but I don't know how to do it.
when I want to install/remove a package I get the following error.
(below I am (re)installing evolution notification):
> installArchives() failed: (Reading database ... 
(Reading database ... 5%
(Reading database ... 10%
(Reading database ... 15%
(Reading database ... 20%
(Reading database ... 25%
(Reading database ... 30%
(Reading database ... 35%
(Reading database ... 40%
(Reading database ... 45%
(Reading database ... 50%
(Reading database ... 55%
(Reading database ... 60%
(Reading database ... 65%
(Reading database ... 70%
(Reading database ... 75%
(Reading database ... 80%
(Reading database ... 85%
(Reading database ... 90%
(Reading database ... 95%
(Reading database ... 100%
(Reading database ... 169408 files and directories currently installed.)
Preparing to replace gnome-do 0.8.3.1+dfsg-1ubuntu1 (using .../gnome-do_0.8.3.1+dfsg-1ubuntu1_i386.deb) ...
Unpacking replacement gnome-do ...
Traceback (most recent call last):
  File "/usr/bin/update-gconf-defaults", line 156, in <module>
    read_entries(realname)
  File "/usr/bin/update-gconf-defaults", line 116, in read_entries
    for line in file(filename):
IOError: [Errno 2] No such file or directory: '/usr/share/gconf/defaults/20_une-gconf-default'
dpkg: warning: old post-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
Traceback (most recent call last):
  File "/usr/bin/update-gconf-defaults", line 156, in <module>
    read_entries(realname)
  File "/usr/bin/update-gconf-defaults", line 116, in read_entries
    for line in file(filename):
IOError: [Errno 2] No such file or directory: '/usr/share/gconf/defaults/20_une-gconf-default'
dpkg: error processing /var/cache/apt/archives/gnome-do_0.8.3.1+dfsg-1ubuntu1_i386.deb (--unpack):
 subprocess new post-removal script returned error exit status 1
Traceback (most recent call last):
  File "/usr/bin/update-gconf-defaults", line 156, in <module>
    read_entries(realname)
  File "/usr/bin/update-gconf-defaults", line 116, in read_entries
    for line in file(filename):
IOError: [Errno 2] No such file or directory: '/usr/share/gconf/defaults/20_une-gconf-default'
dpkg: error while cleaning up:
 subprocess new post-removal script returned error exit status 1
Selecting previously deselected package mail-notification.
Unpacking mail-notification (from .../mail-notification_5.4.dfsg.1-2ubuntu1_i386.deb) ...
Selecting previously deselected package mail-notification-evolution.
Unpacking mail-notification-evolution (from .../mail-notification-evolution_5.4.dfsg.1-2ubuntu1_i386.deb) ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.UTF8.cache...
Processing triggers for man-db ...
Processing triggers for python-support ...
Errors were encountered while processing:
 /var/cache/apt/archives/gnome-do_0.8.3.1+dfsg-1ubuntu1_i386.deb
Setting up mail-notification (5.4.dfsg.1-2ubuntu1) ...

Setting up mail-notification-evolution (5.4.dfsg.1-2ubuntu1) ...


and I did try your solution
sudo rm -f /var/lib/dpkg/info/gnome-do.postrm
sudo rm -f /var/lib/dpkg/info/gnome-do.prerm
sudo apt-get remove gnome-do

but it doesn't work. here is the error I got in the terminal:
> amirpasha@Amirpasha-LucidLynx:~$ sudo apt-get remove gnome-do
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.32-21 linux-headers-2.6.32-21-generic
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  gnome-do
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 2,204kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 169500 files and directories currently installed.)
Removing gnome-do ...
Traceback (most recent call last):
  File "/usr/bin/update-gconf-defaults", line 156, in <module>
    read_entries(realname)
  File "/usr/bin/update-gconf-defaults", line 116, in read_entries
    for line in file(filename):
IOError: [Errno 2] No such file or directory: '/usr/share/gconf/defaults/20_une-gconf-default'
dpkg: error processing gnome-do (--remove):
 subprocess installed post-removal script returned error exit status 1
Processing triggers for man-db ...
Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for hicolor-icon-theme ...
Processing triggers for python-support ...
Errors were encountered while processing:
 gnome-do
E: Sub-process /usr/bin/dpkg returned an error code (1)
amirpasha@Amirpasha-LucidLynx:~$ sudo dpkg -l grep gnome-do
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Cfg-files/Unpacked/Failed-cfg/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
rH  gnome-do       0.8.3.1+dfsg-1 Quickly perform actions on your desktop
ii  grep           2.5.4-4build1  GNU grep, egrep and fgrep
amirpasha@Amirpasha-LucidLynx:~$ sudo apt-get remove gnome-do
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.32-21 linux-headers-2.6.32-21-generic
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  gnome-do
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 2,204kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 169406 files and directories currently installed.)
Removing gnome-do ...
Traceback (most recent call last):
  File "/usr/bin/update-gconf-defaults", line 156, in <module>
    read_entries(realname)
  File "/usr/bin/update-gconf-defaults", line 116, in read_entries
    for line in file(filename):
IOError: [Errno 2] No such file or directory: '/usr/share/gconf/defaults/20_une-gconf-default'
dpkg: error processing gnome-do (--remove):
 subprocess installed post-removal script returned error exit status 1
Errors were encountered while processing:
 gnome-do
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by amir_pasha on 2010-06-11
I got it!
just catch an idea from [here]("http://ubuntuforums.org/showthread.php?t=212467"), 
force removing a package
anyway to get rid of that **** try:
> sudo apt-get install -f

---

### Post by twdurdentwd on 2010-09-28
I'm having a similar problem when downloading any software from the software center:

installArchives() failed: (Reading database ...  (Reading database ... 5% (Reading database ... 10% (Reading database ... 15% (Reading database ... 20% (Reading database ... 25% (Reading database ... 30% (Reading database ... 35% (Reading database ... 40% (Reading database ... 45% (Reading database ... 50% (Reading database ... 55% (Reading database ... 60% (Reading database ... 65% (Reading database ... 70% (Reading database ... 75% (Reading database ... 80% (Reading database ... 85% (Reading database ... 90% (Reading database ... 95% (Reading database ... 100% (Reading database ... 141836 files and directories currently installed.) 
Removing amsn ... 
Processing triggers for man-db ... 
Processing triggers for desktop-file-utils ... 
Setting up ca-certificates-java (20090928) ... 
creating /etc/ssl/certs/java/cacerts... 
  error adding brasil.gov.br/brasil.gov.br.crt 
  error adding cacert.org/cacert.org.crt 
  error adding debconf.org/ca.crt 
  error adding gouv.fr/cert_igca_dsa.crt 
  error adding gouv.fr/cert_igca_rsa.crt 
  error adding mozilla/ABAecom_=sub.__Am._Bankers_Assn.=_Root_CA.crt 
  error adding mozilla/AOL_Time_Warner_Root_Certification_Authority_1.crt 
  error adding mozilla/AOL_Time_Warner_Root_Certification_Authority_2.crt 
  error adding mozilla/AddTrust_External_Root.crt 
  error adding mozilla/AddTrust_Low-Value_Services_Root.crt 
  error adding mozilla/AddTrust_Public_Services_Root.crt 
  error adding mozilla/AddTrust_Qualified_Certificates_Root.crt 
  error adding mozilla/America_Online_Root_Certification_Authority_1.crt 
  error adding mozilla/America_Online_Root_Certification_Authority_2.crt 
  error adding mozilla/Baltimore_CyberTrust_Root.crt 
  error adding mozilla/COMODO_Certification_Authority.crt 
  error adding mozilla/COMODO_ECC_Certification_Authority.crt 
  error adding mozilla/Camerfirma_Chambers_of_Commerce_Root.crt 
  error adding mozilla/Camerfirma_Global_Chambersign_Root.crt 
  error adding mozilla/Certplus_Class_2_Primary_CA.crt 
  error adding mozilla/Certum_Root_CA.crt 
  error adding mozilla/Comodo_AAA_Services_root.crt 
  error adding mozilla/Comodo_Secure_Services_root.crt 
  error adding mozilla/Comodo_Trusted_Services_root.crt 
  error adding mozilla/DST_ACES_CA_X6.crt 
  error adding mozilla/DST_Root_CA_X3.crt 
  error adding mozilla/DigiCert_Assured_ID_Root_CA.crt 
  error adding mozilla/DigiCert_Global_Root_CA.crt 
  error adding mozilla/DigiCert_High_Assurance_EV_Root_CA.crt 
  error adding mozilla/DigiNotar_Root_CA.crt 
  error adding mozilla/Digital_Signature_Trust_Co._Global_CA_1.crt 
  error adding mozilla/Digital_Signature_Trust_Co._Global_CA_2.crt 
  error adding mozilla/Digital_Signature_Trust_Co._Global_CA_3.crt 
  error adding mozilla/Digital_Signature_Trust_Co._Global_CA_4.crt 
  error adding mozilla/Entrust.net_Global_Secure_Personal_CA.crt 
  error adding mozilla/Entrust.net_Global_Secure_Server_CA.crt 
  error adding mozilla/Entrust.net_Premium_2048_Secure_Server_CA.crt 
  error adding mozilla/Entrust.net_Secure_Personal_CA.crt 
  error adding mozilla/Entrust.net_Secure_Server_CA.crt 
  error adding mozilla/Entrust_Root_Certification_Authority.crt 
  error adding mozilla/Equifax_Secure_CA.crt 
  error adding mozilla/Equifax_Secure_Global_eBusiness_CA.crt 
  error adding mozilla/Equifax_Secure_eBusiness_CA_1.crt 
  error adding mozilla/Equifax_Secure_eBusiness_CA_2.crt 
  error adding mozilla/Firmaprofesional_Root_CA.crt 
  error adding mozilla/GTE_CyberTrust_Global_Root.crt 
  error adding mozilla/GTE_CyberTrust_Root_CA.crt 
  error adding mozilla/GeoTrust_Global_CA.crt 
  error adding mozilla/GeoTrust_Global_CA_2.crt 
  error adding mozilla/GeoTrust_Primary_Certification_Authority.crt 
  error adding mozilla/GeoTrust_Universal_CA.crt 
  error adding mozilla/GeoTrust_Universal_CA_2.crt 
  error adding mozilla/GlobalSign_Root_CA.crt 
  error adding mozilla/GlobalSign_Root_CA_-_R2.crt 
  error adding mozilla/Go_Daddy_Class_2_CA.crt 
  error adding mozilla/IPS_CLASE1_root.crt 
  error adding mozilla/IPS_CLASE3_root.crt 
  error adding mozilla/IPS_CLASEA1_root.crt 
  error adding mozilla/IPS_CLASEA3_root.crt 
  error adding mozilla/IPS_Chained_CAs_root.crt 
  error adding mozilla/IPS_Servidores_root.crt 
  error adding mozilla/IPS_Timestamping_root.crt 
  error adding mozilla/NetLock_Business_=Class_B=_Root.crt 
  error adding mozilla/NetLock_Express_=Class_C=_Root.crt 
  error adding mozilla/NetLock_Notary_=Class_A=_Root.crt 
  error adding mozilla/NetLock_Qualified_=Class_QA=_Root.crt 
  error adding mozilla/Network_Solutions_Certificate_Authority.crt 
  error adding mozilla/QuoVadis_Root_CA.crt 
  error adding mozilla/QuoVadis_Root_CA_2.crt 
  error adding mozilla/QuoVadis_Root_CA_3.crt 
  error adding mozilla/RSA_Root_Certificate_1.crt 
  error adding mozilla/RSA_Security_1024_v3.crt 
  error adding mozilla/RSA_Security_2048_v3.crt 
  error adding mozilla/SecureTrust_CA.crt 
  error adding mozilla/Secure_Global_CA.crt 
  error adding mozilla/Security_Communication_Root_CA.crt 
  error adding mozilla/Sonera_Class_1_Root_CA.crt 
  error adding mozilla/Sonera_Class_2_Root_CA.crt 
  error adding mozilla/Staat_der_Nederlanden_Root_CA.crt 
  error adding mozilla/Starfield_Class_2_CA.crt 
  error adding mozilla/StartCom_Certification_Authority.crt 
  error adding mozilla/StartCom_Ltd..crt 
  error adding mozilla/SwissSign_Gold_CA_-_G2.crt 
  error adding mozilla/SwissSign_Platinum_CA_-_G2.crt 
  error adding mozilla/SwissSign_Silver_CA_-_G2.crt 
  error adding mozilla/Swisscom_Root_CA_1.crt 
  error adding mozilla/TC_TrustCenter__Germany__Class_2_CA.crt 
  error adding mozilla/TC_TrustCenter__Germany__Class_3_CA.crt 
  error adding mozilla/TDC_Internet_Root_CA.crt 
  error adding mozilla/TDC_OCES_Root_CA.crt 
  error adding mozilla/TURKTRUST_Certificate_Services_Provider_Root_1.crt 
  error adding mozilla/TURKTRUST_Certificate_Services_Provider_Root_2.crt 
  error adding mozilla/Taiwan_GRCA.crt 
  error adding mozilla/Thawte_Personal_Basic_CA.crt 
  error adding mozilla/Thawte_Personal_Freemail_CA.crt 
  error adding mozilla/Thawte_Personal_Premium_CA.crt 
  error adding mozilla/Thawte_Premium_Server_CA.crt 
  error adding mozilla/Thawte_Server_CA.crt 
  error adding mozilla/Thawte_Time_Stamping_CA.crt 
  error adding mozilla/UTN-USER_First-Network_Applications.crt 
  error adding mozilla/UTN_DATACorp_SGC_Root_CA.crt 
  error adding mozilla/UTN_USERFirst_Email_Root_CA.crt 
  error adding mozilla/UTN_USERFirst_Hardware_Root_CA.crt 
  error adding mozilla/ValiCert_Class_1_VA.crt 
  error adding mozilla/ValiCert_Class_2_VA.crt 
  error adding mozilla/VeriSign_Class_3_Public_Primary_Certification_Authority_-_G5.crt 
  error adding mozilla/Verisign_Class_1_Public_Primary_Certification_Authority.crt 
  error adding mozilla/Verisign_Class_1_Public_Primary_Certification_Authority_-_G2.crt 
  error adding mozilla/Verisign_Class_1_Public_Primary_Certification_Authority_-_G3.crt 
  error adding mozilla/Verisign_Class_2_Public_Primary_Certification_Authority.crt 
  error adding mozilla/Verisign_Class_2_Public_Primary_Certification_Authority_-_G2.crt 
  error adding mozilla/Verisign_Class_2_Public_Primary_Certification_Authority_-_G3.crt 
  error adding mozilla/Verisign_Class_3_Public_Primary_Certification_Authority.crt 
  error adding mozilla/Verisign_Class_3_Public_Primary_Certification_Authority_-_G2.crt 
  error adding mozilla/Verisign_Class_3_Public_Primary_Certification_Authority_-_G3.crt 
  error adding mozilla/Verisign_Class_4_Public_Primary_Certification_Authority_-_G2.crt 
  error adding mozilla/Verisign_Class_4_Public_Primary_Certification_Authority_-_G3.crt 
  error adding mozilla/Verisign_RSA_Secure_Server_CA.crt 
  error adding mozilla/Verisign_Time_Stamping_Authority_CA.crt 
  error adding mozilla/Visa_International_Global_Root_2.crt 
  error adding mozilla/Visa_eCommerce_Root.crt 
  error adding mozilla/WellsSecure_Public_Root_Certificate_Authority.crt 
  error adding mozilla/Wells_Fargo_Root_CA.crt 
  error adding mozilla/XRamp_Global_CA_Root.crt 
  error adding mozilla/beTRUSTed_Root_CA-Baltimore_Implementation.crt 
  error adding mozilla/beTRUSTed_Root_CA.crt 
  error adding mozilla/beTRUSTed_Root_CA_-_Entrust_Implementation.crt 
  error adding mozilla/beTRUSTed_Root_CA_-_RSA_Implementation.crt 
  error adding mozilla/thawte_Primary_Root_CA.crt 
  error adding signet.pl/signet_ca1_pem.crt 
  error adding signet.pl/signet_ca2_pem.crt 
  error adding signet.pl/signet_ca3_pem.crt 
  error adding signet.pl/signet_ocspklasa2_pem.crt 
  error adding signet.pl/signet_ocspklasa3_pem.crt 
  error adding signet.pl/signet_pca2_pem.crt 
  error adding signet.pl/signet_pca3_pem.crt 
  error adding signet.pl/signet_rootca_pem.crt 
  error adding signet.pl/signet_tsa1_pem.crt 
  error adding spi-inc.org/spi-ca-2003.crt 
  error adding spi-inc.org/spi-cacert-2008.crt 
  error adding telesec.de/deutsche-telekom-root-ca-2.crt 
failed. 
dpkg: error processing ca-certificates-java (--configure): 
 subprocess installed post-installation script returned error exit status 1 
Setting up libswscale0 (4:0.5+svn20090706-2ubuntu2.2) ... 
dpkg (subprocess): unable to execute installed post-installation script: Exec format error 
dpkg: error processing libswscale0 (--configure): 
 subprocess installed post-installation script returned error exit status 2 
dpkg: dependency problems prevent configuration of libcv1: 
 libcv1 depends on libswscale0 (>= 3:0.svn20090303-1) | libswscale-extra-0 (>= 3:0.svn20090303-1); however: 
  Package libswscale0 is not configured yet. 
  Package libswscale-extra-0 is not installed. 
dpkg: error processing libcv1 (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of libcvaux1: 
 libcvaux1 depends on libcv1; however: 
  Package libcv1 is not configured yet. 
 libcvaux1 depends on libswscale0 (>= 3:0.svn20090303-1) | libswscale-extra-0 (>= 3:0.svn20090303-1); however: 
  Package libswscale0 is not configured yet. 
  Package libswscale-extra-0 is not installed. 
dpkg: error processing libcvaux1 (--configure): 
 dependency problems - leaving unconfigured 
SettinNo apport report written because the error message indicates its a followup error from a previous failure.
No apport report written because MaxReports is reached already
g up libfftw3-3 (3.2.1-2ubuntu2) ... 
dpkg (subprocess): unable to execute installed post-installation script: Exec format error 
dpkg: error processing libfftw3-3 (--configure): 
 subprocess installed post-installation script returned error exit status 2 
dpkg: dependency problems prevent configuration of libhighgui1: 
 libhighgui1 depends on libcv1; however: 
  Package libcv1 is not configured yet. 
 libhighgui1 depends on libswscale0 (>= 3:0.svn20090303-1) | libswscale-extra-0 (>= 3:0.svn20090303-1); however: 
  Package libswscale0 is not configured yet. 
  Package libswscale-extra-0 is not installed. 
dpkg: error processing libhighgui1 (--configure): 
 dependency problems - leaving unconfigured 
Setting up liblapack3gf (3.2.1-1) ... 
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
dpkg (subprocess): unable to execute installed post-installation script: Exec format error 
dpkg: error processing liblapack3gf (--configure): 
 subprocess installed post-installation script returned error exit status 2 
Setting up libmatio0 (1.3.3-4) ... 
No apport report written because MaxReports is reached already
dpkg (subprocess): unable to execute installed post-installation script: Exec format error 
dpkg: error processing libmatio0 (--configure): 
 subprocess installed post-installation script returned error exit status 2 
Setting up libruby1.8 (1.8.7.174-1ubuntu1) ... 
No apport report written because MaxReports is reached already
dpkg (subprocess): unable to execute installed post-installation script: Exec format error 
dpkg: error processing libruby1.8 (--configure): 
 subprocess installed post-installation script returned error exit status 2 
Setting up libumfpack5.4.0 (1:3.4.0-1ubuntu2) ... 
No apport report written because MaxReports is reached already
dpkg (subprocess): unable to execute installed post-installation script: Exec format error 
dpkg: error processing libumfpack5.4.0 (--configure): 
 subprocess installed post-installation script returned error exit status 2 
dpkg: dependency problems prevent configuration of python-numpy: 
 python-numpy depends on liblapack3gf | liblapack.so.3gf | libatlas3gf-base; however: 
  Package liblapack3gf is not configured yet. 
  Package liblapack.so.3gf is not installed. 
  Package liblapack3gf which provides liblapack.so.3gf is not configured yet. 
  Package libatlas3gf-base is not installed. 
dpkg: error processing python-numpy (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of python-pygame: 
 python-pygame depends on python-numpy; however: 
  Package python-numpy is not configured yet. 
dpkg: error processing python-pygame (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of lightyears: 
 lightNo apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
years depends on python-pygame (>= 1.7); however: 
  Package python-pygame is not configured yet. 
dpkg: error processing lightyears (--configure): 
 dependency problems - leaving unconfigured 
Setting up rhino (1.7R2-1ubuntu1) ... 
dpkg (subprocess): unable to execute installed post-installation script: Exec format error 
dpkg: error processing rhino (--configure): 
 subprocess installed post-installation script returned error exit status 2 
dpkg: dependency problems prevent configuration of ruby1.8: 
 ruby1.8 depends on libruby1.8 (>= 1.8.7.174); however: 
  Package libruby1.8 is not configured yet. 
dpkg: error processing ruby1.8 (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of ruby: 
 ruby depends on ruby1.8; however: 
  Package ruby1.8 is not configured yet. 
dpkg: error processing ruby (--configure): 
 dependency problems - leaving unconfigured 
Setting up tcl8.5 (8.5.7-1) ... 
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
dpkg (subprocess): unable to execute installed post-installation script: Exec format error 
dpkg: error processing tcl8.5 (--configure): 
 subprocess installed post-installation script returned error exit status 2 
dpkg: dependency problems prevent configuration of tk8.5: 
 tk8.5 depends on tcl8.5 (>= 8.5.0); however: 
  Package tcl8.5 is not configured yet. 
dpkg: error processing tk8.5 (--configure): 
 dependency problems - leaving unconfigured 
Setting up libpvm3 (3.4.5-12) ... 
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
dpkg (subprocess): unable to execute installed post-installation script: Exec format error 
dpkg: error processing libpvm3 (--configure): 
 subprocess installed post-installation script returned error exit status 2 
No apport report written because MaxReports is reached already
Errors were encountered while processing: 
 ca-certificates-java 
 libswscale0 
 libcv1 
 libcvaux1 
 libfftw3-3 
 libhighgui1 
 liblapack3gf 
 libmatio0 
 libruby1.8 
 libumfpack5.4.0 
 python-numpy 
 python-pygame 
 lightyears 
 rhino 
 ruby1.8 
 ruby 
 tcl8.5 
 tk8.5 
 libpvm3 


Any suggestions?

---

### Post by twdurdentwd on 2010-09-28
That was actually removing a software that didn't install correctly, but the prompt says "downloading or removing"

---

### Post by twdurdentwd on 2010-09-28
These are the details of an attempted download for software "Axel":


installArchives() failed: Selecting previously deselected package axel. 
(Reading database ...  (Reading database ... 5% (Reading database ... 10% (Reading database ... 15% (Reading database ... 20% (Reading database ... 25% (Reading database ... 30% (Reading database ... 35% (Reading database ... 40% (Reading database ... 45% (Reading database ... 50% (Reading database ... 55% (Reading database ... 60% (Reading database ... 65% (Reading database ... 70% (Reading database ... 75% (Reading database ... 80% (Reading database ... 85% (Reading database ... 90% (Reading database ... 95% (Reading database ... 100% (Reading database ... 141788 files and directories currently installed.) 
Unpacking axel (from .../archives/axel_2.4-1_i386.deb) ... 
Selecting previously deselected package libqt3-mt. 
Unpacking libqt3-mt (from .../libqt3-mt_3%3a3.3.8-b-5ubuntu3_i386.deb) ... 
Selecting previously deselected package kaptain. 
Unpacking kaptain (from .../kaptain_1%3a0.72-3_i386.deb) ... 
Selecting previously deselected package axel-kapt. 
Unpacking axel-kapt (from .../axel-kapt_2.4-1_all.deb) ... 
Processing triggers for man-db ... 
Processing triggers for install-info ... 
Processing triggers for doc-base ... 
Processing 1 added doc-base file(s)... 
Registering documents with scrollkeeper... 
Processing triggers for desktop-file-utils ... 
Setting up ca-certificates-java (20090928) ... 
creating /etc/ssl/certs/java/cacerts... 
  error adding brasil.gov.br/brasil.gov.br.crt 
  error adding cacert.org/cacert.org.crt 
  error adding debconf.org/ca.crt 
  error adding gouv.fr/cert_igca_dsa.crt 
  error adding gouv.fr/cert_igca_rsa.crt 
  error adding mozilla/ABAecom_=sub.__Am._Bankers_Assn.=_Root_CA.crt 
  error adding mozilla/AOL_Time_Warner_Root_Certification_Authority_1.crt 
  error adding mozilla/AOL_Time_Warner_Root_Certification_Authority_2.crt 
  error adding mozilla/AddTrust_External_Root.crt 
  error adding mozilla/AddTrust_Low-Value_Services_Root.crt 
  error adding mozilla/AddTrust_Public_Services_Root.crt 
  error adding mozilla/AddTrust_Qualified_Certificates_Root.crt 
  error adding mozilla/America_Online_Root_Certification_Authority_1.crt 
  error adding mozilla/America_Online_Root_Certification_Authority_2.crt 
  error adding mozilla/Baltimore_CyberTrust_Root.crt 
  error adding mozilla/COMODO_Certification_Authority.crt 
  error adding mozilla/COMODO_ECC_Certification_Authority.crt 
  error adding mozilla/Camerfirma_Chambers_of_Commerce_Root.crt 
  error adding mozilla/Camerfirma_Global_Chambersign_Root.crt 
  error adding mozilla/Certplus_Class_2_Primary_CA.crt 
  error adding mozilla/Certum_Root_CA.crt 
  error adding mozilla/Comodo_AAA_Services_root.crt 
  error adding mozilla/Comodo_Secure_Services_root.crt 
  error adding mozilla/Comodo_Trusted_Services_root.crt 
  error adding mozilla/DST_ACES_CA_X6.crt 
  error adding mozilla/DST_Root_CA_X3.crt 
  error adding mozilla/DigiCert_Assured_ID_Root_CA.crt 
  error adding mozilla/DigiCert_Global_Root_CA.crt 
  error adding mozilla/DigiCert_High_Assurance_EV_Root_CA.crt 
  error adding mozilla/DigiNotar_Root_CA.crt 
  error adding mozilla/Digital_Signature_Trust_Co._Global_CA_1.crt 
  error adding mozilla/Digital_Signature_Trust_Co._Global_CA_2.crt 
  error adding mozilla/Digital_Signature_Trust_Co._Global_CA_3.crt 
  error adding mozilla/Digital_Signature_Trust_Co._Global_CA_4.crt 
  error adding mozilla/Entrust.net_Global_Secure_Personal_CA.crt 
  error adding mozilla/Entrust.net_Global_Secure_Server_CA.crt 
  error adding mozilla/Entrust.net_Premium_2048_Secure_Server_CA.crt 
  error adding mozilla/Entrust.net_Secure_Personal_CA.crt 
  error adding mozilla/Entrust.net_Secure_Server_CA.crt 
  error adding mozilla/Entrust_Root_Certification_Authority.crt 
  error adding mozilla/Equifax_Secure_CA.crt 
  error adding mozilla/Equifax_Secure_Global_eBusiness_CA.crt 
  error adding mozilla/Equifax_Secure_eBusiness_CA_1.crt 
  error adding mozilla/Equifax_Secure_eBusiness_CA_2.crt 
  error adding mozilla/Firmaprofesional_Root_CA.crt 
  error adding mozilla/GTE_CyberTrust_Global_Root.crt 
  error adding mozilla/GTE_CyberTrust_Root_CA.crt 
  error adding mozilla/GeoTrust_Global_CA.crt 
  error adding mozilla/GeoTrust_Global_CA_2.crt 
  error adding mozilla/GeoTrust_Primary_Certification_Authority.crt 
  error adding mozilla/GeoTrust_Universal_CA.crt 
  error adding mozilla/GeoTrust_Universal_CA_2.crt 
  error adding mozilla/GlobalSign_Root_CA.crt 
  error adding mozilla/GlobalSign_Root_CA_-_R2.crt 
  error adding mozilla/Go_Daddy_Class_2_CA.crt 
  error adding mozilla/IPS_CLASE1_root.crt 
  error adding mozilla/IPS_CLASE3_root.crt 
  error adding mozilla/IPS_CLASEA1_root.crt 
  error adding mozilla/IPS_CLASEA3_root.crt 
  error adding mozilla/IPS_Chained_CAs_root.crt 
  error adding mozilla/IPS_Servidores_root.crt 
  error adding mozilla/IPS_Timestamping_root.crt 
  error adding mozilla/NetLock_Business_=Class_B=_Root.crt 
  error adding mozilla/NetLock_Express_=Class_C=_Root.crt 
  error adding mozilla/NetLock_Notary_=Class_A=_Root.crt 
  error adding mozilla/NetLock_Qualified_=Class_QA=_Root.crt 
  error adding mozilla/Network_Solutions_Certificate_Authority.crt 
  error adding mozilla/QuoVadis_Root_CA.crt 
  error adding mozilla/QuoVadis_Root_CA_2.crt 
  error adding mozilla/QuoVadis_Root_CA_3.crt 
  error adding mozilla/RSA_Root_Certificate_1.crt 
  error adding mozilla/RSA_Security_1024_v3.crt 
  error adding mozilla/RSA_Security_2048_v3.crt 
  error adding mozilla/SecureTrust_CA.crt 
  error adding mozilla/Secure_Global_CA.crt 
  error adding mozilla/Security_Communication_Root_CA.crt 
  error adding mozilla/Sonera_Class_1_Root_CA.crt 
  error adding mozilla/Sonera_Class_2_Root_CA.crt 
  error adding mozilla/Staat_der_Nederlanden_Root_CA.crt 
  error adding mozilla/Starfield_Class_2_CA.crt 
  error adding mozilla/StartCom_Certification_Authority.crt 
  error adding mozilla/StartCom_Ltd..crt 
  error adding mozilla/SwissSign_Gold_CA_-_G2.crt 
  error adding mozilla/SwissSign_Platinum_CA_-_G2.crt 
  error adding mozilla/SwissSign_Silver_CA_-_G2.crt 
  error adding mozilla/Swisscom_Root_CA_1.crt 
  error adding mozilla/TC_TrustCenter__Germany__Class_2_CA.crt 
  error adding mozilla/TC_TrustCenter__Germany__Class_3_CA.crt 
  error adding mozilla/TDC_Internet_Root_CA.crt 
  error adding mozilla/TDC_OCES_Root_CA.crt 
  error adding mozilla/TURKTRUST_Certificate_Services_Provider_Root_1.crt 
  error adding mozilla/TURKTRUST_Certificate_Services_Provider_Root_2.crt 
  error adding mozilla/Taiwan_GRCA.crt 
  error adding mozilla/Thawte_Personal_Basic_CA.crt 
  error adding mozilla/Thawte_Personal_Freemail_CA.crt 
  error adding mozilla/Thawte_Personal_Premium_CA.crt 
  error adding mozilla/Thawte_Premium_Server_CA.crt 
  error adding mozilla/Thawte_Server_CA.crt 
  error adding mozilla/Thawte_Time_Stamping_CA.crt 
  error adding mozilla/UTN-USER_First-Network_Applications.crt 
  error adding mozilla/UTN_DATACorp_SGC_Root_CA.crt 
  error adding mozilla/UTN_USERFirst_Email_Root_CA.crt 
  error adding mozilla/UTN_USERFirst_Hardware_Root_CA.crt 
  error adding mozilla/ValiCert_Class_1_VA.crt 
  error adding mozilla/ValiCert_Class_2_VA.crt 
  error adding mozilla/VeriSign_Class_3_Public_Primary_Certification_Authority_-_G5.crt 
  error adding mozilla/Verisign_Class_1_Public_Primary_Certification_Authority.crt 
  error adding mozilla/Verisign_Class_1_Public_Primary_Certification_Authority_-_G2.crt 
  error adding mozilla/Verisign_Class_1_Public_Primary_Certification_Authority_-_G3.crt 
  error adding mozilla/Verisign_Class_2_Public_Primary_Certification_Authority.crt 
  error adding mozilla/Verisign_Class_2_Public_Primary_Certification_Authority_-_G2.crt 
  error adding mozilla/Verisign_Class_2_Public_Primary_Certification_Authority_-_G3.crt 
  error adding mozilla/Verisign_Class_3_Public_Primary_Certification_Authority.crt 
  error adding mozilla/Verisign_Class_3_Public_Primary_Certification_Authority_-_G2.crt 
  error adding mozilla/Verisign_Class_3_Public_Primary_Certification_Authority_-_G3.crt 
  error adding mozilla/Verisign_Class_4_Public_Primary_Certification_Authority_-_G2.crt 
  error adding mozilla/Verisign_Class_4_Public_Primary_Certification_Authority_-_G3.crt 
  error adding mozilla/Verisign_RSA_Secure_Server_CA.crt 
  error adding mozilla/Verisign_Time_Stamping_Authority_CA.crt 
  error adding mozilla/Visa_International_Global_Root_2.crt 
  error adding mozilla/Visa_eCommerce_Root.crt 
  error adding mozilla/WellsSecure_Public_Root_Certificate_Authority.crt 
  error adding mozilla/Wells_Fargo_Root_CA.crt 
  error adding mozilla/XRamp_Global_CA_Root.crt 
  error adding mozilla/beTRUSTed_Root_CA-Baltimore_Implementation.crt 
  error adding mozilla/beTRUSTed_Root_CA.crt 
  error adding mozilla/beTRUSTed_Root_CA_-_Entrust_Implementation.crt 
  error adding mozilla/beTRUSTed_Root_CA_-_RSA_Implementation.crt 
  error adding mozilla/thawte_Primary_Root_CA.crt 
  error adding signet.pl/signet_ca1_pem.crt 
  error adding signet.pl/signet_ca2_pem.crt 
  error adding signet.pl/signet_ca3_pem.crt 
  error adding signet.pl/signet_ocspklasa2_pem.crt 
  error adding signet.pl/signet_ocspklasa3_pem.crt 
  error adding signet.pl/signet_pca2_pem.crt 
  error adding signet.pl/signet_pca3_pem.crt 
  error adding signet.pl/signet_rootca_pem.crt 
  error adding signet.pl/signet_tsa1_pem.crt 
  error adding spi-inc.org/spi-ca-2003.crt 
  error adding spi-inc.org/spi-cacert-2008.crt 
  error adding telesec.de/deutsche-telekom-root-ca-2.crt 
failed. 
dpkg: error processing ca-certificates-java (--configure): 
 subprocess installed post-installation script returned error exit status 1 
Setting up libswscale0 (4:0.5+svn20090706-2ubuntu2.2) ... 
dpkg (subprocess): unable to execute installed post-installation script: Exec format error 
dpkg: error processing libswscale0 (--configure): 
 subprocess installed post-installation script returned error exit status 2 
dpkg: dependency problems prevent configuration of libcv1: 
 libcv1 depends on libswscale0 (>= 3:0.svn20090303-1) | libswscale-extra-0 (>= 3:0.svn20090303-1); however: 
  Package libswscale0 is not configured yet. 
  Package libswscale-extra-0 is not installed. 
dpkg: error processing libcv1 (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of libcvaux1: 
 libcvaux1 depends on libcv1; however: 
  Package libcv1 is not configured yet. 
 libcvaux1 depends on libswscale0 (>= 3:0.svn20090303-1) | libswscale-extra-0 (>= 3:0.svn20090303-1); however: 
  Package libswscale0 is not configured yet. 
  Package libswscale-extra-0 is not installed. 
dpkg: error processing libcvaux1 (--configure): 
 dependency problems - leaving unconfigured 
SettinNo apport report written because the error message indicates its a followup error from a previous failure.
No apport report written because MaxReports is reached already
g up libfftw3-3 (3.2.1-2ubuntu2) ... 
dpkg (subprocess): unable to execute installed post-installation script: Exec format error 
dpkg: error processing libfftw3-3 (--configure): 
 subprocess installed post-installation script returned error exit status 2 
dpkg: dependency problems prevent configuration of libhighgui1: 
 libhighgui1 depends on libcv1; however: 
  Package libcv1 is not configured yet. 
 libhighgui1 depends on libswscale0 (>= 3:0.svn20090303-1) | libswscale-extra-0 (>= 3:0.svn20090303-1); however: 
  Package libswscale0 is not configured yet. 
  Package libswscale-extra-0 is not installed. 
dpkg: error processing libhighgui1 (--configure): 
 dependency problems - leaving unconfigured 
Setting up liblapack3gf (3.2.1-1) ... 
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
dpkg (subprocess): unable to execute installed post-installation script: Exec format error 
dpkg: error processing liblapack3gf (--configure): 
 subprocess installed post-installation script returned error exit status 2 
Setting up libmatio0 (1.3.3-4) ... 
No apport report written because MaxReports is reached already
dpkg (subprocess): unable to execute installed post-installation script: Exec format error 
dpkg: error processing libmatio0 (--configure): 
 subprocess installed post-installation script returned error exit status 2 
Setting up libruby1.8 (1.8.7.174-1ubuntu1) ... 
No apport report written because MaxReports is reached already
dpkg (subprocess): unable to execute installed post-installation script: Exec format error 
dpkg: error processing libruby1.8 (--configure): 
 subprocess installed post-installation script returned error exit status 2 
Setting up libumfpack5.4.0 (1:3.4.0-1ubuntu2) ... 
No apport report written because MaxReports is reached already
dpkg (subprocess): unable to execute installed post-installation script: Exec format error 
dpkg: error processing libumfpack5.4.0 (--configure): 
 subprocess installed post-installation script returned error exit status 2 
dpkg: dependency problems prevent configuration of python-numpy: 
 python-numpy depends on liblapack3gf | liblapack.so.3gf | libatlas3gf-base; however: 
  Package liblapack3gf is not configured yet. 
  Package liblapack.so.3gf is not installed. 
  Package liblapack3gf which provides liblapack.so.3gf is not configured yet. 
  Package libatlas3gf-base is not installed. 
dpkg: error processing python-numpy (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of python-pygame: 
 python-pygame depends on python-numpy; however: 
  Package python-numpy is not configured yet. 
dpkg: error processing python-pygame (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of lightyears: 
 lightNo apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
years depends on python-pygame (>= 1.7); however: 
  Package python-pygame is not configured yet. 
dpkg: error processing lightyears (--configure): 
 dependency problems - leaving unconfigured 
Setting up rhino (1.7R2-1ubuntu1) ... 
dpkg (subprocess): unable to execute installed post-installation script: Exec format error 
dpkg: error processing rhino (--configure): 
 subprocess installed post-installation script returned error exit status 2 
dpkg: dependency problems prevent configuration of ruby1.8: 
 ruby1.8 depends on libruby1.8 (>= 1.8.7.174); however: 
  Package libruby1.8 is not configured yet. 
dpkg: error processing ruby1.8 (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of ruby: 
 ruby depends on ruby1.8; however: 
  Package ruby1.8 is not configured yet. 
dpkg: error processing ruby (--configure): 
 dependency problems - leaving unconfigured 
Setting up tcl8.5 (8.5.7-1) ... 
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
dpkg (subprocess): unable to execute installed post-installation script: Exec format error 
dpkg: error processing tcl8.5 (--configure): 
 subprocess installed post-installation script returned error exit status 2 
dpkg: dependency problems prevent configuration of tk8.5: 
 tk8.5 depends on tcl8.5 (>= 8.5.0); however: 
  Package tcl8.5 is not configured yet. 
dpkg: error processing tk8.5 (--configure): 
 dependency problems - leaving unconfigured 
Setting up libpvm3 (3.4.5-12) ... 
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
dpkg (subprocess): unable to execute installed post-installation script: Exec format error 
dpkg: error processing libpvm3 (--configure): 
 subprocess installed post-installation script returned error exit status 2 
Setting up axel (2.4-1) ... 
No apport report written because MaxReports is reached already
Setting up libqt3-mt (3:3.3.8-b-5ubuntu3) ... 
 
Setting up kaptain (1:0.72-3) ... 
Setting up axel-kapt (2.4-1) ... 
 
Processing triggers for libc-bin ... 
ldconfig deferred processing now taking place 
/sbin/ldconfig.real: File /usr/lib/libpvm3.so.3.4.5 is empty, not checked. 
/sbin/ldconfig.real: File /usr/lib/libhighgui.so.1.0.0 is empty, not checked. 
/sbin/ldconfig.real: File /usr/lib/libfftw3.so.3 is empty, not checked. 
/sbin/ldconfig.real: File /usr/lib/libumfpack.so.5.4.0 is empty, not checked. 
/sbin/ldconfig.real: File /usr/lib/libhighgui.so.1 is empty, not checked. 
/sbin/ldconfig.real: File /usr/lib/libmatio.so.0.0.0 is empty, not checked. 
/sbin/ldconfig.real: file /usr/lib/libavcodec.so.52.20.0 is truncated 
 
/sbin/ldconfig.real: File /usr/lib/libml.so.1 is empty, not checked. 
/sbin/ldconfig.real: File /usr/lib/libfftw3f.so.3 is empty, not checked. 
/sbin/ldconfig.real: File /usr/lib/libruby1.8.so.1.8 is empty, not checked. 
/sbin/ldconfig.real: File /usr/lib/libcxcore.so.1 is empty, not checked. 
/sbin/ldconfig.real: File /usr/lib/libcvaux.so.1.0.0 is empty, not checked. 
/sbin/ldconfig.real: File /usr/lib/libfftw3l_threads.so.3 is empty, not checked. 
/sbin/ldconfig.real: File /usr/lib/libfftw3.so.3.2.3 is empty, not checked. 
/sbin/ldconfig.real: File /usr/lib/liblapack.so.3gf is empty, not checked. 
/sbin/ldconfig.real: File /usr/lib/libcv.so.1.0.0 is empty, not checked. 
/sbin/ldconfig.real: File /usr/lib/liblapack.so.3gf.0 is empty, not checked. 
/sbin/ldconfig.real: File /usr/lib/libtcl8.5.so.0 is empty, not checked. 
/sbin/ldconfig.real: File /usr/lib/libswscale.so.0.7.1 is empty, not checked. 
/sbin/ldconfig.real: File /usr/lib/libfftw3f_threads.so.3 is empty, not checked. 
/sbin/ldconfig.real: File /usr/lib/libfftw3_threads.so.3.2.3 is empty, not checked. 
/sbin/ldconfig.real: file /usr/lib/libavcodec.so.52 is truncated 
 
/sbin/ldconfig.real: File /usr/lib/libcvaux.so.1 is empty, not checked. 
/sbin/ldconfig.real: File /usr/lib/libgpvm3.so.3 is empty, not checked. 
/sbin/ldconfig.real: File /usr/lib/libfftw3f.so.3.2.3 is empty, not checked. 
/sbin/ldconfig.real: File /usr/lib/libswscale.so.0 is empty, not checked. 
/sbin/ldconfig.real: File /usr/lib/libcv.so.1 is empty, not checked. 
/sbin/ldconfig.real: File /usr/lib/libmatio.so.0 is empty, not checked. 
/sbin/ldconfig.real: File /usr/lib/libpvm3.so.3 is empty, not checked. 
/sbin/ldconfig.real: File /usr/lib/libruby1.8.so.1.8.7 is empty, not checked. 
/sbin/ldconfig.real: File /usr/lib/libblas.so.3gf is empty, not checked. 
/sbin/ldconfig.real: File /usr/lib/libcxcore.so.1.0.0 is empty, not checked. 
/sbin/ldconfig.real: File /usr/lib/libfftw3l.so.3.2.3 is empty, not checked. 
/sbin/ldconfig.real: File /usr/lib/libfftw3f_threads.so.3.2.3 is empty, not checked. 
/sbin/ldconfig.real: File /usr/lib/libml.so.1.0.0 is empty, not checked. 
/sbin/ldconfig.real: File /usr/lib/libtk8.5.so.0 is empty, not checked. 
/sbin/ldconfig.real: File /usr/lib/libgpvm3.so.3.4.5 is empty, not checked. 
/sbin/ldconfig.real: File /usr/lib/libfftw3_threads.so.3 is empty, not checked. 
/sbin/ldconfig.real: File /usr/lib/libfftw3l.so.3 is empty, not checked. 
/sbin/ldconfig.real: File /usr/lib/libblas.so.3gf.0 is empty, not checked. 
/sbin/ldconfig.real: File /usr/lib/libfftw3l_threads.so.3.2.3 is empty, not checked. 
/sbin/ldconfig.real: File /usr/lib/i686/cmov/libswscale.so.0.7.1 is empty, not checked. 
/sbin/ldconfig.real: File /usr/lib/i686/cmov/libswscale.so.0 is empty, not checked. 
Errors were encountered while processing: 
 ca-certificates-java 
 libswscale0 
 libcv1 
 libcvaux1 
 libfftw3-3 
 libhighgui1 
 liblapack3gf 
 libmatio0 
 libruby1.8 
 libumfpack5.4.0 
 python-numpy 
 python-pygame 
 lightyears 
 rhino 
 ruby1.8 
 ruby 
 tcl8.5 
 tk8.5 
 libpvm3 




Any suggestions now guys?

---

### Post by twdurdentwd on 2010-09-28
Then, I try to install the adobe flash player, along with these error details:

E: ca-certificates-java: subprocess installed post-installation script returned error exit status 1
E: libswscale0: subprocess installed post-installation script returned error exit status 2
E: libcv1: dependency problems - leaving unconfigured
E: libcvaux1: dependency problems - leaving unconfigured
E: libfftw3-3: subprocess installed post-installation script returned error exit status 2
E: libhighgui1: dependency problems - leaving unconfigured
E: liblapack3gf: subprocess installed post-installation script returned error exit status 2
E: libmatio0: subprocess installed post-installation script returned error exit status 2
E: libruby1.8: subprocess installed post-installation script returned error exit status 2
E: libumfpack5.4.0: subprocess installed post-installation script returned error exit status 2
E: python-numpy: dependency problems - leaving unconfigured
E: python-pygame: dependency problems - leaving unconfigured
E: lightyears: dependency problems - leaving unconfigured
E: rhino: subprocess installed post-installation script returned error exit status 2
E: ruby1.8: dependency problems - leaving unconfigured
E: ruby: dependency problems - leaving unconfigured
E: tcl8.5: subprocess installed post-installation script returned error exit status 2
E: tk8.5: dependency problems - leaving unconfigured
E: libpvm3: subprocess installed post-installation script returned error exit status 2

---

### Post by ibuclaw on 2010-10-01
Please don't hijack, or raise an old thread from the dead.

Closed.

---

