---
title: "No Wired Connection"
date: 2014-09-24
forum: Networking &amp; Wireless
---

### Post by honwaiwong on 2014-09-24
I have just installed [COLOR=#000000] on my Dell Inspirion 9400 Lap Top through USB stick. The version is 14.04 LTS

[/COLOR][COLOR=#000000]I think the wired connection was detected during installation, but once installation is done, there is neither wired connection nor wireless.[/COLOR]

[COLOR=#000000]Below are the responses to the two commands that I may be asked to perform. I would appreciate very much if someone can guide me through trouble shooting it.

[/COLOR]:~$ uname -r
3.13.0-32-generic
:~$ ifconfig
lo        Linkencap:Local Loopback  
          inetaddr:127.0.0.1  Mask:255.0.0.0
          inet6 addr:::1/128 Scope:Host
          UP LOOPBACKRUNNING  MTU:65536  Metric:1
          RX packets:135errors:0 dropped:0 overruns:0 frame:0
          TXpackets:135 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0txqueuelen:0
          RXbytes:10495 (10.4 KB)  TX bytes:10495(10.4 KB)

---

### Post by h.hittini on 2014-09-24
Please post the output of this command
```
sudo lshw -C network
```

---

### Post by honwaiwong on 2014-09-24
This is what I see:```

:~$ sudo lshw -C network
PCI (sysfs)  
  *-network               
       description:Network controller
       product: BCM4311802.11b/g WLAN
       vendor: BroadcomCorporation
       physical id: 0
       bus info:pci@0000:0c:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pmmsi pciexpress bus_master cap_list
       configuration:driver=wl latency=0
       resources:irq:17 memory:efdfc000-efdfffff
  *-network UNCLAIMED
       description:Ethernet controller
       product:BCM4401-B0 100Base-TX
       vendor: BroadcomCorporation
       physical id: 0
       bus info:pci@0000:03:00.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pmbus_master cap_list
       configuration:latency=64
       resources:memory:ef9fe000-ef9fffff
```

---

### Post by honwaiwong on 2014-09-24
I notice "pci"'s "p" has a smiley instead. Post again as below.

:~$ sudo lshw -C network
PCI (sysfs)  
  *-network               
       description:Network controller
       product: BCM4311802.11b/g WLAN
       vendor: BroadcomCorporation
       physical id: 0
       bus info:   pci@0000:0c:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pmmsi pciexpress bus_master cap_list
       configuration:driver=wl latency=0
       resources:irq:17 memory:efdfc000-efdfffff
  *-network UNCLAIMED
       description:Ethernet controller
       product:BCM4401-B0 100Base-TX
       vendor: BroadcomCorporation
       physical id: 0
       bus info:   pci@0000:03:00.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pmbus_master cap_list
       configuration:latency=64
       resources:memory:ef9fe000-ef9fffff

---

### Post by h.hittini on 2014-09-24
The driver for your network adapter is not installed after the update
Your should look for [COLOR=#ff0000]BCM4401-B0[/COLOR] driver
I assume you have a 32bit system, You can get the driver from here [http://www.broadcom.com/support/license.php?file=440x/linux-1.00g.zip](http://www.broadcom.com/support/license.php?file=440x/linux-1.00g.zip)
Follow the instructions in "Building Driver From TAR File" section to compile it

> **honwaiwong said:**
> This is what I see:
:~$ sudo lshw -C network
PCI (sysfs)  
  *-network               
       description:Network controller
       product: BCM4311802.11b/g WLAN
       vendor: BroadcomCorporation
       physical id: 0
       bus info:pci@0000:0c:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pmmsi pciexpress bus_master cap_list
       configuration:driver=wl latency=0
       resources:irq:17 memory:efdfc000-efdfffff
  *-[COLOR=#ff0000]network UNCLAIMED[/COLOR]
       description:Ethernet controller
       product:[COLOR=#ff0000]BCM4401-B0[/COLOR] 100Base-TX
       vendor: BroadcomCorporation
       physical id: 0
       bus info:pci@0000:03:00.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pmbus_master cap_list
       configuration:latency=64
       resources:memory:ef9fe000-ef9fffff

---

### Post by honwaiwong on 2014-09-24
I get the zip file, extract it to a subdirectory in my home directory. At the level where I see b44-1.100g.taz.gz, I tar it successfully and see the directory b44-1.00g created, and under it are Makefile, b44.c b44.h

However I have difficulty following the second step. The second step is cd src and then make. I do not see src. The best I can guess is b44-1.00g, I cd there and do make, and it returns:

b44.c:10:26: fatal error: linux/config.h: No such file or directory
#include <linux/config.h>

Have I missed anything?

---

### Post by h.hittini on 2014-09-25
I believe what's meant by src is the folder extracted from the tar.gz file, because that's what you are supposed to "make"
You also should have installed "build-essential" package and your kernel headers before attempting to "make"
You may need additional libraries but let's start with this
```
sudo apt-get install build-essential linux-headers-`uname -r`
```
and when you want to "make install" you should
```
sudo make install
```
> **honwaiwong said:**
> I get the zip file, extract it to a subdirectory in my home directory. At the level where I see b44-1.100g.taz.gz, I tar it successfully and see the directory b44-1.00g created, and under it are Makefile, b44.c b44.h

However I have difficulty following the second step. The second step is cd src and then make. I do not see src. The best I can guess is b44-1.00g, I cd there and do make, and it returns:

b44.c:10:26: fatal error: linux/config.h: No such file or directory
#include <linux/config.h>

Have I missed anything?

---

### Post by ben222qmz7 on 2014-09-25
Sorry about coming to same thread, but I have the same problem wired connection not working
and therefore I hope to get help in my problem.
My laptop is HP6735s with Xubuntu 12.04 and WinXP as a dualboot
system. The wired connection does not work in Windows either.

My command gives the following:
```
~$ sudo lshw -C network

  *-network               
       description: Wireless interface
       product: BCM4322 802.11a/b/g/n Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth1
       version: 01
       serial: 00:21:00:3a:82:d3
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=6.20.155.1 (r326264) ip=192.168.0.13 latency=0 multicast=yes wireless=IEEE 802.11abg
       resources: irq:17 memory:d1000000-d1003fff

```

---

### Post by h.hittini on 2014-09-25
In order not to get things missed up here, I strongly recommend posting your issue in a new thread
You are running a different version of Ubuntu and have a different chipset

> **ben222qmz7 said:**
> Sorry about coming to same thread, but I have the same problem wired connection not working
and therefore I hope to get help in my problem.
My laptop is HP6735s with [COLOR=#ff0000]Xubuntu 12.04[/COLOR] and WinXP as a dualboot
system. The wired connection does not work in Windows either.

My command gives the following:
```
~$ sudo lshw -C network

  *-network               
       description: Wireless interface
       product: [COLOR=#ff0000]BCM4322[/COLOR] 802.11a/b/g/n Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth1
       version: 01
       serial: 00:21:00:3a:82:d3
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=6.20.155.1 (r326264) ip=192.168.0.13 latency=0 multicast=yes wireless=IEEE 802.11abg
       resources: irq:17 memory:d1000000-d1003fff

```

---

### Post by honwaiwong on 2014-09-25
I get this error 

$ sudo apt-get install build-essential linux-headers-`uname -r`
 


Reading package lists... Done
Building dependency tree      
Reading state information... Done
linux-headers-3.13.0-32-generic is already the newest version.
linux-headers-3.13.0-32-generic set to manually installed.
The following extra packages will be installed:
  dpkg-dev g++ g++-4.8 libalgorithm-diff-perl libalgorithm-diff-xs-perl
  libalgorithm-merge-perl libstdc++-4.8-dev
Suggested packages:
  debian-keyring g++-multilib g++-4.8-multilib gcc-4.8-doc libstdc++6-4.8-dbg
  libstdc++-4.8-doc
The following NEW packages will be installed:
  build-essential dpkg-dev g++ g++-4.8 libalgorithm-diff-perl
  libalgorithm-diff-xs-perl libalgorithm-merge-perl libstdc++-4.8-dev
0 upgraded, 8 newly installed, 0 to remove and 148 not upgraded.
Need to get 8,889 kB of archives.
After this operation, 30.3 MB of additional disk space will be used.
Do you want to continue? [Y/n] Y
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty/main libstdc++-4.8-dev i386 4.8.2-19ubuntu1
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty/main g++-4.8 i386 4.8.2-19ubuntu1
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty/main g++ i386 4:4.8.2-1ubuntu6
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-updates/main dpkg-dev all 1.17.5ubuntu5.3
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty/main build-essential i386 11.6ubuntu6
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty/main libalgorithm-diff-perl all 1.19.02-3
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty/main libalgorithm-diff-xs-perl i386 0.04-2build4
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty/main libalgorithm-merge-perl all 0.08-2
  Could not resolve 'us.archive.ubuntu.com'
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) trusty-security/main dpkg-dev all 1.17.5ubuntu5.3
  Could not resolve 'security.ubuntu.com'
E: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/gcc-4.8/libstdc++-4.8-dev_4.8.2-19ubuntu1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/gcc-4.8/libstdc++-4.8-dev_4.8.2-19ubuntu1_i386.deb)  Could not resolve 'us.archive.ubuntu.com'
 
E: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/gcc-4.8/g++-4.8_4.8.2-19ubuntu1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/gcc-4.8/g++-4.8_4.8.2-19ubuntu1_i386.deb)  Could not resolve 'us.archive.ubuntu.com'
 
E: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/gcc-defaults/g++_4.8.2-1ubuntu6_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/gcc-defaults/g++_4.8.2-1ubuntu6_i386.deb)  Could not resolve 'us.archive.ubuntu.com'
 
E: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/d/dpkg/dpkg-dev_1.17.5ubuntu5.3_all.deb](http://security.ubuntu.com/ubuntu/pool/main/d/dpkg/dpkg-dev_1.17.5ubuntu5.3_all.deb)  Could not resolve 'security.ubuntu.com'
 
E: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/b/build-essential/build-essential_11.6ubuntu6_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/b/build-essential/build-essential_11.6ubuntu6_i386.deb)  Could not resolve 'us.archive.ubuntu.com'
 
E: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/liba/libalgorithm-diff-perl/libalgorithm-diff-perl_1.19.02-3_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/liba/libalgorithm-diff-perl/libalgorithm-diff-perl_1.19.02-3_all.deb)  Could not resolve 'us.archive.ubuntu.com'
 
E: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/liba/libalgorithm-diff-xs-perl/libalgorithm-diff-xs-perl_0.04-2build4_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/liba/libalgorithm-diff-xs-perl/libalgorithm-diff-xs-perl_0.04-2build4_i386.deb)  Could not resolve 'us.archive.ubuntu.com'
 
E: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/liba/libalgorithm-merge-perl/libalgorithm-merge-perl_0.08-2_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/liba/libalgorithm-merge-perl/libalgorithm-merge-perl_0.08-2_all.deb)  Could not resolve 'us.archive.ubuntu.com'
 
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

