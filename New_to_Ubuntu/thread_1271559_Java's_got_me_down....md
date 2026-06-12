---
title: "Java's got me down..."
date: 2009-09-21
forum: New to Ubuntu
---

### Post by flamefury on 2009-09-21
Trying to fix my sound...I figured updating the ALSA drivers was a worth it attempt.

Unfortunately, any time I try to do it, Java spits up this HUGE pile of errors. I try to update Java and it gives the SAME huge pile of errors. I'll cut paste:
```
Setting up ca-certificates-java (20081028) ...
creating /etc/ssl/certs/java/cacerts...
Error occurred during initialization of VM
java/lang/NoClassDefFoundError: java/lang/Object
  error adding brasil.gov.br/brasil.gov.br.crt
Error occurred during initialization of VM
java/lang/NoClassDefFoundError: java/lang/Object
  error adding cacert.org/cacert.org.crt
Error occurred during initialization of VM
java/lang/NoClassDefFoundError: java/lang/Object
  error adding cacert.org/class3.crt
Error occurred during initialization of VM
java/lang/NoClassDefFoundError: java/lang/Object
  error adding cacert.org/root.crt
Error occurred during initialization of VM
java/lang/NoClassDefFoundError: java/lang/Object
  error adding debconf.org/ca.crt
Error occurred during initialization of VM
java/lang/NoClassDefFoundError: java/lang/Object
  error adding gouv.fr/cert_igca_dsa.crt
Error occurred during initialization of VM
java/lang/NoClassDefFoundError: java/lang/Object
  error adding gouv.fr/cert_igca_rsa.crt
Error occurred during initialization of VM
java/lang/NoClassDefFoundError: java/lang/Object
  error adding mozilla/ABAecom_=sub.__Am._Bankers_Assn.=_Root_CA.crt
Error occurred during initialization of VM
java/lang/NoClassDefFoundError: java/lang/Object
  error adding mozilla/AOL_Time_Warner_Root_Certification_Authority_1.crt
Error occurred during initialization of VM
java/lang/NoClassDefFoundError: java/lang/Object
  error adding mozilla/AOL_Time_Warner_Root_Certification_Authority_2.crt
Error occurred during initialization of VM
java/lang/NoClassDefFoundError: java/lang/Object
  error adding mozilla/AddTrust_External_Root.crt
Error occurred during initialization of VM
java/lang/NoClassDefFoundError: java/lang/Object
  error adding mozilla/AddTrust_Low-Value_Services_Root.crt
Error occurred during initialization of VM
java/lang/NoClassDefFoundError: java/lang/Object
  error adding mozilla/AddTrust_Public_Services_Root.crt
Error occurred during initialization of VM
java/lang/NoClassDefFoundError: java/lang/Object
  error adding mozilla/AddTrust_Qualified_Certificates_Root.crt
Error occurred during initialization of VM
java/lang/NoClassDefFoundError: java/lang/Object
  error adding mozilla/America_Online_Root_Certification_Authority_1.crt
Error occurred during initialization of VM
java/lang/NoClassDefFoundError: java/lang/Object
  error adding mozilla/America_Online_Root_Certification_Authority_2.crt
Error occurred during initialization of VM
java/lang/NoClassDefFoundError: java/lang/Object
  error adding mozilla/Baltimore_CyberTrust_Root.crt
Error occurred during initialization of VM
java/lang/NoClassDefFoundError: java/lang/Object
  error adding mozilla/COMODO_Certification_Authority.crt
Error occurred during initialization of VM
java/lang/NoClassDefFoundError: java/lang/Object
  error adding mozilla/Camerfirma_Chambers_of_Commerce_Root.crt
Error occurred during initialization of VM
java/lang/NoClassDefFoundError: java/lang/Object
  error adding mozilla/Camerfirma_Global_Chambersign_Root.crt
Error occurred during initialization of VM
java/lang/NoClassDefFoundError: java/lang/Object
  error adding mozilla/Certplus_Class_2_Primary_CA.crt
Error occurred during initialization of VM
java/lang/NoClassDefFoundError: java/lang/Object
  error adding mozilla/Certum_Root_CA.crt
Error occurred during initialization of VM
java/lang/NoClassDefFoundError: java/lang/Object
  error adding mozilla/Comodo_AAA_Services_root.crt
Error occurred during initialization of VM
java/lang/NoClassDefFoundError: java/lang/Object
  error adding mozilla/Comodo_Secure_Services_root.crt
Error occurred during initialization of VM
java/lang/NoClassDefFoundError: java/lang/Object
  error adding mozilla/Comodo_Trusted_Services_root.crt
Error occurred during initialization of VM
java/lang/NoClassDefFoundError: java/lang/Object
  error adding mozilla/DST_ACES_CA_X6.crt
Error occurred during initialization of VM
java/lang/NoClassDefFoundError: java/lang/Object
  error adding mozilla/DST_Root_CA_X3.crt
Error occurred during initialization of VM
java/lang/NoClassDefFoundError: java/lang/Object
  error adding mozilla/DigiCert_Assured_ID_Root_CA.crt
Error occurred during initialization of VM
java/lang/NoClassDefFoundError: java/lang/Object
  error adding mozilla/DigiCert_Global_Root_CA.crt
Error occurred during initialization of VM
java/lang/NoClassDefFoundError: java/lang/Object
  error adding mozilla/DigiCert_High_Assurance_EV_Root_CA.crt
Error occurred during initialization of VM
java/lang/NoClassDefFoundError: java/lang/Object
  error adding mozilla/Digital_Signature_Trust_Co._Global_CA_1.crt
Error occurred during initialization of VM
java/lang/NoClassDefFoundError: java/lang/Object
  error adding mozilla/Digital_Signature_Trust_Co._Global_CA_2.crt
Error occurred during initialization of VM
java/lang/NoClassDefFoundError: java/lang/Object
  error adding mozilla/Digital_Signature_Trust_Co._Global_CA_3.crt
Error occurred during initialization of VM
java/lang/NoClassDefFoundError: java/lang/Object
  error adding mozilla/Digital_Signature_Trust_Co._Global_CA_4.crt
Error occurred during initialization of VM
java/lang/NoClassDefFoundError: java/lang/Object
  error adding mozilla/Entrust.net_Global_Secure_Personal_CA.crt
Error occurred during initialization of VM
java/lang/NoClassDefFoundError: java/lang/Object
  error adding mozilla/Entrust.net_Global_Secure_Server_CA.crt
Error occurred during initialization of VM
java/lang/NoClassDefFoundError: java/lang/Object
  error adding mozilla/Entrust.net_Premium_2048_Secure_Server_CA.crt
Error occurred during initialization of VM
java/lang/NoClassDefFoundError: java/lang/Object
  error adding mozilla/Entrust.net_Secure_Personal_CA.crt
Error occurred during initialization of VM
java/lang/NoClassDefFoundError: java/lang/Object
  error adding mozilla/Entrust.net_Secure_Server_CA.crt
Error occurred during initialization of VM
java/lang/NoClassDefFoundError: java/lang/Object
  error adding mozilla/Entrust_Root_Certification_Authority.crt
Error occurred during initialization of VM
java/lang/NoClassDefFoundError: java/lang/Object
  error adding mozilla/Equifax_Secure_CA.crt
Error occurred during initialization of VM
java/lang/NoClassDefFoundError: java/lang/Object
  error adding mozilla/Equifax_Secure_Global_eBusiness_CA.crt
Error occurred during initialization of VM
java/lang/NoClassDefFoundError: java/lang/Object
  error adding mozilla/Equifax_Secure_eBusiness_CA_1.crt
Error occurred during initialization of VM
java/lang/NoClassDefFoundError: java/lang/Object
  error adding mozilla/Equifax_Secure_eBusiness_CA_2.crt
Error occurred during initialization of VM
java/lang/NoClassDefFoundError: java/lang/Object
  error adding mozilla/Firmaprofesional_Root_CA.crt
Error occurred during initialization of VM
java/lang/NoClassDefFoundError: java/lang/Object
  error adding mozilla/GTE_CyberTrust_Global_Root.crt
Error occurred during initialization of VM
java/lang/NoClassDefFoundError: java/lang/Object
  error adding mozilla/GTE_CyberTrust_Root_CA.crt
Error occurred during initialization of VM
java/lang/NoClassDefFoundError: java/lang/Object
  error adding mozilla/GeoTrust_Global_CA.crt
Error occurred during initialization of VM
java/lang/NoClassDefFoundError: java/lang/Object
  error adding mozilla/GeoTrust_Global_CA_2.crt
Error occurred during initialization of VM
java/lang/NoClassDefFoundError: java/lang/Object
  error adding mozilla/GeoTrust_Primary_Certification_Authority.crt
Error occurred during initialization of VM
java/lang/NoClassDefFoundError: java/lang/Object
  error adding mozilla/GeoTrust_Universal_CA.crt
Error occurred during initialization of VM
java/lang/NoClassDefFoundError: java/lang/Object
  error adding mozilla/GeoTrust_Universal_CA_2.crt
Error occurred during initialization of VM
java/lang/NoClassDefFoundError: java/lang/Object
  error adding mozilla/GlobalSign_Root_CA.crt
Error occurred during initialization of VM
java/lang/NoClassDefFoundError: java/lang/Object
  error adding mozilla/GlobalSign_Root_CA_-_R2.crt
Error occurred during initialization of VM
java/lang/NoClassDefFoundError: java/lang/Object
  error adding mozilla/Go_Daddy_Class_2_CA.crt
Error occurred during initialization of VM
java/lang/NoClassDefFoundError: java/lang/Object
  error adding mozilla/IPS_CLASE1_root.crt
Error occurred during initialization of VM
java/lang/NoClassDefFoundError: java/lang/Object
  error adding mozilla/IPS_CLASE3_root.crt
Error occurred during initialization of VM
java/lang/NoClassDefFoundError: java/lang/Object
  error adding mozilla/IPS_CLASEA1_root.crt
Error occurred during initialization of VM
java/lang/NoClassDefFoundError: java/lang/Object
  error adding mozilla/IPS_CLASEA3_root.crt
Error occurred during initialization of VM
java/lang/NoClassDefFoundError: java/lang/Object
  error adding mozilla/IPS_Chained_CAs_root.crt
Error occurred during initialization of VM
java/lang/NoClassDefFoundError: java/lang/Object
  error adding mozilla/IPS_Servidores_root.crt
Error occurred during initialization of VM
java/lang/NoClassDefFoundError: java/lang/Object
  error adding mozilla/IPS_Timestamping_root.crt
Error occurred during initialization of VM
java/lang/NoClassDefFoundError: java/lang/Object
  error adding mozilla/NetLock_Business_=Class_B=_Root.crt
Error occurred during initialization of VM
java/lang/NoClassDefFoundError: java/lang/Object
  error adding mozilla/NetLock_Express_=Class_C=_Root.crt
Error occurred during initialization of VM
java/lang/NoClassDefFoundError: java/lang/Object
  error adding mozilla/NetLock_Notary_=Class_A=_Root.crt
Error occurred during initialization of VM
java/lang/NoClassDefFoundError: java/lang/Object
  error adding mozilla/NetLock_Qualified_=Class_QA=_Root.crt
Error occurred during initialization of VM
java/lang/NoClassDefFoundError: java/lang/Object
  error adding mozilla/QuoVadis_Root_CA.crt
Error occurred during initialization of VM
java/lang/NoClassDefFoundError: java/lang/Object
  error adding mozilla/QuoVadis_Root_CA_2.crt
Error occurred during initialization of VM
java/lang/NoClassDefFoundError: java/lang/Object
  error adding mozilla/QuoVadis_Root_CA_3.crt
Error occurred during initialization of VM
java/lang/NoClassDefFoundError: java/lang/Object
  error adding mozilla/RSA_Root_Certificate_1.crt
Error occurred during initialization of VM
java/lang/NoClassDefFoundError: java/lang/Object
  error adding mozilla/RSA_Security_1024_v3.crt
Error occurred during initialization of VM
java/lang/NoClassDefFoundError: java/lang/Object
  error adding mozilla/RSA_Security_2048_v3.crt
Error occurred during initialization of VM
java/lang/NoClassDefFoundError: java/lang/Object
  error adding mozilla/SecureTrust_CA.crt
Error occurred during initialization of VM
java/lang/NoClassDefFoundError: java/lang/Object
  error adding mozilla/Secure_Global_CA.crt
Error occurred during initialization of VM
java/lang/NoClassDefFoundError: java/lang/Object
  error adding mozilla/Security_Communication_Root_CA.crt
Error occurred during initialization of VM
java/lang/NoClassDefFoundError: java/lang/Object
  error adding mozilla/Sonera_Class_1_Root_CA.crt
Error occurred during initialization of VM
java/lang/NoClassDefFoundError: java/lang/Object
  error adding mozilla/Sonera_Class_2_Root_CA.crt
Error occurred during initialization of VM
java/lang/NoClassDefFoundError: java/lang/Object
  error adding mozilla/Staat_der_Nederlanden_Root_CA.crt
Error occurred during initialization of VM
java/lang/NoClassDefFoundError: java/lang/Object
  error adding mozilla/Starfield_Class_2_CA.crt
Error occurred during initialization of VM
java/lang/NoClassDefFoundError: java/lang/Object
  error adding mozilla/StartCom_Certification_Authority.crt
Error occurred during initialization of VM
java/lang/NoClassDefFoundError: java/lang/Object
  error adding mozilla/StartCom_Ltd..crt
Error occurred during initialization of VM
java/lang/NoClassDefFoundError: java/lang/Object
  error adding mozilla/SwissSign_Gold_CA_-_G2.crt
Error occurred during initialization of VM
java/lang/NoClassDefFoundError: java/lang/Object
  error adding mozilla/SwissSign_Platinum_CA_-_G2.crt
Error occurred during initialization of VM
java/lang/NoClassDefFoundError: java/lang/Object
  error adding mozilla/SwissSign_Silver_CA_-_G2.crt
Error occurred during initialization of VM
java/lang/NoClassDefFoundError: java/lang/Object
  error adding mozilla/Swisscom_Root_CA_1.crt
Error occurred during initialization of VM
java/lang/NoClassDefFoundError: java/lang/Object
  error adding mozilla/TC_TrustCenter__Germany__Class_2_CA.crt
Error occurred during initialization of VM
java/lang/NoClassDefFoundError: java/lang/Object
  error adding mozilla/TC_TrustCenter__Germany__Class_3_CA.crt
Error occurred during initialization of VM
java/lang/NoClassDefFoundError: java/lang/Object
  error adding mozilla/TDC_Internet_Root_CA.crt
Error occurred during initialization of VM
java/lang/NoClassDefFoundError: java/lang/Object
  error adding mozilla/TDC_OCES_Root_CA.crt
Error occurred during initialization of VM
java/lang/NoClassDefFoundError: java/lang/Object
  error adding mozilla/TURKTRUST_Certificate_Services_Provider_Root_1.crt
Error occurred during initialization of VM
java/lang/NoClassDefFoundError: java/lang/Object
  error adding mozilla/TURKTRUST_Certificate_Services_Provider_Root_2.crt
Error occurred during initialization of VM
java/lang/NoClassDefFoundError: java/lang/Object
  error adding mozilla/Taiwan_GRCA.crt
Error occurred during initialization of VM
java/lang/NoClassDefFoundError: java/lang/Object
  error adding mozilla/Thawte_Personal_Basic_CA.crt
Error occurred during initialization of VM
java/lang/NoClassDefFoundError: java/lang/Object
  error adding mozilla/Thawte_Personal_Freemail_CA.crt
Error occurred during initialization of VM
java/lang/NoClassDefFoundError: java/lang/Object
  error adding mozilla/Thawte_Personal_Premium_CA.crt
Error occurred during initialization of VM
java/lang/NoClassDefFoundError: java/lang/Object
  error adding mozilla/Thawte_Premium_Server_CA.crt
Error occurred during initialization of VM
java/lang/NoClassDefFoundError: java/lang/Object
  error adding mozilla/Thawte_Server_CA.crt
Error occurred during initialization of VM
java/lang/NoClassDefFoundError: java/lang/Object
  error adding mozilla/Thawte_Time_Stamping_CA.crt
Error occurred during initialization of VM
java/lang/NoClassDefFoundError: java/lang/Object
  error adding mozilla/UTN-USER_First-Network_Applications.crt
Error occurred during initialization of VM
java/lang/NoClassDefFoundError: java/lang/Object
  error adding mozilla/UTN_DATACorp_SGC_Root_CA.crt
Error occurred during initialization of VM
java/lang/NoClassDefFoundError: java/lang/Object
  error adding mozilla/UTN_USERFirst_Email_Root_CA.crt
Error occurred during initialization of VM
java/lang/NoClassDefFoundError: java/lang/Object
  error adding mozilla/UTN_USERFirst_Hardware_Root_CA.crt
Error occurred during initialization of VM
java/lang/NoClassDefFoundError: java/lang/Object
  error adding mozilla/UTN_USERFirst_Object_Root_CA.crt
Error occurred during initialization of VM
java/lang/NoClassDefFoundError: java/lang/Object
  error adding mozilla/ValiCert_Class_1_VA.crt
Error occurred during initialization of VM
java/lang/NoClassDefFoundError: java/lang/Object
  error adding mozilla/ValiCert_Class_2_VA.crt
Error occurred during initialization of VM
java/lang/NoClassDefFoundError: java/lang/Object
  error adding mozilla/VeriSign_Class_3_Public_Primary_Certification_Authority_-_G5.crt
Error occurred during initialization of VM
java/lang/NoClassDefFoundError: java/lang/Object
  error adding mozilla/Verisign_Class_1_Public_Primary_Certification_Authority.crt
Error occurred during initialization of VM
java/lang/NoClassDefFoundError: java/lang/Object
  error adding mozilla/Verisign_Class_1_Public_Primary_Certification_Authority_-_G2.crt
Error occurred during initialization of VM
java/lang/NoClassDefFoundError: java/lang/Object
  error adding mozilla/Verisign_Class_1_Public_Primary_Certification_Authority_-_G3.crt
Error occurred during initialization of VM
java/lang/NoClassDefFoundError: java/lang/Object
  error adding mozilla/Verisign_Class_2_Public_Primary_Certification_Authority.crt
Error occurred during initialization of VM
java/lang/NoClassDefFoundError: java/lang/Object
  error adding mozilla/Verisign_Class_2_Public_Primary_Certification_Authority_-_G2.crt
Error occurred during initialization of VM
java/lang/NoClassDefFoundError: java/lang/Object
  error adding mozilla/Verisign_Class_2_Public_Primary_Certification_Authority_-_G3.crt
Error occurred during initialization of VM
java/lang/NoClassDefFoundError: java/lang/Object
  error adding mozilla/Verisign_Class_3_Public_Primary_Certification_Authority.crt
Error occurred during initialization of VM
java/lang/NoClassDefFoundError: java/lang/Object
  error adding mozilla/Verisign_Class_3_Public_Primary_Certification_Authority_-_G2.crt
Error occurred during initialization of VM
java/lang/NoClassDefFoundError: java/lang/Object
  error adding mozilla/Verisign_Class_3_Public_Primary_Certification_Authority_-_G3.crt
Error occurred during initialization of VM
java/lang/NoClassDefFoundError: java/lang/Object
  error adding mozilla/Verisign_Class_4_Public_Primary_Certification_Authority_-_G2.crt
Error occurred during initialization of VM
java/lang/NoClassDefFoundError: java/lang/Object
  error adding mozilla/Verisign_Class_4_Public_Primary_Certification_Authority_-_G3.crt
Error occurred during initialization of VM
java/lang/NoClassDefFoundError: java/lang/Object
  error adding mozilla/Verisign_RSA_Secure_Server_CA.crt
Error occurred during initialization of VM
java/lang/NoClassDefFoundError: java/lang/Object
  error adding mozilla/Verisign_Time_Stamping_Authority_CA.crt
Error occurred during initialization of VM
java/lang/NoClassDefFoundError: java/lang/Object
  error adding mozilla/Visa_International_Global_Root_2.crt
Error occurred during initialization of VM
java/lang/NoClassDefFoundError: java/lang/Object
  error adding mozilla/Visa_eCommerce_Root.crt
Error occurred during initialization of VM
java/lang/NoClassDefFoundError: java/lang/Object
  error adding mozilla/Wells_Fargo_Root_CA.crt
Error occurred during initialization of VM
java/lang/NoClassDefFoundError: java/lang/Object
  error adding mozilla/XRamp_Global_CA_Root.crt
Error occurred during initialization of VM
java/lang/NoClassDefFoundError: java/lang/Object
  error adding mozilla/beTRUSTed_Root_CA-Baltimore_Implementation.crt
Error occurred during initialization of VM
java/lang/NoClassDefFoundError: java/lang/Object
  error adding mozilla/beTRUSTed_Root_CA.crt
Error occurred during initialization of VM
java/lang/NoClassDefFoundError: java/lang/Object
  error adding mozilla/beTRUSTed_Root_CA_-_Entrust_Implementation.crt
Error occurred during initialization of VM
java/lang/NoClassDefFoundError: java/lang/Object
  error adding mozilla/beTRUSTed_Root_CA_-_RSA_Implementation.crt
Error occurred during initialization of VM
java/lang/NoClassDefFoundError: java/lang/Object
  error adding mozilla/thawte_Primary_Root_CA.crt
Error occurred during initialization of VM
java/lang/NoClassDefFoundError: java/lang/Object
  error adding quovadis.bm/QuoVadis_Root_Certification_Authority.crt
Error occurred during initialization of VM
java/lang/NoClassDefFoundError: java/lang/Object
  error adding signet.pl/signet_ca1_pem.crt
Error occurred during initialization of VM
java/lang/NoClassDefFoundError: java/lang/Object
  error adding signet.pl/signet_ca2_pem.crt
Error occurred during initialization of VM
java/lang/NoClassDefFoundError: java/lang/Object
  error adding signet.pl/signet_ca3_pem.crt
Error occurred during initialization of VM
java/lang/NoClassDefFoundError: java/lang/Object
  error adding signet.pl/signet_ocspklasa2_pem.crt
Error occurred during initialization of VM
java/lang/NoClassDefFoundError: java/lang/Object
  error adding signet.pl/signet_ocspklasa3_pem.crt
Error occurred during initialization of VM
java/lang/NoClassDefFoundError: java/lang/Object
  error adding signet.pl/signet_pca2_pem.crt
Error occurred during initialization of VM
java/lang/NoClassDefFoundError: java/lang/Object
  error adding signet.pl/signet_pca3_pem.crt
Error occurred during initialization of VM
java/lang/NoClassDefFoundError: java/lang/Object
  error adding signet.pl/signet_rootca_pem.crt
Error occurred during initialization of VM
java/lang/NoClassDefFoundError: java/lang/Object
  error adding signet.pl/signet_tsa1_pem.crt
Error occurred during initialization of VM
java/lang/NoClassDefFoundError: java/lang/Object
  error adding spi-inc.org/spi-ca-2003.crt
Error occurred during initialization of VM
java/lang/NoClassDefFoundError: java/lang/Object
  error adding spi-inc.org/spi-cacert-2008.crt
Error occurred during initialization of VM
java/lang/NoClassDefFoundError: java/lang/Object
  error adding telesec.de/deutsche-telekom-root-ca-2.crt
failed.
dpkg: error processing ca-certificates-java (--configure):
 subprocess post-installation script returned error exit status 1
Setting up odbcinst1debian1 (2.2.11-16build3) ...

Setting up unixodbc (2.2.11-16build3) ...

Setting up sun-java6-bin (6-16-0ubuntu1.9.04) ...
update-binfmts: warning: current package is openjdk-6, but binary format
already installed by ia32-sun-java6 

Setting up sun-java6-fonts (6-16-0ubuntu1.9.04) ...
No CIDSupplement specified for Batang-Bold, defaulting to 0.
No CIDSupplement specified for UMingCN, defaulting to 0.
No CIDSupplement specified for ZenHei-CNS, defaulting to 0.
No CIDSupplement specified for ZenHei, defaulting to 0.
No CIDSupplement specified for Batang-Regular, defaulting to 0.
No CIDSupplement specified for Dotum-Bold, defaulting to 0.
No CIDSupplement specified for Dotum-Regular, defaulting to 0.
Updating fontconfig cache for /usr/share/fonts/truetype/ttf-lucida

Setting up sun-java6-plugin (6-16-0ubuntu1.9.04) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 ca-certificates-java
E: Sub-process /usr/bin/dpkg returned an error code (1)

```
And I've no idea what any of this means...Is there a way to completely remove all components of Java then reinstall them?

