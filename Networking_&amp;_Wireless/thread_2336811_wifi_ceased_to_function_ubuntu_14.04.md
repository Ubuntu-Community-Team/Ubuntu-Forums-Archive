---
title: "wifi ceased to function ubuntu 14.04"
date: 2016-09-11
forum: Networking &amp; Wireless
---

### Post by loutchoa on 2016-09-11
A few days ago, my son had its wifi disconnected and could not connect again.
The wifi is seen, the computer attempts to connect to it, but fails even before asking for a password.
This has been working fine for the last two years. 
I have included some output from lshw and history from updates.

Any idea is very welcome!Any idea is very welcome!
Cheers,
Francois


piece of lshw output:```

  *-network               
       description: Wireless interface
       product: AR9285 Wireless Network Adapter (PCI-Express)
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: wlan0
       version: 01
       serial: 90:4c:e5:8e:ff:fd
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=3.13.0-96-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:f1200000-f120ffff
```

I just check recent updates,
Start-Date: 2016-09-08  20:54:32
Commandline:```
 aptdaemon role='role-commit-packages' sender=':1.83'
Install: linux-headers-3.13.0-96-generic:amd64 (3.13.0-96.143), linux-headers-3.13.0-96:amd64 (3.13.0-96.143), linux-image-extra-3.13.0-96-generic:amd64 (3.13.0-96.143), linux-image-3.13.0-96-generic:amd64 (3.13.0-96.143)
Upgrade: linux-headers-generic:amd64 (3.13.0.94.102, 3.13.0.96.104), update-manager-core:amd64 (0.196.17, 0.196.21), isc-dhcp-common:amd64 (4.2.4-7ubuntu12.5, 4.2.4-7ubuntu12.6), whoopsie:amd64 (0.2.24.6ubuntu2, 0.2.24.6ubuntu3), eog:amd64 (3.10.2-0ubuntu5.1, 3.10.2-0ubuntu5.2), libharfbuzz-icu0:amd64 (0.9.27-1ubuntu1, 0.9.27-1ubuntu1.1), libfontconfig1:amd64 (2.11.0-0ubuntu4.1, 2.11.0-0ubuntu4.2), libfontconfig1:i386 (2.11.0-0ubuntu4.1, 2.11.0-0ubuntu4.2), python3-update-manager:amd64 (0.196.17, 0.196.21), fontconfig:amd64 (2.11.0-0ubuntu4.1, 2.11.0-0ubuntu4.2), libidn11:amd64 (1.28-1ubuntu2, 1.28-1ubuntu2.1), ssh-askpass-gnome:amd64 (6.6p1-2ubuntu2.7, 6.6p1-2ubuntu2.8), fontconfig-config:amd64 (2.11.0-0ubuntu4.1, 2.11.0-0ubuntu4.2), curl:amd64 (7.35.0-1ubuntu2.8, 7.35.0-1ubuntu2.9), libharfbuzz0b:amd64 (0.9.27-1ubuntu1, 0.9.27-1ubuntu1.1), gnupg:amd64 (1.4.16-1ubuntu2.3, 1.4.16-1ubuntu2.4), update-notifier-common:amd64 (0.154.1ubuntu1, 0.154.1ubuntu2), gnome-contacts:amd64 (3.8.3-1ubuntu1, 3.8.3-1ubuntu1.1), openjdk-7-jre-headless:amd64 (7u101-2.6.6-0ubuntu0.14.04.1, 7u111-2.6.7-0ubuntu0.14.04.3), libwhoopsie0:amd64 (0.2.24.6ubuntu2, 0.2.24.6ubuntu3), gnome-keyring:amd64 (3.10.1-1ubuntu4.2, 3.10.1-1ubuntu4.3), update-notifier:amd64 (0.154.1ubuntu1, 0.154.1ubuntu2), openssh-client:amd64 (6.6p1-2ubuntu2.7, 6.6p1-2ubuntu2.8), isc-dhcp-client:amd64 (4.2.4-7ubuntu12.5, 4.2.4-7ubuntu12.6), openjdk-7-jre:amd64 (7u101-2.6.6-0ubuntu0.14.04.1, 7u111-2.6.7-0ubuntu0.14.04.3), libpam-gnome-keyring:amd64 (3.10.1-1ubuntu4.2, 3.10.1-1ubuntu4.3), libcurl3:amd64 (7.35.0-1ubuntu2.8, 7.35.0-1ubuntu2.9), gpgv:amd64 (1.4.16-1ubuntu2.3, 1.4.16-1ubuntu2.4), libp11-kit-gnome-keyring:amd64 (3.10.1-1ubuntu4.2, 3.10.1-1ubuntu4.3), linux-libc-dev:amd64 (3.13.0-94.141, 3.13.0-96.143), update-manager:amd64 (0.196.17, 0.196.21), geogebra5:amd64 (5.0.266.0-48701, 5.0.272.0-49051), linux-image-generic:amd64 (3.13.0.94.102, 3.13.0.96.104), libgcrypt11:amd64 (1.5.3-2ubuntu4.3, 1.5.3-2ubuntu4.4), libgcrypt11:i386 (1.5.3-2ubuntu4.3, 1.5.3-2ubuntu4.4), libcurl3-gnutls:amd64 (7.35.0-1ubuntu2.8, 7.35.0-1ubuntu2.9), linux-generic:amd64 (3.13.0.94.102, 3.13.0.96.104)
End-Date: 2016-09-08  20:58:34
```
~
~

---

### Post by loutchoa on 2016-09-18
Dear forum,
I am still stuck, any idea of what kind of information I should look at? simple checks on hardware to know whether it's properly functioning?
Cheers,
François

---

### Post by wildmanne39 on 2016-09-18
Hi, please click on the wireless script in my signature and follow the directions for running the script and posting the results here. 
Thanks

---

