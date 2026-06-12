---
title: "Minimal Install"
date: 2011-08-22
forum: New to Ubuntu
---

### Post by arbi07 on 2011-08-22
Hi, 

This is with regard about what does it really mean to have a minimal install. I read somewhere that you customize what you want to do with your Ubuntu like picking the window manager, applications etc... But what I would like to ask is that why does it says Minimal Install (insert distro here e.g. Natty). Does it mean it will have the same capabilities of that certain version and you just pick what applications you will be using? I am just curious, because I am meticulous in picking the apps. Thanks for the reply.

---

### Post by ron999 on 2011-08-22
> **arbi07 said:**
>  Does it mean it will have the same capabilities of that certain version and you just pick what applications you will be using?..
Yes, that's right.
After you do a minimal install using the 'mini iso' all you see is the monochrome Linux login screen.
No desktop.
You need to install everything else yourself.

From there I install **gdm** (login window) and **gnome-core** (desktop).
Then afterwards add other programs.

32 bit Natty mini iso is here:- [http://archive.ubuntu.com/ubuntu/dists/natty/main/installer-i386/current/images/netboot/]("http://archive.ubuntu.com/ubuntu/dists/natty/main/installer-i386/current/images/netboot/")
64 bit Natty mini iso is here:- [http://archive.ubuntu.com/ubuntu/dists/natty/main/installer-amd64/current/images/netboot/]("http://archive.ubuntu.com/ubuntu/dists/natty/main/installer-amd64/current/images/netboot/")

---

### Post by sisco311 on 2011-08-22
The minimal install provides a fully functional command-line only Linux environment. It installs a bootloader(grub), a kernel, ubuntu-minimal and ubuntu-standard.  

ubuntu-minmal:
```

Depends: adduser, apt, apt-utils, bzip2, console-setup, debconf, debconf-i18n, eject, gnupg, ifupdown, initramfs-tools, iproute, iputils-ping, isc-dhcp-client, kbd, less, locales, lsb-release, makedev, mawk, module-init-tools, net-tools, netbase, netcat-openbsd, ntpdate, passwd, procps, python, rsyslog, sudo, tzdata, ubuntu-keyring, udev, upstart, ureadahead, vim-tiny, whiptail
Description: Minimal core of Ubuntu
 This package depends on all of the packages in the Ubuntu minimal system,
 that is a functional command-line system with the following capabilities:
 .
  - Boot
  - Detect hardware
  - Connect to a network
  - Install packages
  - Perform basic diagnostics
 .
 It is also used to help ensure proper upgrades, so it is recommended that
 it not be removed.

```

ubuntu-standard:
```

Depends: at, busybox-static, cpio, cron, dmidecode, dnsutils, dosfstools, ed, file, ftp, hdparm, info, iptables, language-selector-common, logrotate, lshw, lsof, ltrace, man-db, memtest86+, mime-support, parted, pciutils, popularity-contest, psmisc, rsync, strace, time, usbutils, wget
Recommends: apparmor, apt-transport-https, bash-completion, command-not-found, friendly-recovery, iputils-tracepath, irqbalance, manpages, mlocate, mtr-tiny, nano, ntfs-3g, openssh-client, plymouth, plymouth-theme-ubuntu-text, ppp, pppconfig, pppoeconf, tcpdump, telnet, ufw, update-manager-core, uuid-runtime
Description: The Ubuntu standard system
 This package depends on all of the packages in the Ubuntu standard system.
 This set of packages provides a comfortable command-line Unix-like
 environment.
 .
 It is also used to help ensure proper upgrades, so it is recommended that
 it not be removed.

```

---

### Post by elliotn on 2011-08-22
> **sisco311 said:**
> The minimal install provides a fully functional command-line only Linux environment. It installs a bootloader(grub), a kernel, ubuntu-minimal and ubuntu-standard.  

ubuntu-minmal:
```

Depends: adduser, apt, apt-utils, bzip2, console-setup, debconf, debconf-i18n, eject, gnupg, ifupdown, initramfs-tools, iproute, iputils-ping, isc-dhcp-client, kbd, less, locales, lsb-release, makedev, mawk, module-init-tools, net-tools, netbase, netcat-openbsd, ntpdate, passwd, procps, python, rsyslog, sudo, tzdata, ubuntu-keyring, udev, upstart, ureadahead, vim-tiny, whiptail
Description: Minimal core of Ubuntu
 This package depends on all of the packages in the Ubuntu minimal system,
 that is a functional command-line system with the following capabilities:
 .
  - Boot
  - Detect hardware
  - Connect to a network
  - Install packages
  - Perform basic diagnostics
 .
 It is also used to help ensure proper upgrades, so it is recommended that
 it not be removed.

```

ubuntu-standard:
```

Depends: at, busybox-static, cpio, cron, dmidecode, dnsutils, dosfstools, ed, file, ftp, hdparm, info, iptables, language-selector-common, logrotate, lshw, lsof, ltrace, man-db, memtest86+, mime-support, parted, pciutils, popularity-contest, psmisc, rsync, strace, time, usbutils, wget
Recommends: apparmor, apt-transport-https, bash-completion, command-not-found, friendly-recovery, iputils-tracepath, irqbalance, manpages, mlocate, mtr-tiny, nano, ntfs-3g, openssh-client, plymouth, plymouth-theme-ubuntu-text, ppp, pppconfig, pppoeconf, tcpdump, telnet, ufw, update-manager-core, uuid-runtime
Description: The Ubuntu standard system
 This package depends on all of the packages in the Ubuntu standard system.
 This set of packages provides a comfortable command-line Unix-like
 environment.
 .
 It is also used to help ensure proper upgrades, so it is recommended that
 it not be removed.

```

why not install the whole Ubuntu then remove all apps u don't like

---

### Post by donkyhotay on 2011-08-22
> **elliotn said:**
> why not install the whole Ubuntu then remove all apps u don't like

Define an "app". With the minimal install you're installing you're own desktop environments from the beginning. Things like desktop environments are programs or 'apps' (at least to the computer) though most people wouldn't consider them as such. If you're an average user that just wants to simply replace firefox with chromium then the regular installation and uninstalling would be fine. But if you want to do something like compile your own version of gnome from source code or to have a very lean system, it is much easier to do a minimal install and then install what you want then to uninstall then reinstall the new versions.

---

### Post by arbi07 on 2011-08-23
Thanks for the reply. Yep, I am actually looking for a lean system. I am the type who wants to maximize things so that's the reason why. So it is really like just getting the apps that I need(including DE, Window manager etc)

Another question, when I do it that way, do I have the option to partition my drive?

And I am also thinking if there is such a thing as "this app cannot co-exist with this one" producing an error(worst system crash)?

Thanks again for the reply and patience. Still enjoying the part of knowing the terms and other technicalities..

---

### Post by kartabosh on 2011-08-23
i suggest you try to install ubuntu minimal in a virtualbox first
it's much easier to check if you know what you're doing in a virtual environment
if you succeed there you can go ahead and install it on your hdd

---

### Post by ron999 on 2011-08-23
> **arbi07 said:**
>  when I do it that way, do I have the option to partition my drive?

Yes.

---

### Post by sisco311 on 2011-08-23
> **arbi07 said:**
> 
Another question, when I do it that way, do I have the option to partition my drive?


Of course. The text-based installer, used by the Alternate and Minimal CD, also allows more advanced installation options (LVM and LUKS encrypted file systems, OEM Install, Option to install an LTSP Server...) which are not available with the Standard LiveCD.


> **arbi07 said:**
> 
And I am also thinking if there is such a thing as "this app cannot co-exist with this one" producing an error(worst system crash)?

No, if you use the package manager (apt: apt-get, synaptic or Ubuntu Software Center) to install & remove software.


Check out this guide, it  has some nice screenshots: [http://psychocats.net/ubuntu/minimal](http://psychocats.net/ubuntu/minimal)

---

### Post by donkyhotay on 2011-08-24
If you really want a lean/mean system you might try arch linux. It's a little different and generally more "advanced" compared to ubuntu but it is designed to be built from the ground up with exactly what you want and nothing you don't. As others have suggested I would also recommend doing all this in a VM once or twice before attempting it for real. The last thing you want is to get stuck in the middle of the install, uncertain how to proceed, and be unable to go online to figure out how to fix it.

---