---

### Post by inobe on 2009-09-21
hi

in synaptic search sun-java6-jre

you can remove it, see what's included' for example java common.

when removing see if all the dependencies get removed too.

may want to include your sound hardware and why you updated alsa drivers.

also include your

```
lspci
```

---

### Post by flamefury on 2009-09-21
Blargh, same list of errors, with a pop up of this at the end:```

E: ca-certificates-java: subprocess post-installation script returned error exit status 1
```Which appears at the end of the huge pile of stuff too. Uninstall AND install are both affected by whatever's causing this.

If you need to know, the situation came up when I followed the multimedia guide doing this:
```

**sudo apt-get remove gnash gnash-common libflashsupport mozilla-plugin-gnash swfdec-mozilla && sudo apt-get install alsa-oss faac faad flashplugin-nonfree gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse ia32-libs ia32-sun-java6-bin icedtea6-plugin libmp3lame0 non-free-codecs openjdk-6-jre unrar**
```The process was going fine until it hit a certain point about fonts and then my computer froze. I didn't have any other option, so I hard-resetted and now all my installs and uninstalls throw up that huge pile of RT.jar mess about certificates.

Oh, and for sound card stuff.
[B]aplay -l
```
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC663 Analog [ALC663 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC663 Digital [ALC663 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```[/B]
and
[B]lscpi
```
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:01.0 PCI bridge: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M-E LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation Device 062b (rev a1)
03:00.0 Network controller: Intel Corporation Wireless WiFi Link 5100
06:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
07:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
07:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
07:01.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
07:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
07:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
```[/B]