---

### Post by h.hittini on 2014-09-26
```
sudo apt-get update
```
Will update the links your OS downloads packages from, it will also get links for new packages and links for updated versions of the packages you already have
```
sudo apt-get upgrade
```
Will update any package you have, if a newer version was released and published in the repository

You should run these two commands regularly and before you try to install anything new

---

### Post by honwaiwong on 2014-09-27
Both commands return similar messages, as below.

If I am not mistaken, there seems to be a chicken and egg problem, the command seems to want to go to the internet and down load something but I have no internet access via ubuntu.
===
$ sudo apt-get update
Err [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security InRelease
  
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty InRelease
  
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty InRelease
  
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates InRelease
  
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports InRelease
  
Err [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security Release.gpg
  Could not resolve'security.ubuntu.com'
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty Release.gpg
  Could not resolve'extras.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty Release.gpg
  Could not resolve'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates Release.gpg
  Could not resolve'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports Release.gpg
  Could not resolve'us.archive.ubuntu.com'
Reading package lists... Done
W: Failed to fetchhttp://us.archive.ubuntu.com/ubuntu/dists/trusty/InRelease  
 
W: Failed to fetchhttp://us.archive.ubuntu.com/ubuntu/dists/trusty-updates/InRelease  
 
W: Failed to fetchhttp://us.archive.ubuntu.com/ubuntu/dists/trusty-backports/InRelease  
 
W: Failed to fetchhttp://security.ubuntu.com/ubuntu/dists/trusty-security/InRelease  
 
W: Failed to fetchhttp://extras.ubuntu.com/ubuntu/dists/trusty/InRelease  
 
W: Failed to fetchhttp://security.ubuntu.com/ubuntu/dists/trusty-security/Release.gpg  Could not resolve 'security.ubuntu.com'
 
W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/trusty/Release.gpg](http://extras.ubuntu.com/ubuntu/dists/trusty/Release.gpg)  Could not resolve 'extras.ubuntu.com'
 
W: Failed to fetchhttp://us.archive.ubuntu.com/ubuntu/dists/trusty/Release.gpg  Could not resolve 'us.archive.ubuntu.com'
 
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/trusty-updates/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/trusty-updates/Release.gpg)  Could not resolve 'us.archive.ubuntu.com'
 
W: Failed to fetchhttp://us.archive.ubuntu.com/ubuntu/dists/trusty-backports/Release.gpg  Could not resolve 'us.archive.ubuntu.com'
 
W: Some index files failed to download. They have beenignored, or old ones used instead.
===================================
$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree      
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  linux-genericlinux-headers-generic linux-image-generic
The following packages will be upgraded:
  accountsserviceapport apport-gtk apt apt-transport-https apt-utils
  aptdaemonaptdaemon-data bash cups cups-bsd cups-client cups-common
  cups-core-driverscups-daemon cups-ppdc cups-server-common dbus dbus-x11
  evolution-data-serverevolution-data-server-common
 evolution-data-server-online-accounts firefox fonts-opensymbolgcc-4.9-base
  gir1.2-ebook-1.2gir1.2-ebookcontacts-1.2 gir1.2-edataserver-1.2
  gir1.2-freedesktopgir1.2-glib-2.0 gir1.2-gtk-3.0 gir1.2-gudev-1.0
 gir1.2-javascriptcoregtk-3.0 gir1.2-webkit-3.0 irqbalance krb5-locales
  libaccountsservice0libapt-inst1.5 libapt-pkg4.12 libc-bin libc-dev-bin
  libc6 libc6-dbglibc6-dev libcamel-1.2-45 libcups2 libcupscgi1 libcupsimage2
  libcupsmime1libcupsppdc1 libcurl3 libcurl3-gnutls libdbus-1-3
  libebackend-1.2-7libebook-1.2-14 libebook-contacts-1.2-0 libecal-1.2-16
  libedata-book-1.2-20libedata-cal-1.2-23 libedataserver-1.2-18 libgail-3-0
  libgcc1 libgcrypt11libgirepository-1.0-1 libgpgme11 libgssapi-krb5-2
  libgtk-3-0libgtk-3-bin libgtk-3-common libgudev-1.0-0 libharfbuzz-icu0
  libharfbuzz0blibjavascriptcoregtk-3.0-0 libk5crypto3 libkrb5-3
  libkrb5support0liblzo2-2 libnm-gtk-common libnm-gtk0 libnss3 libnss3-1d
  libnss3-nssdbliboxideqt-qmlplugin libpam-systemd
 libreoffice-avmedia-backend-gstreamer libreoffice-ogltrans
  libreoffice-pdfimportlibreoffice-presentation-minimizer
 libreoffice-style-human libsmbclient libssl1.0.0 libsystemd-daemon0
  libsystemd-journal0libsystemd-login0 libudev1 libunity-core-6.0-9
  libunity-gtk2-parser0libunity-gtk3-parser0 libwbclient0 libwebkitgtk-3.0-0
 libwebkitgtk-3.0-common linux-firmware linux-libc-dev multiarch-support
  net-toolsnetwork-manager-gnome openssl python-aptdaemon
 python-aptdaemon.gtk3widgets python-gi python-gi-cairo python-gobject
  python-sambapython3-apport python3-aptdaemon python3-aptdaemon.gtk3widgets
 python3-aptdaemon.pkcompat python3-distupgrade python3-gipython3-gi-cairo
 python3-problem-report rsyslog samba-common samba-common-bin samba-libs
  shotwellshotwell-common smbclient systemd-services ubuntu-drivers-common
 ubuntu-release-upgrader-core ubuntu-release-upgrader-gtk udev unity
 unity-gtk-module-common unity-gtk2-module unity-gtk3-moduleunity-services
  uno-libs3 ureusb-creator-common usb-creator-gtk xserver-common
  xserver-xorg-corexserver-xorg-video-intel
145 upgraded, 0 newly installed, 0 to remove and 3 notupgraded.
Need to get 548 kB/105 MB of archives.
After this operation, 2,437 kB of additional disk space willbe used.
Do you want to continue? [Y/n] Y
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) trusty-security/mainbash i386 4.3-7ubuntu1.3
  Could not resolve'security.ubuntu.com'
