---
title: "Vivobook S14 WiFi Stopped Working in Ubuntu 19.10 after running dist-upgrade"
date: 2020-03-04
forum: Networking &amp; Wireless
---

### Post by nor-wanderer on 2020-03-04
On my brand new Asus Vivobook S14 S432FA, I've installed Ubuntu 19.10.

After a standard full installation, my WiFi works fine, but as soon as I run an upgrade using dist-upgrade WiFi will not stop working immediately, but after reboot.

If I perform a full installation with the option to include updates during installation, WiFi will also stop working during the first boot of the new installation.

This is information from lshw before I ran the upgrade, when WiFi was still working:
```

sudo lshw -C network
  *-network                 
       description: Wireless interface
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 14.3
       bus info: pci@0000:00:14.3
       logical name: wlo1
       version: 00
       serial: [Removed]
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=5.3.0-18-generic firmware=48.4fa0041f.0 ip=10.3.3.13 latency=0 link=yes multicast=yes wireless=IEEE 802.11
       resources: irq:16 memory:b121c000-b121ffff

```
This is information after the upgrade (when WiFi is no longer working)
```

sudo lshw -C network
  *-network                 
       description: Network controller
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 14.3
       bus info: pci@0000:00:14.3
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list
       configuration: driver=iwlwifi latency=0
       resources: irq:16 memory:b121c000-b121ffff

```
Here's the packages which were upgraded:
```

sudo apt list --upgradable
Listing... Done
amd64-microcode/eoan-updates,eoan-security 3.20191021.1+really3.20181128.1ubuntu2 amd64 [upgradable from: 3.20181128.1ubuntu2]
apport-gtk/eoan-updates,eoan-updates 2.20.11-0ubuntu8.5 all [upgradable from: 2.20.11-0ubuntu8]
apport/eoan-updates,eoan-updates 2.20.11-0ubuntu8.5 all [upgradable from: 2.20.11-0ubuntu8]
aptdaemon-data/eoan-updates,eoan-updates,eoan-security,eoan-security 1.1.1+bzr982-0ubuntu28.1 all [upgradable from: 1.1.1+bzr982-0ubuntu28]
aptdaemon/eoan-updates,eoan-updates,eoan-security,eoan-security 1.1.1+bzr982-0ubuntu28.1 all [upgradable from: 1.1.1+bzr982-0ubuntu28]
aspell/eoan-updates,eoan-security 0.60.7-3ubuntu0.1 amd64 [upgradable from: 0.60.7-3]
base-files/eoan-updates 10.2ubuntu7.19.10.0 amd64 [upgradable from: 10.2ubuntu7]
bind9-host/eoan-updates,eoan-security 1:9.11.5.P4+dfsg-5.1ubuntu2.1 amd64 [upgradable from: 1:9.11.5.P4+dfsg-5.1ubuntu2]
binutils-common/eoan-updates,eoan-security 2.33-2ubuntu1.2 amd64 [upgradable from: 2.33-2ubuntu1]
binutils-x86-64-linux-gnu/eoan-updates,eoan-security 2.33-2ubuntu1.2 amd64 [upgradable from: 2.33-2ubuntu1]
binutils/eoan-updates,eoan-security 2.33-2ubuntu1.2 amd64 [upgradable from: 2.33-2ubuntu1]
bluez-cups/eoan-updates 5.50-0ubuntu5 amd64 [upgradable from: 5.50-0ubuntu4]
bluez-obexd/eoan-updates 5.50-0ubuntu5 amd64 [upgradable from: 5.50-0ubuntu4]
bluez/eoan-updates 5.50-0ubuntu5 amd64 [upgradable from: 5.50-0ubuntu4]
bsdutils/eoan-updates 1:2.34-0.1ubuntu2.2 amd64 [upgradable from: 1:2.34-0.1ubuntu2]
cpio/eoan-updates,eoan-security 2.12+dfsg-9ubuntu0.1 amd64 [upgradable from: 2.12+dfsg-9]
dmidecode/eoan-updates 3.2-2ubuntu0.1 amd64 [upgradable from: 3.2-2]
dnsutils/eoan-updates,eoan-security 1:9.11.5.P4+dfsg-5.1ubuntu2.1 amd64 [upgradable from: 1:9.11.5.P4+dfsg-5.1ubuntu2]
e2fsprogs/eoan-updates,eoan-security 1.45.3-4ubuntu2.1 amd64 [upgradable from: 1.45.3-4ubuntu2]
fdisk/eoan-updates 2.34-0.1ubuntu2.2 amd64 [upgradable from: 2.34-0.1ubuntu2]
file/eoan-updates,eoan-security 1:5.37-5ubuntu0.1 amd64 [upgradable from: 1:5.37-5]
firefox-locale-en/eoan-updates,eoan-security 73.0.1+build1-0ubuntu0.19.10.1 amd64 [upgradable from: 69.0.3+build1-0ubuntu1]
fonts-opensymbol/eoan-updates,eoan-updates 2:102.11+LibO6.3.4-0ubuntu0.19.10.1 all [upgradable from: 2:102.11+LibO6.3.2-0ubuntu2]
fwupd-signed/eoan-updates 1.10.2+1.2.10-1ubuntu4 amd64 [upgradable from: 1.10+1.2.10-1ubuntu2]
fwupd/eoan-updates 1.2.10-1ubuntu4 amd64 [upgradable from: 1.2.10-1ubuntu2]
ghostscript-x/eoan-updates,eoan-security 9.27~dfsg+0-0ubuntu3.1 amd64 [upgradable from: 9.27~dfsg+0-0ubuntu3]
ghostscript/eoan-updates,eoan-security 9.27~dfsg+0-0ubuntu3.1 amd64 [upgradable from: 9.27~dfsg+0-0ubuntu3]
gir1.2-gnomedesktop-3.0/eoan-updates 3.34.2-2ubuntu1~19.10.1 amd64 [upgradable from: 3.34.1-1ubuntu1]
gir1.2-javascriptcoregtk-4.0/eoan-updates,eoan-security 2.26.4-0ubuntu0.19.10.1 amd64 [upgradable from: 2.26.1-3]
gir1.2-mutter-5/eoan-updates 3.34.1+git20191107-1ubuntu1~19.10.1 amd64 [upgradable from: 3.34.1-1ubuntu1]
gir1.2-nm-1.0/eoan-updates 1.20.4-2ubuntu2.2 amd64 [upgradable from: 1.20.4-2ubuntu2]
gir1.2-snapd-1/eoan-updates 1.49-0ubuntu1.19.10.0 amd64 [upgradable from: 1.49-0ubuntu1]
gir1.2-webkit2-4.0/eoan-updates,eoan-security 2.26.4-0ubuntu0.19.10.1 amd64 [upgradable from: 2.26.1-3]
gnome-desktop3-data/eoan-updates,eoan-updates 3.34.2-2ubuntu1~19.10.1 all [upgradable from: 3.34.1-1ubuntu1]
gnome-shell-common/eoan-updates,eoan-updates 3.34.1+git20191024-1ubuntu1~19.10.1 all [upgradable from: 3.34.1-1ubuntu1]
gnome-shell/eoan-updates 3.34.1+git20191024-1ubuntu1~19.10.1 amd64 [upgradable from: 3.34.1-1ubuntu1]
gnome-software-common/eoan-updates,eoan-updates 3.30.6-2ubuntu10.19.10.0 all [upgradable from: 3.30.6-2ubuntu10]
gnome-software-plugin-snap/eoan-updates 3.30.6-2ubuntu10.19.10.0 amd64 [upgradable from: 3.30.6-2ubuntu10]
gnome-software/eoan-updates 3.30.6-2ubuntu10.19.10.0 amd64 [upgradable from: 3.30.6-2ubuntu10]
gnome-terminal-data/eoan-updates,eoan-updates 3.34.2-1ubuntu1 all [upgradable from: 3.34.0-1ubuntu2]
gnome-terminal/eoan-updates 3.34.2-1ubuntu1 amd64 [upgradable from: 3.34.0-1ubuntu2]
google-chrome-stable/stable 80.0.3987.132-1 amd64 [upgradable from: 80.0.3987.122-1]
grub-common/eoan-updates 2.04-1ubuntu12.1 amd64 [upgradable from: 2.04-1ubuntu12]
grub-efi-amd64-bin/eoan-updates 2.04-1ubuntu12.1 amd64 [upgradable from: 2.04-1ubuntu12]
grub-efi-amd64-signed/eoan-updates 1.128.1+2.04-1ubuntu12.1 amd64 [upgradable from: 1.128+2.04-1ubuntu12]
grub-pc-bin/eoan-updates 2.04-1ubuntu12.1 amd64 [upgradable from: 2.04-1ubuntu12]
grub-pc/eoan-updates 2.04-1ubuntu12.1 amd64 [upgradable from: 2.04-1ubuntu12]
grub2-common/eoan-updates 2.04-1ubuntu12.1 amd64 [upgradable from: 2.04-1ubuntu12]
gzip/eoan-updates 1.10-0ubuntu3.1 amd64 [upgradable from: 1.10-0ubuntu3]
intel-microcode/eoan-updates,eoan-security 3.20191115.1ubuntu0.19.10.2 amd64 [upgradable from: 3.20190918.1ubuntu1]
klibc-utils/eoan-updates 2.0.6-1ubuntu3 amd64 [upgradable from: 2.0.6-1ubuntu1]
libarchive13/eoan-updates,eoan-security 3.4.0-1ubuntu0.1 amd64 [upgradable from: 3.4.0-1]
libaspell15/eoan-updates,eoan-security 0.60.7-3ubuntu0.1 amd64 [upgradable from: 0.60.7-3]
libbind9-161/eoan-updates,eoan-security 1:9.11.5.P4+dfsg-5.1ubuntu2.1 amd64 [upgradable from: 1:9.11.5.P4+dfsg-5.1ubuntu2]
libbinutils/eoan-updates,eoan-security 2.33-2ubuntu1.2 amd64 [upgradable from: 2.33-2ubuntu1]
libblkid1/eoan-updates 2.34-0.1ubuntu2.2 amd64 [upgradable from: 2.34-0.1ubuntu2]
libbluetooth3/eoan-updates 5.50-0ubuntu5 amd64 [upgradable from: 5.50-0ubuntu4]
libc-bin/eoan-updates 2.30-0ubuntu2.1 amd64 [upgradable from: 2.30-0ubuntu2]
libc-dev-bin/eoan-updates 2.30-0ubuntu2.1 amd64 [upgradable from: 2.30-0ubuntu2]
libc6-dbg/eoan-updates 2.30-0ubuntu2.1 amd64 [upgradable from: 2.30-0ubuntu2]
libc6-dev/eoan-updates 2.30-0ubuntu2.1 amd64 [upgradable from: 2.30-0ubuntu2]
libc6/eoan-updates 2.30-0ubuntu2.1 amd64 [upgradable from: 2.30-0ubuntu2]
libcom-err2/eoan-updates,eoan-security 1.45.3-4ubuntu2.1 amd64 [upgradable from: 1.45.3-4ubuntu2]
libdjvulibre-text/eoan-updates,eoan-updates,eoan-security,eoan-security 3.5.27.1-13ubuntu0.1 all [upgradable from: 3.5.27.1-13]
libdjvulibre21/eoan-updates,eoan-security 3.5.27.1-13ubuntu0.1 amd64 [upgradable from: 3.5.27.1-13]
libdns-export1104/eoan-updates,eoan-security 1:9.11.5.P4+dfsg-5.1ubuntu2.1 amd64 [upgradable from: 1:9.11.5.P4+dfsg-5.1ubuntu2]
libdns1104/eoan-updates,eoan-security 1:9.11.5.P4+dfsg-5.1ubuntu2.1 amd64 [upgradable from: 1:9.11.5.P4+dfsg-5.1ubuntu2]
libegl-mesa0/eoan-updates 19.2.8-0ubuntu0~19.10.3 amd64 [upgradable from: 19.2.1-1ubuntu1]
libegl1-mesa/eoan-updates 19.2.8-0ubuntu0~19.10.3 amd64 [upgradable from: 19.2.1-1ubuntu1]
libexif12/eoan-updates,eoan-security 0.6.21-5.1ubuntu0.1 amd64 [upgradable from: 0.6.21-5.1]
libexiv2-14/eoan-updates,eoan-security 0.25-4ubuntu2.2 amd64 [upgradable from: 0.25-4ubuntu2]
libext2fs2/eoan-updates,eoan-security 1.45.3-4ubuntu2.1 amd64 [upgradable from: 1.45.3-4ubuntu2]
libfdisk1/eoan-updates 2.34-0.1ubuntu2.2 amd64 [upgradable from: 2.34-0.1ubuntu2]
libfribidi0/eoan-updates,eoan-security 1.0.5-3.1ubuntu0.19.10.1 amd64 [upgradable from: 1.0.5-3.1]
libfwupd2/eoan-updates 1.2.10-1ubuntu4 amd64 [upgradable from: 1.2.10-1ubuntu2]
libgbm1/eoan-updates 19.2.8-0ubuntu0~19.10.3 amd64 [upgradable from: 19.2.1-1ubuntu1]
libgcrypt20/eoan-updates,eoan-security 1.8.4-5ubuntu2.1 amd64 [upgradable from: 1.8.4-5ubuntu2]
libgl1-mesa-dri/eoan-updates 19.2.8-0ubuntu0~19.10.3 amd64 [upgradable from: 19.2.1-1ubuntu1]
libglapi-mesa/eoan-updates 19.2.8-0ubuntu0~19.10.3 amd64 [upgradable from: 19.2.1-1ubuntu1]
libglx-mesa0/eoan-updates 19.2.8-0ubuntu0~19.10.3 amd64 [upgradable from: 19.2.1-1ubuntu1]
libgnome-desktop-3-18/eoan-updates 3.34.2-2ubuntu1~19.10.1 amd64 [upgradable from: 3.34.1-1ubuntu1]
libgs9-common/eoan-updates,eoan-updates,eoan-security,eoan-security 9.27~dfsg+0-0ubuntu3.1 all [upgradable from: 9.27~dfsg+0-0ubuntu3]
libgs9/eoan-updates,eoan-security 9.27~dfsg+0-0ubuntu3.1 amd64 [upgradable from: 9.27~dfsg+0-0ubuntu3]
libirs161/eoan-updates,eoan-security 1:9.11.5.P4+dfsg-5.1ubuntu2.1 amd64 [upgradable from: 1:9.11.5.P4+dfsg-5.1ubuntu2]
libisc-export1100/eoan-updates,eoan-security 1:9.11.5.P4+dfsg-5.1ubuntu2.1 amd64 [upgradable from: 1:9.11.5.P4+dfsg-5.1ubuntu2]
libisc1100/eoan-updates,eoan-security 1:9.11.5.P4+dfsg-5.1ubuntu2.1 amd64 [upgradable from: 1:9.11.5.P4+dfsg-5.1ubuntu2]
libisccc161/eoan-updates,eoan-security 1:9.11.5.P4+dfsg-5.1ubuntu2.1 amd64 [upgradable from: 1:9.11.5.P4+dfsg-5.1ubuntu2]
libisccfg163/eoan-updates,eoan-security 1:9.11.5.P4+dfsg-5.1ubuntu2.1 amd64 [upgradable from: 1:9.11.5.P4+dfsg-5.1ubuntu2]
libjavascriptcoregtk-4.0-18/eoan-updates,eoan-security 2.26.4-0ubuntu0.19.10.1 amd64 [upgradable from: 2.26.1-3]
libklibc/eoan-updates 2.0.6-1ubuntu3 amd64 [upgradable from: 2.0.6-1ubuntu1]
liblwres161/eoan-updates,eoan-security 1:9.11.5.P4+dfsg-5.1ubuntu2.1 amd64 [upgradable from: 1:9.11.5.P4+dfsg-5.1ubuntu2]
libmagic-mgc/eoan-updates,eoan-security 1:5.37-5ubuntu0.1 amd64 [upgradable from: 1:5.37-5]
libmagic1/eoan-updates,eoan-security 1:5.37-5ubuntu0.1 amd64 [upgradable from: 1:5.37-5]
libmount1/eoan-updates 2.34-0.1ubuntu2.2 amd64 [upgradable from: 2.34-0.1ubuntu2]
libmutter-5-0/eoan-updates 3.34.1+git20191107-1ubuntu1~19.10.1 amd64 [upgradable from: 3.34.1-1ubuntu1]
libmysqlclient21/eoan-updates,eoan-security 8.0.19-0ubuntu0.19.10.3 amd64 [upgradable from: 8.0.17-0ubuntu2]
libnm0/eoan-updates 1.20.4-2ubuntu2.2 amd64 [upgradable from: 1.20.4-2ubuntu2]
libnss-systemd/eoan-updates 242-7ubuntu3.7 amd64 [upgradable from: 242-7ubuntu3]
libnss3/eoan-updates,eoan-security 2:3.45-1ubuntu2.2 amd64 [upgradable from: 2:3.45-1ubuntu2]
libpam-modules-bin/eoan-updates 1.3.1-5ubuntu1.19.10.1 amd64 [upgradable from: 1.3.1-5ubuntu1]
libpam-modules/eoan-updates 1.3.1-5ubuntu1.19.10.1 amd64 [upgradable from: 1.3.1-5ubuntu1]
libpam-runtime/eoan-updates,eoan-updates 1.3.1-5ubuntu1.19.10.1 all [upgradable from: 1.3.1-5ubuntu1]
libpam-systemd/eoan-updates 242-7ubuntu3.7 amd64 [upgradable from: 242-7ubuntu3]
libpam0g/eoan-updates 1.3.1-5ubuntu1.19.10.1 amd64 [upgradable from: 1.3.1-5ubuntu1]
libplymouth4/eoan-updates 0.9.4git20190712-0ubuntu4.1 amd64 [upgradable from: 0.9.4git20190712-0ubuntu4]
libpoppler-cpp0v5/eoan-updates 0.80.0-0ubuntu1.1 amd64 [upgradable from: 0.80.0-0ubuntu1]
libpoppler-glib8/eoan-updates 0.80.0-0ubuntu1.1 amd64 [upgradable from: 0.80.0-0ubuntu1]
libpoppler90/eoan-updates 0.80.0-0ubuntu1.1 amd64 [upgradable from: 0.80.0-0ubuntu1]
libpulse-mainloop-glib0/eoan-updates 1:13.0-1ubuntu1.1 amd64 [upgradable from: 1:13.0-1ubuntu1]
libpulse0/eoan-updates 1:13.0-1ubuntu1.1 amd64 [upgradable from: 1:13.0-1ubuntu1]
libpulsedsp/eoan-updates 1:13.0-1ubuntu1.1 amd64 [upgradable from: 1:13.0-1ubuntu1]
libpython3.7-minimal/eoan-updates 3.7.5-2~19.10 amd64 [upgradable from: 3.7.5~rc1-2]
libpython3.7-stdlib/eoan-updates 3.7.5-2~19.10 amd64 [upgradable from: 3.7.5~rc1-2]
libpython3.7/eoan-updates 3.7.5-2~19.10 amd64 [upgradable from: 3.7.5~rc1-2]
libreoffice-base-core/eoan-updates 1:6.3.4-0ubuntu0.19.10.1 amd64 [upgradable from: 1:6.3.2-0ubuntu2]
libreoffice-calc/eoan-updates 1:6.3.4-0ubuntu0.19.10.1 amd64 [upgradable from: 1:6.3.2-0ubuntu2]
libreoffice-common/eoan-updates,eoan-updates 1:6.3.4-0ubuntu0.19.10.1 all [upgradable from: 1:6.3.2-0ubuntu2]
libreoffice-core/eoan-updates 1:6.3.4-0ubuntu0.19.10.1 amd64 [upgradable from: 1:6.3.2-0ubuntu2]
libreoffice-draw/eoan-updates 1:6.3.4-0ubuntu0.19.10.1 amd64 [upgradable from: 1:6.3.2-0ubuntu2]
libreoffice-gnome/eoan-updates 1:6.3.4-0ubuntu0.19.10.1 amd64 [upgradable from: 1:6.3.2-0ubuntu2]
libreoffice-gtk3/eoan-updates 1:6.3.4-0ubuntu0.19.10.1 amd64 [upgradable from: 1:6.3.2-0ubuntu2]
libreoffice-help-common/eoan-updates,eoan-updates 1:6.3.4-0ubuntu0.19.10.1 all [upgradable from: 1:6.3.2-0ubuntu2]
libreoffice-help-en-us/eoan-updates,eoan-updates 1:6.3.4-0ubuntu0.19.10.1 all [upgradable from: 1:6.3.2-0ubuntu2]
libreoffice-impress/eoan-updates 1:6.3.4-0ubuntu0.19.10.1 amd64 [upgradable from: 1:6.3.2-0ubuntu2]
libreoffice-math/eoan-updates 1:6.3.4-0ubuntu0.19.10.1 amd64 [upgradable from: 1:6.3.2-0ubuntu2]
libreoffice-ogltrans/eoan-updates,eoan-updates 1:6.3.4-0ubuntu0.19.10.1 all [upgradable from: 1:6.3.2-0ubuntu2]
libreoffice-pdfimport/eoan-updates,eoan-updates 1:6.3.4-0ubuntu0.19.10.1 all [upgradable from: 1:6.3.2-0ubuntu2]
libreoffice-style-breeze/eoan-updates,eoan-updates 1:6.3.4-0ubuntu0.19.10.1 all [upgradable from: 1:6.3.2-0ubuntu2]
libreoffice-style-colibre/eoan-updates,eoan-updates 1:6.3.4-0ubuntu0.19.10.1 all [upgradable from: 1:6.3.2-0ubuntu2]
libreoffice-style-elementary/eoan-updates,eoan-updates 1:6.3.4-0ubuntu0.19.10.1 all [upgradable from: 1:6.3.2-0ubuntu2]
libreoffice-style-tango/eoan-updates,eoan-updates 1:6.3.4-0ubuntu0.19.10.1 all [upgradable from: 1:6.3.2-0ubuntu2]
libreoffice-writer/eoan-updates 1:6.3.4-0ubuntu0.19.10.1 amd64 [upgradable from: 1:6.3.2-0ubuntu2]
librygel-core-2.6-2/eoan-updates,eoan-security 0.38.1-2ubuntu3.3 amd64 [upgradable from: 0.38.1-2ubuntu3]
librygel-db-2.6-2/eoan-updates,eoan-security 0.38.1-2ubuntu3.3 amd64 [upgradable from: 0.38.1-2ubuntu3]
librygel-renderer-2.6-2/eoan-updates,eoan-security 0.38.1-2ubuntu3.3 amd64 [upgradable from: 0.38.1-2ubuntu3]
librygel-server-2.6-2/eoan-updates,eoan-security 0.38.1-2ubuntu3.3 amd64 [upgradable from: 0.38.1-2ubuntu3]
libsasl2-2/eoan-updates,eoan-security 2.1.27+dfsg-1ubuntu0.1 amd64 [upgradable from: 2.1.27+dfsg-1build3]
libsasl2-modules-db/eoan-updates,eoan-security 2.1.27+dfsg-1ubuntu0.1 amd64 [upgradable from: 2.1.27+dfsg-1build3]
libsasl2-modules/eoan-updates,eoan-security 2.1.27+dfsg-1ubuntu0.1 amd64 [upgradable from: 2.1.27+dfsg-1build3]
libsmartcols1/eoan-updates 2.34-0.1ubuntu2.2 amd64 [upgradable from: 2.34-0.1ubuntu2]
libsmbclient/eoan-updates,eoan-security 2:4.10.7+dfsg-0ubuntu2.4 amd64 [upgradable from: 2:4.10.7+dfsg-0ubuntu2]
libsnapd-glib1/eoan-updates 1.49-0ubuntu1.19.10.0 amd64 [upgradable from: 1.49-0ubuntu1]
libsqlite3-0/eoan-updates,eoan-security 3.29.0-2ubuntu0.1 amd64 [upgradable from: 3.29.0-2]
libss2/eoan-updates,eoan-security 1.45.3-4ubuntu2.1 amd64 [upgradable from: 1.45.3-4ubuntu2]
libssh-4/eoan-updates,eoan-security 0.9.0-1ubuntu1.3 amd64 [upgradable from: 0.9.0-1ubuntu1]
libsystemd0/eoan-updates 242-7ubuntu3.7 amd64 [upgradable from: 242-7ubuntu3]
libudev1/eoan-updates 242-7ubuntu3.7 amd64 [upgradable from: 242-7ubuntu3]
libuuid1/eoan-updates 2.34-0.1ubuntu2.2 amd64 [upgradable from: 2.34-0.1ubuntu2]
libwbclient0/eoan-updates,eoan-security 2:4.10.7+dfsg-0ubuntu2.4 amd64 [upgradable from: 2:4.10.7+dfsg-0ubuntu2]
libwebkit2gtk-4.0-37/eoan-updates,eoan-security 2.26.4-0ubuntu0.19.10.1 amd64 [upgradable from: 2.26.1-3]
libwhoopsie0/eoan-updates,eoan-security 0.2.66ubuntu0.3 amd64 [upgradable from: 0.2.66]
libxatracker2/eoan-updates 19.2.8-0ubuntu0~19.10.3 amd64 [upgradable from: 19.2.1-1ubuntu1]
libxml2/eoan-updates,eoan-security 2.9.4+dfsg1-7ubuntu3.1 amd64 [upgradable from: 2.9.4+dfsg1-7ubuntu3]
libxslt1.1/eoan-updates,eoan-security 1.1.33-0ubuntu1.1 amd64 [upgradable from: 1.1.33-0ubuntu1]
linux-firmware/eoan-updates,eoan-updates 1.183.4 all [upgradable from: 1.183]
linux-generic/eoan-updates,eoan-security 5.3.0.40.34 amd64 [upgradable from: 5.3.0.18.21]
linux-headers-generic/eoan-updates,eoan-security 5.3.0.40.34 amd64 [upgradable from: 5.3.0.18.21]
linux-image-generic/eoan-updates,eoan-security 5.3.0.40.34 amd64 [upgradable from: 5.3.0.18.21]
linux-libc-dev/eoan-updates,eoan-security 5.3.0-40.32 amd64 [upgradable from: 5.3.0-18.19]
linux-signed-generic/eoan-updates,eoan-security 5.3.0.40.34 amd64 [upgradable from: 5.3.0.18.21]
locales/eoan-updates,eoan-updates 2.30-0ubuntu2.1 all [upgradable from: 2.30-0ubuntu2]
logsave/eoan-updates,eoan-security 1.45.3-4ubuntu2.1 amd64 [upgradable from: 1.45.3-4ubuntu2]
mesa-vulkan-drivers/eoan-updates 19.2.8-0ubuntu0~19.10.3 amd64 [upgradable from: 19.2.1-1ubuntu1]
mount/eoan-updates 2.34-0.1ubuntu2.2 amd64 [upgradable from: 2.34-0.1ubuntu2]
mutter-common/eoan-updates,eoan-updates 3.34.1+git20191107-1ubuntu1~19.10.1 all [upgradable from: 3.34.1-1ubuntu1]
mutter/eoan-updates 3.34.1+git20191107-1ubuntu1~19.10.1 amd64 [upgradable from: 3.34.1-1ubuntu1]
nautilus-extension-gnome-terminal/eoan-updates 3.34.2-1ubuntu1 amd64 [upgradable from: 3.34.0-1ubuntu2]
network-manager-config-connectivity-ubuntu/eoan-updates,eoan-updates 1.20.4-2ubuntu2.2 all [upgradable from: 1.20.4-2ubuntu2]
network-manager/eoan-updates 1.20.4-2ubuntu2.2 amd64 [upgradable from: 1.20.4-2ubuntu2]
plymouth-label/eoan-updates 0.9.4git20190712-0ubuntu4.1 amd64 [upgradable from: 0.9.4git20190712-0ubuntu4]
plymouth-theme-ubuntu-logo/eoan-updates 0.9.4git20190712-0ubuntu4.1 amd64 [upgradable from: 0.9.4git20190712-0ubuntu4]
plymouth-theme-ubuntu-text/eoan-updates 0.9.4git20190712-0ubuntu4.1 amd64 [upgradable from: 0.9.4git20190712-0ubuntu4]
plymouth/eoan-updates 0.9.4git20190712-0ubuntu4.1 amd64 [upgradable from: 0.9.4git20190712-0ubuntu4]
poppler-utils/eoan-updates 0.80.0-0ubuntu1.1 amd64 [upgradable from: 0.80.0-0ubuntu1]
ppp/eoan-updates,eoan-security 2.4.7-2+4.1ubuntu4.1 amd64 [upgradable from: 2.4.7-2+4.1ubuntu4]
pulseaudio-module-bluetooth/eoan-updates 1:13.0-1ubuntu1.1 amd64 [upgradable from: 1:13.0-1ubuntu1]
pulseaudio-utils/eoan-updates 1:13.0-1ubuntu1.1 amd64 [upgradable from: 1:13.0-1ubuntu1]
pulseaudio/eoan-updates 1:13.0-1ubuntu1.1 amd64 [upgradable from: 1:13.0-1ubuntu1]
python-apt-common/eoan-updates,eoan-updates,eoan-security,eoan-security 1.9.0ubuntu1.3 all [upgradable from: 1.9.0ubuntu1]
python3-apport/eoan-updates,eoan-updates 2.20.11-0ubuntu8.5 all [upgradable from: 2.20.11-0ubuntu8]
python3-apt/eoan-updates,eoan-security 1.9.0ubuntu1.3 amd64 [upgradable from: 1.9.0ubuntu1]
python3-aptdaemon.gtk3widgets/eoan-updates,eoan-updates,eoan-security,eoan-security 1.1.1+bzr982-0ubuntu28.1 all [upgradable from: 1.1.1+bzr982-0ubuntu28]
python3-aptdaemon/eoan-updates,eoan-updates,eoan-security,eoan-security 1.1.1+bzr982-0ubuntu28.1 all [upgradable from: 1.1.1+bzr982-0ubuntu28]
python3-distupgrade/eoan-updates,eoan-updates 1:19.10.15.4 all [upgradable from: 1:19.10.15]
python3-gdbm/eoan-updates 3.7.5-1build1 amd64 [upgradable from: 3.7.5~rc1-1]
python3-lib2to3/eoan-updates,eoan-updates 3.7.5-1build1 all [upgradable from: 3.7.5~rc1-1]
python3-pil/eoan-updates,eoan-security 6.1.0-1ubuntu0.2 amd64 [upgradable from: 6.1.0-1]
python3-problem-report/eoan-updates,eoan-updates 2.20.11-0ubuntu8.5 all [upgradable from: 2.20.11-0ubuntu8]
python3-renderpm/eoan-updates,eoan-security 3.5.23-1ubuntu0.1 amd64 [upgradable from: 3.5.23-1]
python3-reportlab-accel/eoan-updates,eoan-security 3.5.23-1ubuntu0.1 amd64 [upgradable from: 3.5.23-1]
python3-reportlab/eoan-updates,eoan-updates,eoan-security,eoan-security 3.5.23-1ubuntu0.1 all [upgradable from: 3.5.23-1]
python3-uno/eoan-updates 1:6.3.4-0ubuntu0.19.10.1 amd64 [upgradable from: 1:6.3.2-0ubuntu2]
python3.7-minimal/eoan-updates 3.7.5-2~19.10 amd64 [upgradable from: 3.7.5~rc1-2]
python3.7/eoan-updates 3.7.5-2~19.10 amd64 [upgradable from: 3.7.5~rc1-2]
rfkill/eoan-updates 2.34-0.1ubuntu2.2 amd64 [upgradable from: 2.34-0.1ubuntu2]
rygel/eoan-updates,eoan-security 0.38.1-2ubuntu3.3 amd64 [upgradable from: 0.38.1-2ubuntu3]
samba-libs/eoan-updates,eoan-security 2:4.10.7+dfsg-0ubuntu2.4 amd64 [upgradable from: 2:4.10.7+dfsg-0ubuntu2]
sudo/eoan-updates,eoan-security 1.8.27-1ubuntu4.1 amd64 [upgradable from: 1.8.27-1ubuntu4]
systemd-sysv/eoan-updates 242-7ubuntu3.7 amd64 [upgradable from: 242-7ubuntu3]
systemd/eoan-updates 242-7ubuntu3.7 amd64 [upgradable from: 242-7ubuntu3]
ubuntu-desktop-minimal/eoan-updates 1.440.1 amd64 [upgradable from: 1.440]
ubuntu-desktop/eoan-updates 1.440.1 amd64 [upgradable from: 1.440]
ubuntu-drivers-common/eoan-updates 1:0.7.6.0.1 amd64 [upgradable from: 1:0.7.6]
ubuntu-minimal/eoan-updates 1.440.1 amd64 [upgradable from: 1.440]
ubuntu-release-upgrader-core/eoan-updates,eoan-updates 1:19.10.15.4 all [upgradable from: 1:19.10.15]
ubuntu-release-upgrader-gtk/eoan-updates,eoan-updates 1:19.10.15.4 all [upgradable from: 1:19.10.15]
ubuntu-software/eoan-updates,eoan-updates 3.30.6-2ubuntu10.19.10.0 all [upgradable from: 3.30.6-2ubuntu10]
ubuntu-standard/eoan-updates 1.440.1 amd64 [upgradable from: 1.440]
udev/eoan-updates 242-7ubuntu3.7 amd64 [upgradable from: 242-7ubuntu3]
unattended-upgrades/eoan-updates,eoan-updates 1.14ubuntu1.2 all [upgradable from: 1.14ubuntu1]
uno-libs3/eoan-updates 6.3.4-0ubuntu0.19.10.1 amd64 [upgradable from: 6.3.2-0ubuntu2]
update-notifier-common/eoan-updates,eoan-updates 3.192.26.1 all [upgradable from: 3.192.26]
update-notifier/eoan-updates 3.192.26.1 amd64 [upgradable from: 3.192.26]
ure/eoan-updates 6.3.4-0ubuntu0.19.10.1 amd64 [upgradable from: 6.3.2-0ubuntu2]
util-linux/eoan-updates 2.34-0.1ubuntu2.2 amd64 [upgradable from: 2.34-0.1ubuntu2]
uuid-runtime/eoan-updates 2.34-0.1ubuntu2.2 amd64 [upgradable from: 2.34-0.1ubuntu2]
whoopsie/eoan-updates,eoan-security 0.2.66ubuntu0.3 amd64 [upgradable from: 0.2.66]
xdg-desktop-portal/eoan-updates 1.4.2-2ubuntu1 amd64 [upgradable from: 1.4.2-2]

```

