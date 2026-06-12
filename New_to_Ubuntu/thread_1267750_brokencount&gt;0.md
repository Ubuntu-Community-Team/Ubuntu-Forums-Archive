---
title: "brokencount&gt;0"
date: 2009-09-16
forum: New to Ubuntu
---

### Post by MelDJ on 2009-09-16
hi there.
yesterday update manager showed that there is an update fore firefox. i updated but it failed as a 404 error came up. now there are 2 broken packages in synaptic: firefox and firefox-3.5. removing either will force me to remove songbird. could anybody help me resolve this?

---

### Post by Mike_IronFist on 2009-09-16
> **MelDJ said:**
> hi there.
yesterday update manager showed that there is an update fore firefox. i updated but it failed as a 404 error came up. now there are 2 broken packages in synaptic: firefox and firefox-3.5. removing either will force me to remove songbird. could anybody help me resolve this?

Your settings for Songbird are actually saved in a hidden file within your home folder, so if you remove Songbird, you can reinstall it again after you remove and/or reinstall Firefox - you won't lose any settings for your music or anything like that.

---

### Post by MelDJ on 2009-09-16
really? wow. thanks. was really scared of losing all the data for my music:lolflag:

---

### Post by MelDJ on 2009-09-16
i removed firefox 3.5 and firefox form synaptic. i then tried reinstalling songbird but it says that it needs firefox 3.5 and firefox. i tried installing firefox 3.5 using ubuntuzilla but that did no work too..help pls..

---

### Post by MelDJ on 2009-09-16
using hardy by the way

---

### Post by nanotube on 2009-09-16
do you get any errors when you run "sudo apt-get update" or "sudo apt-get install firefox" ? if so, post your output here.

---