E: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/b/bash/bash_4.3-7ubuntu1.3_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/b/bash/bash_4.3-7ubuntu1.3_i386.deb)  Could not resolve 'security.ubuntu.com'
 
E: Unable to fetch some archives, maybe run apt-get update ortry with --fix-missing?
hon-wai@honwai-MP061:~$

---

### Post by h.hittini on 2014-09-27
You have a problem with apt-get
Google "failed to fetch apt-get 14.04", and try the proposed solutions
This may work for you [http://askubuntu.com/questions/483565/error-occured-when-apt-get-update-run](http://askubuntu.com/questions/483565/error-occured-when-apt-get-update-run)

---

### Post by varunendra on 2014-09-28
Oh my! We need to hold our horses guys, wrong direction, wrong approach!

The trouble is this - You have, most probably because you chose to "Install Updates" and/or "Install Third Party Software" during installation, installed the proprietary "**wl**" driver for your wireless. This is *supposed* to work with the card that you have, but evidently (a one-million'th time) it doesn't.

Now, in order to rule without resistence or opposition, this "wl" driver suppresses the native "b43" and some supporting drivers. Now one of the supporting drivers - "**ssb**" is also **_required_** by the driver (b44) that supports your Ethernet card.

Since the "wl" driver also blacklists this "ssb" driver, your Ethernet card is no more usable, because 'ssb' is not loading anymore.

Fortunately for you, the solution is really-really easy - just 'purge' (means - completely remove, along with configuration files) the "wl" driver with this command -
```
sudo apt-get purge bcmwl-kernel-source
```
Then reload the driver that drives the Ethernet card -
```
sudo modprobe -rv b44
sudo modprobe -v b44
```
At this point, your Ethernet card should start working. If not, simply reboot.

Once we get the Ethernet working, install the firmware that is required by the 'Correct' driver for your wireless card -
```
sudo apt-get install firmware-b43-installer
```

Please try, and come back with the cake and drinks for the celebration.

**PS:**
Terminal commands & outputs should always be posted within '**Code**' tags to preserve their formatting and make the post compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Use Code Tags" link in my signature.

---

### Post by honwaiwong on 2014-09-28
Many thanks. It works! I was rather depressed for a few days and now all problems gone.

However, I do have a few questions, as the process does not work as smoothly as you describe and I want to be sure there is no lurking problem I should worry.

1) After 
sudo apt-get install firmware-b43-installer
I still do not get wireless. I go to Software and Update=>Additional Drivers, and check on  "using Broadcom 802.11 Linux STA.." and this does not help
2) I feel maybe I should do apt-get update AND apt-get upgrade. To my surprise, I then lose my even ethernet connection!
3) So I re-do your steps. Reboot, miraculously, BOTH ethernet and wirelss is up!
4) to play safe again, I do sudo-get update and upgrade, this time, both ethernet and wireless are intact!