---

### Post by flamefury on 2009-09-21
Good news! I was able to get rid of the huge puke pile by extracting an installation whatchamahoozits from the Sun site and replacing the old (likely incomplete) rt.jar with a new one. It fixed up those wild installation errors.

Unfortunately, I can't run anything involving flash, anything involving Java will cause Firefox to stop responding and there's still no sound...I have Flash 10 installed, as well as Java, and I got the ALSA drivers updated too. Doesn't look like an easy fix...

I suspect it may be an issue with the browser I'm using. Flash is only known to work with 32-bit browsers, correct? How do I check what version of Firefox I'm using? The About page only has the Linux platform (x86_64, apparently...).

As far as sound goes...ugh. I don't even know what angle to take with this issue.

---

### Post by inobe on 2009-09-21
you can check firefox

```
dpkg -s firefox
```


let me do some research on this, i will try to help.

side note: 64bit issues with flash and java are likely "citation needed"


check back from time to time.

---

### Post by inobe on 2009-09-21
flamefury just browsing forum search i ran into this

[http://ubuntuforums.org/showthread.php?t=940689](http://ubuntuforums.org/showthread.php?t=940689)

now many have fixed their sound, some used different ways than others, i would consider reviewing this thread considering they all have the same chipset.

---

### Post by flamefury on 2009-09-22
Tried everything in that thread...nothing works. ;_;

Tried using one fix at a time, tried two at a time in different pairs, tried 'em all at once, nothing. Thanks for pointing that out, regardless.

---

