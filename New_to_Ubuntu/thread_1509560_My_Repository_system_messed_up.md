---
title: "My Repository system messed up"
date: 2010-06-14
forum: New to Ubuntu
---

### Post by Polemistis on 2010-06-14
Hi,

This problem started to occur when I installed broadcom drivers and my computer shutdown half way during the installation. Later I managed to install my wireless, but I still get problems with dpkg.

Whenever I install something from apt-get, I get problems.
If I do
sudo apt-get install vlc

I get this:
> 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
  vlc: Depends: vlc-nox (= 1.0.6-1ubuntu1.1) but it is not going to be installed
       Depends: libsdl-image1.2 (>= 1.2.5) but it is not installable
       Depends: libtar but it is not installable
       Recommends: vlc-plugin-pulse (= 1.0.6-1ubuntu1.1) but it is not going to be installed
E: Broken packages


Some stuff does install. But even after successful install I get a dpkg error, which means nothing to me. Although the package does get installed. For instance, I installed Opera downloading the deb from the site, after it finished installing I got the dpkg error.

I tried now to install the win32 codecs from ubuntu software centre and I get:

> installArchives() failed: Selecting previously deselected package w32codecs.

(Reading database ... 
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
(Reading database ... 163909 files and directories currently installed.)

Unpacking w32codecs (from .../w32codecs_1%3a20100303-0.0medibuntu1_i386.deb) ...

Setting up linux-image-2.6.32-22-generic (2.6.32-22.36) ...

Running depmod.

update-initramfs: Generating /boot/initrd.img-2.6.32-22-generic

Running postinst hook script /usr/sbin/update-grub.

Generating grub.cfg ...

Found linux image: /boot/vmlinuz-2.6.32-22-generic

Found initrd image: /boot/initrd.img-2.6.32-22-generic

Found linux image: /boot/vmlinuz-2.6.32-21-generic

Found initrd image: /boot/initrd.img-2.6.32-21-generic

Found memtest86+ image: /boot/memtest86+.bin

Found Windows 7 (loader) on /dev/sda1

done

Examining /etc/kernel/postinst.d.

run-parts: executing /etc/kernel/postinst.d/dkms 2.6.32-22-generic /boot/vmlinuz-2.6.32-22-generic

run-parts: failed to exec /etc/kernel/postinst.d/dkms: Exec format error

run-parts: /etc/kernel/postinst.d/dkms exited with return code 1

Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.32-22-generic.postinst line 1003.

dpkg: error processing linux-image-2.6.32-22-generic (--configure):

 subprocess installed post-installation script returned error exit status 2

Setting up dkms (2.1.1.2-2fakesync1) ...

dpkg (subprocess): unable to execute installed post-installation script: Exec format error

dpkg: error processing dkms (--configure):

 subprocess installed post-installation script returned error exit status 2

dpkg: dependency problems prevent configuration of linux-image-generic:

 linux-image-generic depends on linux-image-2.6.32-22-generic; however:

  Package linux-image-2.6.32-22-generic is not configured yet.

dpkg: error processing linux-image-generic (--configure):

 dependency problems - leaving unconfigured

dpkg: dependency problems prevent configuration of linux-generic:

 linux-generic depends on linux-image-generic (= 2.6.32.22.23); however:

  Package linux-image-generic is not configured yet.

dpkg: error processing linux-generic (--configure):

 dependency problems - leaving unconfigured

Setting up linux-headers-2.6.32-22-generic (2.6.32-22.36) ...

No apport report written because the error message indicates its a followup error from a previous failure.
No apport report written because MaxReports is reached already
Examining /etc/kernel/header_postinst.d.

run-parts: executing /etc/kernel/header_postinst.d/dkms 2.6.32-22-generic /boot/vmlinuz-2.6.32-22-generic

run-parts: failed to exec /etc/kernel/header_postinst.d/dkms: Exec format error

run-parts: /etc/kernel/header_postinst.d/dkms exited with return code 1

Failed to process /etc/kernel/header_postinst.d at /var/lib/dpkg/info/linux-headers-2.6.32-22-generic.postinst line 110.

dpkg: error processing linux-headers-2.6.32-22-generic (--configure):

 subprocess installed post-installation script returned error exit status 2

dpkg: dependency problems prevent configuration of linux-headers-generic:

 linux-headers-generic depends on linux-headers-2.6.32-22-generic; however:

  Package linux-headers-2.6.32-22-generic is not configured yet.

dpkg: error processing linux-headers-generic (--configure):

 dependency problems - leaving unconfigured

Setting up w32codecs (1:20100303-0.0medibuntu1) ...

No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
Errors were encountered while processing:

 linux-image-2.6.32-22-generic

 dkms

 linux-image-generic

 linux-generic

 linux-headers-2.6.32-22-generic

 linux-headers-generic

Setting up dkms (2.1.1.2-2fakesync1) ...

dpkg (subprocess): unable to execute installed post-installation script: Exec format error

dpkg: error processing dkms (--configure):

 subprocess installed post-installation script returned error exit status 2

Setting up linux-headers-2.6.32-22-generic (2.6.32-22.36) ...

Examining /etc/kernel/header_postinst.d.

run-parts: executing /etc/kernel/header_postinst.d/dkms 2.6.32-22-generic /boot/vmlinuz-2.6.32-22-generic

run-parts: failed to exec /etc/kernel/header_postinst.d/dkms: Exec format error

run-parts: /etc/kernel/header_postinst.d/dkms exited with return code 1

Failed to process /etc/kernel/header_postinst.d at /var/lib/dpkg/info/linux-headers-2.6.32-22-generic.postinst line 110.

dpkg: error processing linux-headers-2.6.32-22-generic (--configure):

 subprocess installed post-installation script returned error exit status 2

dpkg: dependency problems prevent configuration of linux-headers-generic:

 linux-headers-generic depends on linux-headers-2.6.32-22-generic; however:

  Package linux-headers-2.6.32-22-generic is not configured yet.

dpkg: error processing linux-headers-generic (--configure):

 dependency problems - leaving unconfigured

Setting up linux-image-2.6.32-22-generic (2.6.32-22.36) ...

Running depmod.

update-initramfs: Generating /boot/initrd.img-2.6.32-22-generic

Running postinst hook script /usr/sbin/update-grub.

Generating grub.cfg ...

Found linux image: /boot/vmlinuz-2.6.32-22-generic

Found initrd image: /boot/initrd.img-2.6.32-22-generic

Found linux image: /boot/vmlinuz-2.6.32-21-generic

Found initrd image: /boot/initrd.img-2.6.32-21-generic

Found memtest86+ image: /boot/memtest86+.bin

Found Windows 7 (loader) on /dev/sda1

done

Examining /etc/kernel/postinst.d.

run-parts: executing /etc/kernel/postinst.d/dkms 2.6.32-22-generic /boot/vmlinuz-2.6.32-22-generic

run-parts: failed to exec /etc/kernel/postinst.d/dkms: Exec format error

run-parts: /etc/kernel/postinst.d/dkms exited with return code 1

Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.32-22-generic.postinst line 1003.

dpkg: error processing linux-image-2.6.32-22-generic (--configure):

 subprocess installed post-installation script returned error exit status 2

dpkg: dependency problems prevent configuration of linux-image-generic:

 linux-image-generic depends on linux-image-2.6.32-22-generic; however:

  Package linux-image-2.6.32-22-generic is not configured yet.

dpkg: error processing linux-image-generic (--configure):

 dependency problems - leaving unconfigured

dpkg: dependency problems prevent configuration of linux-generic:

 linux-generic depends on linux-image-generic (= 2.6.32.22.23); however:

  Package linux-image-generic is not configured yet.

dpkg: error processing linux-generic (--configure):

 dependency problems - leaving unconfigured




I'm running Ubuntu 10.04.
Can someone help me to install vlc?

---

### Post by Ozymandias_117 on 2010-06-14
I would try
```
sudo aptitude update
sudo dpkg --configure -a
sudo aptitude full-upgrade
``` then reboot

---

### Post by sidzen on 2010-06-14
If [Ozymandias_117]("http://ubuntuforums.org/member.php?u=805682") 's suggestion does not work as desired, please execute the following and post the output
[PHP]sudo apt-get build-dep vlc[/PHP]

---

### Post by Polemistis on 2010-06-14
> **Ozymandias_117 said:**
> I would try
```
sudo aptitude update
sudo dpkg --configure -a
sudo aptitude full-upgrade
``` then reboot

When I do a sudo dpkg --configure -a, I get the following error:
> 
Setting up dkms (2.1.1.2-2fakesync1) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing dkms (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up linux-headers-2.6.32-22-generic (2.6.32-22.36) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms 2.6.32-22-generic /boot/vmlinuz-2.6.32-22-generic
run-parts: failed to exec /etc/kernel/header_postinst.d/dkms: Exec format error
run-parts: /etc/kernel/header_postinst.d/dkms exited with return code 1
Failed to process /etc/kernel/header_postinst.d at /var/lib/dpkg/info/linux-headers-2.6.32-22-generic.postinst line 110.
dpkg: error processing linux-headers-2.6.32-22-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-headers-generic:
 linux-headers-generic depends on linux-headers-2.6.32-22-generic; however:
  Package linux-headers-2.6.32-22-generic is not configured yet.
dpkg: error processing linux-headers-generic (--configure):
 dependency problems - leaving unconfigured
Setting up linux-image-2.6.32-22-generic (2.6.32-22.36) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.32-22-generic
Running postinst hook script /usr/sbin/update-grub.
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-22-generic
Found initrd image: /boot/initrd.img-2.6.32-22-generic
Found linux image: /boot/vmlinuz-2.6.32-21-generic
Found initrd image: /boot/initrd.img-2.6.32-21-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
done
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 2.6.32-22-generic /boot/vmlinuz-2.6.32-22-generic
run-parts: failed to exec /etc/kernel/postinst.d/dkms: Exec format error
run-parts: /etc/kernel/postinst.d/dkms exited with return code 1
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.32-22-generic.postinst line 1003.
dpkg: error processing linux-image-2.6.32-22-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.32-22-generic; however:
  Package linux-image-2.6.32-22-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.32.22.23); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 dkms
 linux-headers-2.6.32-22-generic
 linux-headers-generic
 linux-image-2.6.32-22-generic
 linux-image-generic
 linux-generic


---

### Post by Polemistis on 2010-06-14
> **sidzen said:**
> If [Ozymandias_117]("http://ubuntuforums.org/member.php?u=805682") 's suggestion does not work as desired, please execute the following and post the output
[PHP]sudo apt-get build-dep vlc[/PHP]

I get the following error when I try what u suggested:

> Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Build-Depends dependency for vlc cannot be satisfied because the package liba52-0.7.4-dev cannot be found


---

### Post by sidzen on 2010-06-14
> **Polemistis said:**
> I get the following error when I try what u suggested:

This makes it more obvious that repositories need to be added to the /etc/apt/sources.lst
(sources list) file.  
To do so, please go to [https://help.ubuntu.com](https://help.ubuntu.com), choose your release, then type in "medibuntu repositories."  This will explain better than I how to make things work.  (And we all had to go through this to learn).

Best wishes!

---

### Post by Polemistis on 2010-06-14
> **sidzen said:**
> This makes it more obvious that repositories need to be added to the /etc/apt/sources.lst
(sources list) file.  
To do so, please go to [https://help.ubuntu.com](https://help.ubuntu.com), choose your release, then type in "medibuntu repositories."  This will explain better than I how to make things work.  (And we all had to go through this to learn).

Best wishes!

Hiya,

I take it you mean this website: [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

I tried 

> sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update


in my earlier attempts before starting this thread. I still get the same error.
This is the error I get:
> 
--2010-06-14 18:16:58--  [http://www.medibuntu.org/sources.list.d/lucid.list](http://www.medibuntu.org/sources.list.d/lucid.list)
Resolving [www.medibuntu.org](www.medibuntu.org)... 87.98.242.110
Connecting to [www.medibuntu.org|87.98.242.110|:80](www.medibuntu.org|87.98.242.110|:80)... connected.
HTTP request sent, awaiting response... 200 OK
Length: 268 [text/plain]
Saving to: `/etc/apt/sources.list.d/medibuntu.list'

100%[======================================>] 268         --.-K/s   in 0s      

2010-06-14 18:16:58 (8.69 MB/s) - `/etc/apt/sources.list.d/medibuntu.list' saved [268/268]

Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release.gpg
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) lucid/partner Translation-en_GB
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg
Ign [http://ppa.launchpad.net/tualatrix/ppa/ubuntu/](http://ppa.launchpad.net/tualatrix/ppa/ubuntu/) lucid/main Translation-en_GB
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid Release.gpg
Ign [http://packages.medibuntu.org/](http://packages.medibuntu.org/) lucid/free Translation-en_GB
Ign [http://packages.medibuntu.org/](http://packages.medibuntu.org/) lucid/non-free Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid Release.gpg
Hit [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid/main Translation-en_GB
Hit [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_GB
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release
Hit [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_GB
Hit [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid-updates Release.gpg
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_GB
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en_GB
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_GB
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-en_GB
Hit [http://deb.opera.com](http://deb.opera.com) stable Release.gpg
Ign [http://deb.opera.com/opera/](http://deb.opera.com/opera/) stable/non-free Translation-en_GB
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid Release
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid-backports Release.gpg
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid-backports/main Translation-en_GB
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid-backports/restricted Translation-en_GB
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid/free Packages
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid-backports/universe Translation-en_GB
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid-backports/multiverse Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid Release
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid-updates Release
Hit [http://deb.opera.com](http://deb.opera.com) stable Release
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid-backports Release
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid/non-free Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid/main Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid/restricted Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid/main Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid/restricted Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid/universe Packages
Ign [http://deb.opera.com](http://deb.opera.com) stable/non-free Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid/universe Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid/multiverse Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid/multiverse Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid-updates/main Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid-updates/restricted Packages
Ign [http://deb.opera.com](http://deb.opera.com) stable/non-free Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid-updates/main Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid-updates/restricted Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid-updates/universe Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid-updates/universe Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid-updates/multiverse Packages
Hit [http://deb.opera.com](http://deb.opera.com) stable/non-free Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid-updates/multiverse Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid-backports/main Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid-backports/restricted Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid-backports/universe Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid-backports/multiverse Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid-backports/main Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid-backports/restricted Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid-backports/universe Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid-backports/multiverse Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release.gpg
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main Translation-en_GB
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_GB
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_GB
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en_GB
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Sources
Reading package lists...
Reading package lists...
Building dependency tree...
Reading state information...
medibuntu-keyring is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
6 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up linux-image-2.6.32-22-generic (2.6.32-22.36) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.32-22-generic
Running postinst hook script /usr/sbin/update-grub.
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-22-generic
Found initrd image: /boot/initrd.img-2.6.32-22-generic
Found linux image: /boot/vmlinuz-2.6.32-21-generic
Found initrd image: /boot/initrd.img-2.6.32-21-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
done
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 2.6.32-22-generic /boot/vmlinuz-2.6.32-22-generic
run-parts: failed to exec /etc/kernel/postinst.d/dkms: Exec format error
run-parts: /etc/kernel/postinst.d/dkms exited with return code 1
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.32-22-generic.postinst line 1003.
dpkg: error processing linux-image-2.6.32-22-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up dkms (2.1.1.2-2fakesync1) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing dkms (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.32-22-generic; however:
  Package linux-image-2.6.32-22-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.32.22.23); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
Setting up linux-headers-2.6.32-22-generic (2.6.32-22.36) ...
No apport report written because the error message indicates it's a follow-up error from a previous failure.
                            No apport report written because MaxReports has already been reached
                Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms 2.6.32-22-generic /boot/vmlinuz-2.6.32-22-generic
run-parts: failed to exec /etc/kernel/header_postinst.d/dkms: Exec format error
run-parts: /etc/kernel/header_postinst.d/dkms exited with return code 1
Failed to process /etc/kernel/header_postinst.d at /var/lib/dpkg/info/linux-headers-2.6.32-22-generic.postinst line 110.
dpkg: error processing linux-headers-2.6.32-22-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-headers-generic:
 linux-headers-generic depends on linux-headers-2.6.32-22-generic; however:
  Package linux-headers-2.6.32-22-generic is not configured yet.
dpkg: error processing linux-headers-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports has already been reached
                                                                    No apport report written because MaxReports has already been reached
                                                        Errors were encountered while processing:
 linux-image-2.6.32-22-generic
 dkms
 linux-image-generic
 linux-generic
 linux-headers-2.6.32-22-generic
 linux-headers-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)


do u have any solutions?

---

### Post by Polemistis on 2010-06-14
The problem is related to more than the repository.
For instance, I tried to install Wine following the steps on this site: [http://www.winehq.org/download/deb](http://www.winehq.org/download/deb).

I then did:
> sudo apt-get update
sudo apt-get install wine

and I received the following error:

> The following packages have unmet dependencies.
  wine: Depends: wine1.2 but it is not going to be installed
E: Broken packages

Then I did:
> sudo apt-get install wine1.2

and I got the following error:

> The following packages have unmet dependencies.
  wine1.2: Depends: libmpg123-0 (>= 1.6.2) but it is not installable
           Recommends: wine1.2-gecko but it is not installable
           Recommends: ttf-mscorefonts-installer but it is not installable
E: Broken packages


Something is seriously wrong with my repository. ANyone know of a fix??

---

### Post by sidzen on 2010-06-14
If you wish to stick with Lucid Lynx, see [http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal), for details on building your own ubuntu with only what the builder wants, including choices a full install does not give a person (like the LXDE desktop, in my preference).  Note that I tried lubuntu and found it "buggy."

Then, after a minimal install and choosing ones own packages and associated libraries, the only one a person can blame for something not working is oneself.  That's what I'd do in your case, amigo!  My experience in linux has shown one must be willing to start over to get it right; and you're correct in saying the problem goes deeper than it appears.  I've yet to hear anyone admit it, however.

bodhi.zazen turned me on to this idea in one of his responses, just today.  MIX YOUR OWN!

---

### Post by oldos2er on 2010-06-14
> **Polemistis said:**
> Something is seriously wrong with my repository. ANyone know of a fix??

Go into System, Administration, Software Sources, and make sure all repositories including Source Code are checked.

---

### Post by Polemistis on 2010-06-15
> **sidzen said:**
> If you wish to stick with Lucid Lynx, see [http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal), for details on building your own ubuntu with only what the builder wants, including choices a full install does not give a person (like the LXDE desktop, in my preference).  Note that I tried lubuntu and found it "buggy."

Then, after a minimal install and choosing ones own packages and associated libraries, the only one a person can blame for something not working is oneself.  That's what I'd do in your case, amigo!  My experience in linux has shown one must be willing to start over to get it right; and you're correct in saying the problem goes deeper than it appears.  I've yet to hear anyone admit it, however.

bodhi.zazen turned me on to this idea in one of his responses, just today.  MIX YOUR OWN!




Thanks for the advice.. but it is solved now.

The Solution: Re-installed Ubuntu :)
This time I made sure it didn't switch off while downloading/installing the wireless drivers.

Now everything works and I can install Ubuntu Software Centre also.

Thanks guys/.!

---