### Post by MelDJ on 2009-09-16
for sudo apt-get update:
W: Duplicate sources.list entry [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages (/var/lib/apt/lists/ppa.launchpad.net_gnome-colors-packagers_ppa_ubuntu_dists_hardy_main_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems

for sudo apt-get install firefox:
Unpacking firefox-3.5-branding (from .../firefox-3.5-branding_3.5.4~hg20090914r26358+nobinonly-0ubuntu1~umd1~hardy_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/firefox-3.5-branding_3.5.4~hg20090914r26358+nobinonly-0ubuntu1~umd1~hardy_i386.deb (--unpack):
 trying to overwrite `/usr/share/applications/firefox.desktop', which is also in package firefox-3.0
Selecting previously deselected package firefox-3.5.
Unpacking firefox-3.5 (from .../firefox-3.5_3.5.4~hg20090914r26358+nobinonly-0ubuntu1~umd1~hardy_i386.deb) ...
Selecting previously deselected package firefox.
Unpacking firefox (from .../firefox_3.5.4~hg20090914r26358+nobinonly-0ubuntu1~umd1~hardy_all.deb) ...
Errors were encountered while processing:
 /var/cache/apt/archives/firefox-3.5-branding_3.5.4~hg20090914r26358+nobinonly-0ubuntu1~umd1~hardy_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by nanotube on 2009-09-16
well, first, get rid of duplicate entries in sources.list (the first warning there)

second, you seem to have enabled the daily PPA, so you're trying to install alpha versions, and there appears to be a problem with ff3.5 package from there...

instead of the daily ppa, try the security PPA instead, which only tracks releases:
[https://edge.launchpad.net/~ubuntu-mozilla-security/+archive/ppa](https://edge.launchpad.net/~ubuntu-mozilla-security/+archive/ppa)

and if you want to use ubuntuzilla, take out those mozilla PPAs completely, you don't need them.

---

### Post by MelDJ on 2009-09-16
how do i disable the daily ppa?

---

### Post by nanotube on 2009-09-16
> **MelDJ said:**
> how do i disable the daily ppa?

the same way you enabled it, only in reverse. :)

you can either directly edit your /etc/apt/sources.list
or use the "repositories" option in synaptic to use the gui to edit your repositories.

---

### Post by MelDJ on 2009-09-17
done. now there is the brokencount error. there are broken dependencies too: firefox and firefox-3.5

---

### Post by MelDJ on 2009-09-17
now i cant update or uninstall programs as this comes:

mel@mel-laptop:~$ sudo apt-get remove exaile
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  firefox: Depends: firefox-3.5-branding but it is not installable
  firefox-3.5: Depends: firefox-3.5-branding but it is not installable or
                        abrowser-3.5-branding but it is not installable
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

Argh! Really need help here!

---

### Post by MelDJ on 2009-09-17
er..bump

---

### Post by nanotube on 2009-09-17
try running "sudo apt-get --reinstall install firefox" which should pull in a fresh copy of firefox package from the official repositories (now that you have disabled the daily ppa)

---

### Post by MelDJ on 2009-09-17
running update manager got this: 
W: Failed to fetch [http://ftp.hostrino.com/pub/ubuntu/archive/pool/main/l/linux/linux-image-2.6.24-24-generic_2.6.24-24.60_i386.deb](http://ftp.hostrino.com/pub/ubuntu/archive/pool/main/l/linux/linux-image-2.6.24-24-generic_2.6.24-24.60_i386.deb)
  404 Not Found


W: Failed to fetch [http://ftp.hostrino.com/pub/ubuntu/archive/pool/multiverse/s/sun-java6/sun-java6-jdk_6-16-0ubuntu1.8.04_i386.deb](http://ftp.hostrino.com/pub/ubuntu/archive/pool/multiverse/s/sun-java6/sun-java6-jdk_6-16-0ubuntu1.8.04_i386.deb)
  404 Not Found


W: Failed to fetch [http://ftp.hostrino.com/pub/ubuntu/archive/pool/multiverse/s/sun-java6/sun-java6-bin_6-16-0ubuntu1.8.04_i386.deb](http://ftp.hostrino.com/pub/ubuntu/archive/pool/multiverse/s/sun-java6/sun-java6-bin_6-16-0ubuntu1.8.04_i386.deb)
  404 Not Found


W: Failed to fetch [http://ftp.hostrino.com/pub/ubuntu/archive/pool/multiverse/s/sun-java6/sun-java6-jre_6-16-0ubuntu1.8.04_all.deb](http://ftp.hostrino.com/pub/ubuntu/archive/pool/multiverse/s/sun-java6/sun-java6-jre_6-16-0ubuntu1.8.04_all.deb)
  404 Not Found


W: Failed to fetch [http://ftp.hostrino.com/pub/ubuntu/archive/pool/main/t/tzdata/tzdata_2009m-0ubuntu0.8.04_all.deb](http://ftp.hostrino.com/pub/ubuntu/archive/pool/main/t/tzdata/tzdata_2009m-0ubuntu0.8.04_all.deb)
  404 Not Found


W: Failed to fetch [http://ftp.hostrino.com/pub/ubuntu/archive/pool/main/o/openssl/libssl0.9.8_0.9.8g-4ubuntu3.8_i386.deb](http://ftp.hostrino.com/pub/ubuntu/archive/pool/main/o/openssl/libssl0.9.8_0.9.8g-4ubuntu3.8_i386.deb)
  404 Not Found


W: Failed to fetch [http://ftp.hostrino.com/pub/ubuntu/archive/pool/main/m/mono/mono-runtime_1.2.6+dfsg-6ubuntu3.1_i386.deb](http://ftp.hostrino.com/pub/ubuntu/archive/pool/main/m/mono/mono-runtime_1.2.6+dfsg-6ubuntu3.1_i386.deb)
  404 Not Found


W: Failed to fetch [http://ftp.hostrino.com/pub/ubuntu/archive/pool/main/m/mono/mono-gac_1.2.6+dfsg-6ubuntu3.1_all.deb](http://ftp.hostrino.com/pub/ubuntu/archive/pool/main/m/mono/mono-gac_1.2.6+dfsg-6ubuntu3.1_all.deb)
  404 Not Found


W: Failed to fetch [http://ftp.hostrino.com/pub/ubuntu/archive/pool/main/m/mono/mono-jit_1.2.6+dfsg-6ubuntu3.1_i386.deb](http://ftp.hostrino.com/pub/ubuntu/archive/pool/main/m/mono/mono-jit_1.2.6+dfsg-6ubuntu3.1_i386.deb)
  404 Not Found


W: Failed to fetch [http://ftp.hostrino.com/pub/ubuntu/archive/pool/main/m/mono/mono-common_1.2.6+dfsg-6ubuntu3.1_i386.deb](http://ftp.hostrino.com/pub/ubuntu/archive/pool/main/m/mono/mono-common_1.2.6+dfsg-6ubuntu3.1_i386.deb)
  404 Not Found


W: Failed to fetch [http://ftp.hostrino.com/pub/ubuntu/archive/pool/main/m/mono/libmono-corlib1.0-cil_1.2.6+dfsg-6ubuntu3.1_all.deb](http://ftp.hostrino.com/pub/ubuntu/archive/pool/main/m/mono/libmono-corlib1.0-cil_1.2.6+dfsg-6ubuntu3.1_all.deb)
  404 Not Found


W: Failed to fetch [http://ftp.hostrino.com/pub/ubuntu/archive/pool/main/m/mono/libmono-cairo1.0-cil_1.2.6+dfsg-6ubuntu3.1_all.deb](http://ftp.hostrino.com/pub/ubuntu/archive/pool/main/m/mono/libmono-cairo1.0-cil_1.2.6+dfsg-6ubuntu3.1_all.deb)
  404 Not Found


W: Failed to fetch [http://ftp.hostrino.com/pub/ubuntu/archive/pool/main/m/mono/libmono-corlib2.0-cil_1.2.6+dfsg-6ubuntu3.1_all.deb](http://ftp.hostrino.com/pub/ubuntu/archive/pool/main/m/mono/libmono-corlib2.0-cil_1.2.6+dfsg-6ubuntu3.1_all.deb)
  404 Not Found


W: Failed to fetch [http://ftp.hostrino.com/pub/ubuntu/archive/pool/main/m/mono/libmono-cairo2.0-cil_1.2.6+dfsg-6ubuntu3.1_all.deb](http://ftp.hostrino.com/pub/ubuntu/archive/pool/main/m/mono/libmono-cairo2.0-cil_1.2.6+dfsg-6ubuntu3.1_all.deb)
  404 Not Found


W: Failed to fetch [http://ftp.hostrino.com/pub/ubuntu/archive/pool/main/m/mono/libmono-system1.0-cil_1.2.6+dfsg-6ubuntu3.1_all.deb](http://ftp.hostrino.com/pub/ubuntu/archive/pool/main/m/mono/libmono-system1.0-cil_1.2.6+dfsg-6ubuntu3.1_all.deb)
  404 Not Found


W: Failed to fetch [http://ftp.hostrino.com/pub/ubuntu/archive/pool/main/m/mono/libmono-security1.0-cil_1.2.6+dfsg-6ubuntu3.1_all.deb](http://ftp.hostrino.com/pub/ubuntu/archive/pool/main/m/mono/libmono-security1.0-cil_1.2.6+dfsg-6ubuntu3.1_all.deb)
  404 Not Found


W: Failed to fetch [http://ftp.hostrino.com/pub/ubuntu/archive/pool/main/m/mono/libmono-data-tds1.0-cil_1.2.6+dfsg-6ubuntu3.1_all.deb](http://ftp.hostrino.com/pub/ubuntu/archive/pool/main/m/mono/libmono-data-tds1.0-cil_1.2.6+dfsg-6ubuntu3.1_all.deb)
  404 Not Found


W: Failed to fetch [http://ftp.hostrino.com/pub/ubuntu/archive/pool/main/m/mono/libmono0_1.2.6+dfsg-6ubuntu3.1_i386.deb](http://ftp.hostrino.com/pub/ubuntu/archive/pool/main/m/mono/libmono0_1.2.6+dfsg-6ubuntu3.1_i386.deb)
  404 Not Found


W: Failed to fetch [http://ftp.hostrino.com/pub/ubuntu/archive/pool/main/m/mono/libmono-system2.0-cil_1.2.6+dfsg-6ubuntu3.1_all.deb](http://ftp.hostrino.com/pub/ubuntu/archive/pool/main/m/mono/libmono-system2.0-cil_1.2.6+dfsg-6ubuntu3.1_all.deb)
  404 Not Found


W: Failed to fetch [http://ftp.hostrino.com/pub/ubuntu/archive/pool/main/m/mono/libmono-security2.0-cil_1.2.6+dfsg-6ubuntu3.1_all.deb](http://ftp.hostrino.com/pub/ubuntu/archive/pool/main/m/mono/libmono-security2.0-cil_1.2.6+dfsg-6ubuntu3.1_all.deb)
  404 Not Found


W: Failed to fetch [http://ftp.hostrino.com/pub/ubuntu/archive/pool/main/m/mono/libmono-data-tds2.0-cil_1.2.6+dfsg-6ubuntu3.1_all.deb](http://ftp.hostrino.com/pub/ubuntu/archive/pool/main/m/mono/libmono-data-tds2.0-cil_1.2.6+dfsg-6ubuntu3.1_all.deb)
  404 Not Found


W: Failed to fetch [http://ftp.hostrino.com/pub/ubuntu/archive/pool/main/m/mono/libmono-sharpzip0.84-cil_1.2.6+dfsg-6ubuntu3.1_all.deb](http://ftp.hostrino.com/pub/ubuntu/archive/pool/main/m/mono/libmono-sharpzip0.84-cil_1.2.6+dfsg-6ubuntu3.1_all.deb)
  404 Not Found


W: Failed to fetch [http://ftp.hostrino.com/pub/ubuntu/archive/pool/main/m/mono/libmono-sharpzip2.84-cil_1.2.6+dfsg-6ubuntu3.1_all.deb](http://ftp.hostrino.com/pub/ubuntu/archive/pool/main/m/mono/libmono-sharpzip2.84-cil_1.2.6+dfsg-6ubuntu3.1_all.deb)
  404 Not Found


W: Failed to fetch [http://ftp.hostrino.com/pub/ubuntu/archive/pool/main/m/mono/libmono-system-data2.0-cil_1.2.6+dfsg-6ubuntu3.1_all.deb](http://ftp.hostrino.com/pub/ubuntu/archive/pool/main/m/mono/libmono-system-data2.0-cil_1.2.6+dfsg-6ubuntu3.1_all.deb)
  404 Not Found


W: Failed to fetch [http://ftp.hostrino.com/pub/ubuntu/archive/pool/main/m/mono/libmono-sqlite2.0-cil_1.2.6+dfsg-6ubuntu3.1_all.deb](http://ftp.hostrino.com/pub/ubuntu/archive/pool/main/m/mono/libmono-sqlite2.0-cil_1.2.6+dfsg-6ubuntu3.1_all.deb)
  404 Not Found


W: Failed to fetch [http://ftp.hostrino.com/pub/ubuntu/archive/pool/main/m/mono/libmono-system-data1.0-cil_1.2.6+dfsg-6ubuntu3.1_all.deb](http://ftp.hostrino.com/pub/ubuntu/archive/pool/main/m/mono/libmono-system-data1.0-cil_1.2.6+dfsg-6ubuntu3.1_all.deb)
  404 Not Found


W: Failed to fetch [http://ftp.hostrino.com/pub/ubuntu/archive/pool/main/m/mono/libmono-system-web1.0-cil_1.2.6+dfsg-6ubuntu3.1_all.deb](http://ftp.hostrino.com/pub/ubuntu/archive/pool/main/m/mono/libmono-system-web1.0-cil_1.2.6+dfsg-6ubuntu3.1_all.deb)
  404 Not Found


W: Failed to fetch [http://ftp.hostrino.com/pub/ubuntu/archive/pool/main/m/mono/libmono-system-web2.0-cil_1.2.6+dfsg-6ubuntu3.1_all.deb](http://ftp.hostrino.com/pub/ubuntu/archive/pool/main/m/mono/libmono-system-web2.0-cil_1.2.6+dfsg-6ubuntu3.1_all.deb)
  404 Not Found


W: Failed to fetch [http://ftp.hostrino.com/pub/ubuntu/archive/pool/main/m/mono/libmono1.0-cil_1.2.6+dfsg-6ubuntu3.1_all.deb](http://ftp.hostrino.com/pub/ubuntu/archive/pool/main/m/mono/libmono1.0-cil_1.2.6+dfsg-6ubuntu3.1_all.deb)
  404 Not Found


W: Failed to fetch [http://ftp.hostrino.com/pub/ubuntu/archive/pool/main/m/mono/libmono2.0-cil_1.2.6+dfsg-6ubuntu3.1_all.deb](http://ftp.hostrino.com/pub/ubuntu/archive/pool/main/m/mono/libmono2.0-cil_1.2.6+dfsg-6ubuntu3.1_all.deb)
  404 Not Found


W: Failed to fetch [http://ftp.hostrino.com/pub/ubuntu/archive/pool/main/n/nss/libnss3-1d_3.12.3.1-0ubuntu0.8.04.2_i386.deb](http://ftp.hostrino.com/pub/ubuntu/archive/pool/main/n/nss/libnss3-1d_3.12.3.1-0ubuntu0.8.04.2_i386.deb)
  404 Not Found


W: Failed to fetch [http://ftp.hostrino.com/pub/ubuntu/archive/pool/main/o/openexr/libopenexr2ldbl_1.2.2-4.4ubuntu1.1_i386.deb](http://ftp.hostrino.com/pub/ubuntu/archive/pool/main/o/openexr/libopenexr2ldbl_1.2.2-4.4ubuntu1.1_i386.deb)
  404 Not Found


W: Failed to fetch [http://ftp.hostrino.com/pub/ubuntu/archive/pool/main/q/qt4-x11/libqt4-gui_4.3.4-0ubuntu3.1_i386.deb](http://ftp.hostrino.com/pub/ubuntu/archive/pool/main/q/qt4-x11/libqt4-gui_4.3.4-0ubuntu3.1_i386.deb)
  404 Not Found


W: Failed to fetch [http://ftp.hostrino.com/pub/ubuntu/archive/pool/main/q/qt4-x11/libqt4-core_4.3.4-0ubuntu3.1_i386.deb](http://ftp.hostrino.com/pub/ubuntu/archive/pool/main/q/qt4-x11/libqt4-core_4.3.4-0ubuntu3.1_i386.deb)
  404 Not Found


W: Failed to fetch [http://ftp.hostrino.com/pub/ubuntu/archive/pool/main/l/linux/linux-headers-2.6.24-24_2.6.24-24.60_all.deb](http://ftp.hostrino.com/pub/ubuntu/archive/pool/main/l/linux/linux-headers-2.6.24-24_2.6.24-24.60_all.deb)
  404 Not Found


W: Failed to fetch [http://ftp.hostrino.com/pub/ubuntu/archive/pool/main/l/linux/linux-headers-2.6.24-24-generic_2.6.24-24.60_i386.deb](http://ftp.hostrino.com/pub/ubuntu/archive/pool/main/l/linux/linux-headers-2.6.24-24-generic_2.6.24-24.60_i386.deb)
  404 Not Found


W: Failed to fetch [http://ftp.hostrino.com/pub/ubuntu/archive/pool/main/l/linux/linux-libc-dev_2.6.24-24.60_i386.deb](http://ftp.hostrino.com/pub/ubuntu/archive/pool/main/l/linux/linux-libc-dev_2.6.24-24.60_i386.deb)
  404 Not Found


W: Failed to fetch [http://ftp.hostrino.com/pub/ubuntu/archive/pool/main/o/openssl/openssl_0.9.8g-4ubuntu3.8_i386.deb](http://ftp.hostrino.com/pub/ubuntu/archive/pool/main/o/openssl/openssl_0.9.8g-4ubuntu3.8_i386.deb)
  404 Not Found


other than that, everything is alright. i can install things. no more irritating firefox branding or broken dependencies. thanks nanotube, you really made my day:)

---

### Post by nanotube on 2009-09-18
glad your problems are gone :)

as to the hostrino thing.. don't know what that is... doesn't look like an official ubuntu repository. you can comment that one out of your sources.list as well, if you don't want to keep seeing those warnings.

---

### Post by MelDJ on 2009-09-18
i changed the server i get my update. all is well now:)

---

