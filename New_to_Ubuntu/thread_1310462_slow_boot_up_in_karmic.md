---
title: "slow boot up in karmic"
date: 2009-11-01
forum: New to Ubuntu
---

### Post by samsamros on 2009-11-01
I just upgraded from 9.04 everything works beautifully, smooth. when i turn it off it goes even quicker than before the interface runs faster than 9.04 everything is good except the boot up which i feel there is an extra 20 seconds in the process compared to jaunty.. any solutions for this.. Thank you very much in advance

---

### Post by zkriesse on 2009-11-02
I've not had any problems with speed but I did a full install rather than an upgrade.

---

### Post by Xomm on 2009-11-02
If you simply upgraded, that would be the problem.

If you're looking for that increase in speed, I would do a full install.

---

### Post by LoloftheRings on 2009-11-11
I did a full install with beta 1, and boot time increased to 1:30. The 'beautiful boot' wasn't there either. I don't know if this is fixed by now, but it gave a REALLY bad experience.

---

### Post by unmole on 2009-11-11
Try this:
 ```
 gksu gedit /etc/init.d/rc 
```
Look for the line which reads CONCURRENCY=none and change none to shell. You should see a significant reduction in boot time.


P.S. You might see a black screen with ubuntu login after reboot. Just ignore it,wait for a while and the GUI shuld start up

---

### Post by gatos on 2009-11-11
> **unmole said:**
> Try this:
 ```
 gksu gedit /etc/init.d/rc 
```
Look for the line which reads CONCURRENCY=none and change none to shell. You should see a significant reduction in boot time.


P.S. You might see a black screen with ubuntu login after reboot. Just ignore it,wait for a while and the GUI shuld start up