Appreciate if anyone can help me troubleshoot this issue further?

I have also run the wireless-info script before and after, if some more information from that would be helpful...

---

### Post by chili555 on 2020-03-04
> linux-image-generic/eoan-updates,eoan-security 5.3.0.[COLOR="#FF0000"]40[/COLOR].34 amd64 Please reboot and interrupt the boot process to get to the GRUB menu. Boot into any earlier kernel version. Does your wireless now work again?

I think there is a bug.

---

### Post by nor-wanderer on 2020-03-04
> **chili555 said:**
> Please reboot and interrupt the boot process to get to the GRUB menu. Boot into any earlier kernel version. Does your wireless now work again?

I think there is a bug.

I can choose between **5.3.0-40-generic** and **5.3.0-18-generic**.

If I select 5.3.0-18-generic, WiFi actually works again! That's good to know. Many thanks!

That being said, is there any way to get it to work with 5.3.0-40-generic, or would I need to wait for the next kernel update?

Would I be able to expect my WiFi to work in Ubuntu 20.04, which I'm kind of waiting for? With 18.04 there were plenty more issues...

---

### Post by chili555 on 2020-03-04
Please check: [https://askubuntu.com/questions/1192531/wifi-adapter-not-found-for-dell-inspiron-5590-processor-is-i5-10th-gen-10210u/1193493#comment2038719_1193493](https://askubuntu.com/questions/1192531/wifi-adapter-not-found-for-dell-inspiron-5590-processor-is-i5-10th-gen-10210u/1193493#comment2038719_1193493)

Please see the last three comments.

---

### Post by nor-wanderer on 2020-03-05
Many thanks. I've added a comment, and will keep an eye on this bug: [https://bugs.launchpad.net/hwe-next/+bug/1833065](https://bugs.launchpad.net/hwe-next/+bug/1833065)

---

### Post by nor-wanderer on 2020-04-03
For the record, I can confirm that this issue persists also with both 5.3.0-**42**-generic and 5.3.0-**45**-generic.

---

### Post by Yellow Pasque on 2020-04-03
> **nor-wanderer said:**
> Many thanks. I've added a comment, and will keep an eye on this bug: [https://bugs.launchpad.net/hwe-next/+bug/1833065](https://bugs.launchpad.net/hwe-next/+bug/1833065)

I believe that is a different bug, although the last few comments seem to describe your problem. This is probably the one you (and others) want where the -40 kernel broke iwlwifi:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1863769](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1863769)