Do you have any idea what may be happening. Do you expect I have to re-do your steps every time there I do a serious update?

Thanks again, it really helps!

---

### Post by varunendra on 2014-09-29
> **honwaiwong said:**
> However, I do have a few questions, as the process does not work as smoothly as you describe and I want to be sure there is no lurking problem I should worry.
I was thinking of adding this to my first post, but it was already much longer than it needed to be. Didn't want to make it confusing by adding too many explanations at once. :D

Yes there is a problem, but you don't need to worry once you know that _one thing_ that you should _NOT_ do - **DON't install the driver that the "Additional Drivers" program offers!** It is the same "**wl**" driver that caused all this trouble.

The native driver did not work initially because, I think, you tried to connect to it immediately (without rebooting) after installing the "firmware-b43-installer" package. This package only installs the missing firmware, the driver already exists in the kernel and is loaded. But just like we reloaded the ethernet driver, the wifi driver (b43) also needs to be reloaded in order to load _with the firmware_ after it is installed. This can be done using either the "modprobe.." commands with "b43" driver, or a simple reboot.

So the bottomline - DON't accept the driver from "Additional Drivers" program, and Don't install "bcmwl-kernel-source" package any other way - both these lead to the same "wl" driver which won't work with your card, and will also disable the Ethernet.

Now that you have the required firmware installed, you don't need to worry about anything else. Just keep the above "don't install these" part in mind, the firmware or the driver won't break across updates/upgrades.

You can safely and confidently mark the thread as **[SOLVED]** now, using "Thread Tools" link above the top post. :p

**PS:**
And Just because you should know - On a clean installation of Ubuntu, if you ever need to do it again, Don't opt to install "Updates" or "Third Party Software" _during installation_. You can do these later (later updates don't install the "wl" driver unless you explicitly choose to). After installation of the OS is finished, simply run the "apt-get install firmware-b43-installer" command with the working wired connection to get the missing firmware for the correct driver. Of course this is valid only for some broadcom cards, including yours.

---