Tried it but no difference.:-(

Booting was slow after upgrade, so I did a fresh install and the problem persists

---

### Post by yesint on 2009-11-20
Here is one possible solution:
[http://arstechnica.com/open-source/reviews/2009/11/good-karma-ars-reviews-ubuntu-910.ars/2](http://arstechnica.com/open-source/reviews/2009/11/good-karma-ars-reviews-ubuntu-910.ars/2)

"Users who do not have solid-state drives can potentially improve their startup performance by disabling sreadahead or replacing it with ureadahead, a new version that is optimized for both solid-state and conventional magnetic hard drives. Unfortunately, ureadahead was not ready in time to be included in the default Karmic installation. It will be rolled out soon as an update in Karmic, but users who want it now can install it from a Personal Package Archive (PPA). Remnant provides instructions on how to set up the PPA in a comment posted on Launchpad."

Basically go here:
[https://bugs.edge.launchpad.net/ubuntu/+source/ureadahead/+bug/432089/comments/20](https://bugs.edge.launchpad.net/ubuntu/+source/ureadahead/+bug/432089/comments/20)
and follow the instructions.

---

### Post by jsacks on 2009-11-21
updating the kernal doesnt work for me. I put in:

sudo add-apt-repository ppa:ubuntu-boot/ppa
  sudo apt-get update
  sudo apt-get dist-upgrade

I get the following from terminal:


I posted that into terminal and got the following. It seems its not finding the distribution upgrade??? I'm not sure what that means or how to work around that.

jared@dell-desktop:~$ sudo add-apt-repository ppa:ubuntu-boot/ppa
[sudo] password for jared:
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv 4537E18AF1840D5CA312AED257B0CE6D09827771
gpg: requesting key 09827771 from hkp server keyserver.ubuntu.com
gpg: key 09827771: public key "Launchpad ppa" imported
gpg: Total number processed: 1
gpg: imported: 1 (RSA: 1)
jared@dell-desktop:~$ sudo apt-get update
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release.gpg
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic Release.gpg
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Translation-en_US
Get:1 [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release.gpg [307B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/universe Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Sources
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release
Get:2 [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release [66.0kB]
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/multiverse Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates Release.gpg
Get:3 [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages [3,464B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/multiverse Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/universe Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/multiverse Packages
Hit http:...

---

### Post by jsacks on 2009-11-21
Sorry was missing the last entry into the terminal:

jared@dell-desktop:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following NEW packages will be installed:
  ureadahead
The following packages have been kept back:
  mencoder mplayer mplayer-nogui
The following packages will be upgraded:
  libxine1 libxine1-bin libxine1-console libxine1-ffmpeg libxine1-misc-plugins
  libxine1-plugins libxine1-x linux-headers-2.6.31-14
  linux-headers-2.6.31-14-generic linux-image-2.6.31-14-generic linux-libc-dev
  sreadahead
12 upgraded, 1 newly installed, 0 to remove and 3 not upgraded.
Need to get 2,005kB/43.8MB of archives.
After this operation, 393kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main libxine1-x 1.1.16.3-0ubuntu2~xine-vdpau~karmic~nvidiavdpauppa1
  404  Not Found
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main libxine1-bin 1.1.16.3-0ubuntu2~xine-vdpau~karmic~nvidiavdpauppa1
  404  Not Found
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main libxine1-plugins 1.1.16.3-0ubuntu2~xine-vdpau~karmic~nvidiavdpauppa1
  404  Not Found
Failed to fetch [http://ppa.launchpad.net/nvidia-vdpau/ppa/ubuntu/pool/main/x/xine-lib/libxine1-x_1.1.16.3-0ubuntu2~xine-vdpau~karmic~nvidiavdpauppa1_i386.deb](http://ppa.launchpad.net/nvidia-vdpau/ppa/ubuntu/pool/main/x/xine-lib/libxine1-x_1.1.16.3-0ubuntu2~xine-vdpau~karmic~nvidiavdpauppa1_i386.deb)  404  Not Found
Failed to fetch [http://ppa.launchpad.net/nvidia-vdpau/ppa/ubuntu/pool/main/x/xine-lib/libxine1-bin_1.1.16.3-0ubuntu2~xine-vdpau~karmic~nvidiavdpauppa1_i386.deb](http://ppa.launchpad.net/nvidia-vdpau/ppa/ubuntu/pool/main/x/xine-lib/libxine1-bin_1.1.16.3-0ubuntu2~xine-vdpau~karmic~nvidiavdpauppa1_i386.deb)  404  Not Found
Failed to fetch [http://ppa.launchpad.net/nvidia-vdpau/ppa/ubuntu/pool/main/x/xine-lib/libxine1-plugins_1.1.16.3-0ubuntu2~xine-vdpau~karmic~nvidiavdpauppa1_all.deb](http://ppa.launchpad.net/nvidia-vdpau/ppa/ubuntu/pool/main/x/xine-lib/libxine1-plugins_1.1.16.3-0ubuntu2~xine-vdpau~karmic~nvidiavdpauppa1_all.deb)  404  Not Found
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

---

### Post by yesint on 2009-11-22
> **jsacks said:**
> Sorry was missing the last entry into the terminal:

jared@dell-desktop:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following NEW packages will be installed:
  ureadahead
The following packages have been kept back:
  mencoder mplayer mplayer-nogui
The following packages will be upgraded:
  libxine1 libxine1-bin libxine1-console libxine1-ffmpeg libxine1-misc-plugins
  libxine1-plugins libxine1-x linux-headers-2.6.31-14
  linux-headers-2.6.31-14-generic linux-image-2.6.31-14-generic linux-libc-dev
  sreadahead
12 upgraded, 1 newly installed, 0 to remove and 3 not upgraded.
Need to get 2,005kB/43.8MB of archives.
After this operation, 393kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main libxine1-x 1.1.16.3-0ubuntu2~xine-vdpau~karmic~nvidiavdpauppa1
  404  Not Found
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main libxine1-bin 1.1.16.3-0ubuntu2~xine-vdpau~karmic~nvidiavdpauppa1
  404  Not Found
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main libxine1-plugins 1.1.16.3-0ubuntu2~xine-vdpau~karmic~nvidiavdpauppa1
  404  Not Found
Failed to fetch [http://ppa.launchpad.net/nvidia-vdpau/ppa/ubuntu/pool/main/x/xine-lib/libxine1-x_1.1.16.3-0ubuntu2~xine-vdpau~karmic~nvidiavdpauppa1_i386.deb](http://ppa.launchpad.net/nvidia-vdpau/ppa/ubuntu/pool/main/x/xine-lib/libxine1-x_1.1.16.3-0ubuntu2~xine-vdpau~karmic~nvidiavdpauppa1_i386.deb)  404  Not Found
Failed to fetch [http://ppa.launchpad.net/nvidia-vdpau/ppa/ubuntu/pool/main/x/xine-lib/libxine1-bin_1.1.16.3-0ubuntu2~xine-vdpau~karmic~nvidiavdpauppa1_i386.deb](http://ppa.launchpad.net/nvidia-vdpau/ppa/ubuntu/pool/main/x/xine-lib/libxine1-bin_1.1.16.3-0ubuntu2~xine-vdpau~karmic~nvidiavdpauppa1_i386.deb)  404  Not Found
Failed to fetch [http://ppa.launchpad.net/nvidia-vdpau/ppa/ubuntu/pool/main/x/xine-lib/libxine1-plugins_1.1.16.3-0ubuntu2~xine-vdpau~karmic~nvidiavdpauppa1_all.deb](http://ppa.launchpad.net/nvidia-vdpau/ppa/ubuntu/pool/main/x/xine-lib/libxine1-plugins_1.1.16.3-0ubuntu2~xine-vdpau~karmic~nvidiavdpauppa1_all.deb)  404  Not Found
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

Strange... It works like a charm for me. Check your connection and network settings. I had such failures from time to time with local mirror. Changing the mirror fixed this.

---