---

### Post by fyfe54 on 2020-04-04
5.6 and 5.6.1 kernels also broke iwlwifi.  FIXED in 5.6.2

---

### Post by jebradley on 2020-04-04
I have had the same problems with the 19.04 to 19.10 upgrade with a hardwired network card. The solution that I found to at least get the internet working (but not network-manager) is to use the command, 'sudo dhclient enp3s0&#8217; which is for an ethernet card. You might try 'sudo dhclient wlp2s0' which would be for a wifi device. I still haven't solved why network-manager doesn't work.

---

### Post by chili555 on 2020-04-05
> **jebradley said:**
> I have had the same problems with the 19.04 to 19.10 upgrade with a hardwired network card. The solution that I found to at least get the internet working (but not network-manager) is to use the command, 'sudo dhclient enp3s0’ which is for an ethernet card. You might try 'sudo dhclient wlp2s0' which would be for a wifi device. I still haven't solved why network-manager doesn't work.
the command 'dhclient' offers no option to specify which of several wireless access points (SSID) you wish to connect to nor does it offer the option to supply the WPA2 password. It will therefore be ineffective.

---

### Post by nor-wanderer on 2020-04-11
I'm still a bit new to Ubuntu, but plan to update to Unbuntu 20.04, which I see will be released soon. It appears it will be released with kernel 5.4.

Does anyone know if I should expect this issue as well with that kernel? If so, should I refrain from updating to Ubuntu 20.04?

---

### Post by Yellow Pasque on 2020-04-11
Try a LiveUSB before updating.

---

### Post by citesoleil20 on 2020-04-11
I think that it's broken.I was posting this before readind this thread:

After the clean install (of Ubuntu 20.04), everything worked perfect. I downloaded some files, used internet, all was OK. But after the first reboot the Wi-Fi just doesn't work at all.
The Wi-Fi card is an RTL8723AE .
The point is: It was already working fine, why it all went wrong with a reboot? If it was working properly at first, what could be happening now?

---

### Post by wildmanne39 on 2020-04-11
Hello and welcome to the forum citesoleil20, please start your own thread instead of posting in someone else's because even if the issue seems the same most of the time the cause is different and it gets confusing help more then one person in a thread.

In your new thread include the results from the wireless script in my signature and please tell everyone what files you downloaded when your wifi stop working and did you install the driver manually or did it come installed in ubuntu?

---

### Post by nor-wanderer on 2020-04-25
I performed a clean upgrade to and installation of Ubuntu 20.04 today, and can confirm that WiFi is working as intended then. Kernel: 5.4.0-26-generic

---

