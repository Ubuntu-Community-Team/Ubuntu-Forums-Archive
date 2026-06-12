---
title: "Howto Huawei E220 connect using Python"
date: 2008-08-07
forum: Networking &amp; Wireless
---

### Post by jbb on 2008-08-07
Further to an ealier Howto get your Huawei E220 working on Gutsy 7.1 I am now able to offer a Howto for Hardy 8.04.  This was the result of a fopar by me when trying to create a new partition within my Ubuntu partition which wiped out said partition resulting in necessity being the driving force to get Ubuntu 8.04 up and internet up using  Huawei E220 modem 
Attached is the Howto.  I hope this helps all seeking help in this area.

The followng files are those that I found by trial and error to be added to Ubuntu 8.04 (Hardy) to enable the use of the Huawei E220 modem. This was determined by switching between WinXP for downloading and Ubuntu A reboot being required each time as my only internet access is via a Huawei E220, hence the need to swap between OS's.  I assume that this will probably also work with other variants of the Huawei modem, possibly needing changes in your setup data. I noticed that version of Vodafone driver stated below detected my supplier (vodacom sa ) without problem and only needed insertion of my pin code to function.
I tested the order mentioned below by reinstalling Ubuntu 8.04 ( a fresh install) then installing the files in given order  (I saved a copy of the files on download rather than to direct install, this allowed me to confirm the file order, and to have a backup should I again need to reinstall for any reason) 
Yes I know that Mandriva 2008.1 allows you select a Huawei device from the Internet menu but they use a different file system and scripts As I am not offey with them I chose to use the Python route. It may need more files but it is very easy to use and does not require knowledge of scripting to use.

Following are the files I used, the order in which I installed them.  

[http://packages.ubuntu.com/hardy/](http://packages.ubuntu.com/hardy/)

 1  - python/python-crypto_2.0.1+dfsg1-2ubuntu1_i386.deb
 2  - python/python-pysqlite2_2.3.4-2_i386.deb
 3  - python/python-serial_2.2-4_all.deb
 4  - python/python-twisted-bin_2.5.0-2build1_i386.deb
 5  - python/python-zopeinterface_3.3.1-3build2_i386.deb
 6  - python/python-twisted-core_2.5.0-2build1_all.deb
 7  - python/python-twisted-conch_0.8.0-1_all.deb
 8  - python/python-twisted-mail_0.4.0-1_all.deb
 9  - python/python-twisted-web_0.7.0-1_all.deb
 10 - python/python-twisted-lore_0.3.0-1_all.deb
 11 - python/python-twisted-names_0.4.0-1_all.deb
 12 - python/python-twisted-news_0.3.0-1_all.deb
 13 - python/python-twisted-runner_0.2.0-2_i386.deb
 14 - python/python-twisted-words_0.5.0-1.1_all.deb
 15 - python/python-twisted_2.5.0-2build1_all.deb
 16 - python/libgda3-common_3.0.1-1build2_all.deb
 17 - python/libgda3-3_3.0.1-1build2_i386.deb
 18 - python/libgdl-1-common_0.7.6-1_all.deb
 19 - python/libgdl-1-0_0.7.6-1_i386.deb
 20 - python/libgdl-gnome-1-0_0.7.6-1_i386.deb
 21 - python/libgksu1.2-1_1.3.8-1ubuntu3_i386.deb
 22 - python/libgksuui1.0-1_1.0.7-2ubuntu2_i386.deb
 23 - python/python-gnome2-extras_2.19.1-0ubuntu4_i386.deb
 24 - python/python2.4-minimal_2.4.4-6ubuntu4.2_i386.deb
 25 - python/libdb4.5_4.5.20-5ubuntu3_i386.deb
 26 - python/python2.4_2.4.4-6ubuntu4.2_i386.deb
 27 - python/python-tz_2007d-1_all.deb

[http://forge.vodafonebetavine.net](http://forge.vodafonebetavine.net)

    vodafone-mobile-connect-card-driver-for-linux_1.99.17_i386.deb

The startup screen with above driver is very different to that I used previously  ver 1.0   I tried the beta versions but found that they tended to hang my Laptop

---

