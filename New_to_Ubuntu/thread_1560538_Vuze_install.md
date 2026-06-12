---
title: "Vuze install"
date: 2010-08-25
forum: New to Ubuntu
---

### Post by brittanie on 2010-08-25
Hi. I am having trouble installing Vuze. Here is what the terminal said whe nI tried to install..
bunbunderson@bunbunderson-laptop:~$ sudo tar -xvjf Vuze_*.tar.bz2 -C /opt/
tar: Record size = 8 blocks
vuze/azureus
vuze/updateAzureus
vuze/vuze
tar: vuze/vuze: Cannot open: File exists
vuze/README.txt
vuze/TOS.txt
vuze/vuze.desktop
vuze/vuze.png
vuze/vuze.schemas
vuze/vuze.torrent.png
vuze/swt.jar
vuze/Azureus2.jar
vuze/installer.log
vuze/plugins/azplugins/
vuze/plugins/azrating/
vuze/plugins/azupdater/
vuze/plugins/azupnpav/
vuze/plugins/azplugins/azplugins_2.1.6.jar
vuze/plugins/azrating/azrating_1.3.1.jar
vuze/plugins/azupdater/Updater.jar
vuze/plugins/azupdater/azupdaterpatcher_1.8.16.jar
vuze/plugins/azupdater/azureus.sig
vuze/plugins/azupdater/plugin.properties
vuze/plugins/azupnpav/azupnpav_0.2.29.2.jar
vuze/plugins/azupnpav/azureus.sig
vuze/plugins/azupnpav/plugin.properties
tar: Exiting with failure status due to previous errors.

I am very new to Ubuntu. I ran Mandriva about 4 years ago, but much has changed since then . Any help will be greatly appreciated.

---

### Post by cjv8888 on 2010-08-25
Vuze is in the repositories.

---

### Post by brittanie on 2010-08-26
How do I find the repositories?

---

### Post by sikander3786 on 2010-08-26
Hi.

Either go to Applications >>> Software Center

OR

System >>> Administration >>> Synaptic Package Manager and search for Vuze and install.

OR

In terminal

***sudo apt-get install vuze***

That will do it.

---

### Post by brittanie on 2010-08-26
Sweet. Thanks!

---

### Post by cybercookie72 on 2010-10-09
but as with many programs in the repositories...it is outdated.

how can I get the repositories to keep up with the latest version of vuze or any program for that matter?

thanks for any help in advance...

---

### Post by sikander3786 on 2010-10-09
> **cybercookie72 said:**
> but as with many programs in the repositories...it is outdated.

how can I get the repositories to keep up with the latest version of vuze or any program for that matter?

thanks for any help in advance...
Only officially or atleast community supported software for relating *buntu release is present in the repositories.

[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

You can install new/unsupported versions by either downloading the source or *.deb from the relative official websites (there should also be installation instructions) or the other method is  by adding the testing PPAs.

[https://help.launchpad.net/Packaging/PPA](https://help.launchpad.net/Packaging/PPA)

For Vuze,

[http://www.khattam.info/howto-update-vuze-azureus-to-latest-version-4-5-in-ubuntu-10-10-maverick-meerkat-2010-09-10.html](http://www.khattam.info/howto-update-vuze-azureus-to-latest-version-4-5-in-ubuntu-10-10-maverick-meerkat-2010-09-10.html)

---

### Post by cybercookie72 on 2010-10-10
thank you very much for the help....

:KS


edit ::: worked great...

installed vuse from Software Center

then downloaded vuse installer zip from vuse site [http://www.vuze.com/download/](http://www.vuze.com/download/)

took vuse_4510.jar and swt.jar out of zip 

backed up Azureus2.jar and swt.jar in the /usr/share/java folder

then copied vuse_4510.jar (renaming it to Azureus2.jar) to /usr/share/java
and copied swt.jar to /usr/share/java

the Applications menu entry works to open vuse 4510 :) woot

all that wisdom is from the link sikander3786 shared 
[http://www.khattam.info/howto-update...010-09-10.html](http://www.khattam.info/howto-update...010-09-10.html)

---

