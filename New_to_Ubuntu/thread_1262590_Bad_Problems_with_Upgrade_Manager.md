---
title: "Bad Problems with Upgrade Manager"
date: 2009-09-10
forum: New to Ubuntu
---

### Post by evil_urna on 2009-09-10
I fought and fought but I finally got ubuntu to reinstall. And now it gives me this. What exactly is failing? And is there anyway to fix this? 

```
scott@Scott-Desktop:~$ sudo apt-get upgrade
[sudo] password for scott: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  bluez-cups bluez-gstreamer bluez-utils brasero checkbox checkbox-gtk compiz
  compiz-core compiz-gnome compiz-plugins compiz-wrapper
  compizconfig-backend-gconf consolekit cups cups-bsd cups-client cups-common
  ekiga evince evolution evolution-common evolution-data-server
  evolution-data-server-common evolution-documentation-en evolution-exchange
  evolution-plugins gnome-about gnome-desktop-data gnome-settings-daemon
  gnome-system-tools gnome-terminal gnome-terminal-data gvfs gvfs-backends
  gvfs-bin gvfs-fuse hal language-selector language-selector-common
  libbrasero-media0 libcamel1.2-14 libck-connector0 libdecoration0
  libebackend1.2-0 libebook1.2-9 libecal1.2-7 libedata-book1.2-2
  libedata-cal1.2-6 libedataserver1.2-11 libedataserverui1.2-8
  libegroupwise1.2-13 libevdocument1 libevview1 libexchange-storage1.2-3
  libgdata-google1.2-1 libgdata1.2-1 libgvfscommon0 libhal-storage1 libical0
  libmetacity0 libnautilus-extension1 libpam-ck-connector libpoppler-glib4
  libpoppler4 libsmbclient libtrackerclient0 libudev0 libwbclient0
  libxcb-render0 linux-generic linux-headers-generic linux-image-generic
  linux-libc-dev linux-restricted-modules-generic metacity metacity-common
  nautilus nautilus-data ntpdate openssl pidgin poppler-utils pulseaudio
  pulseaudio-esound-compat pulseaudio-module-gconf pulseaudio-module-hal
  pulseaudio-module-x11 pulseaudio-utils python-cupshelpers python-libxml2
  samba-common screen-profiles smbclient splix system-config-printer-common
  system-config-printer-gnome xserver-xorg-video-intel
97 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/49.2MB of archives.
After this operation, 782kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Extracting templates from packages: 100%
Preconfiguring packages ...
(Reading database ... 121712 files and directories currently installed.)
Preparing to replace libpoppler4 0.10.5-1ubuntu2 (using .../libpoppler4_0.10.5-1ubuntu2.2_i386.deb) ...
Unpacking replacement libpoppler4 ...
Preparing to replace poppler-utils 0.10.5-1ubuntu2 (using .../poppler-utils_0.10.5-1ubuntu2.2_i386.deb) ...
Unpacking replacement poppler-utils ...
Preparing to replace cups-common 1.3.9-17ubuntu3.1 (using .../cups-common_1.3.9-17ubuntu3.2_all.deb) ...
Unpacking replacement cups-common ...
Preparing to replace cups 1.3.9-17ubuntu3.1 (using .../cups_1.3.9-17ubuntu3.2_i386.deb) ...
 * Stopping Common Unix Printing System: cupsd                           [ OK ] 
Unpacking replacement cups ...
Preparing to replace bluez-cups 4.32-0ubuntu4 (using .../bluez-cups_4.32-0ubuntu4.1_i386.deb) ...
Unpacking replacement bluez-cups ...
Preparing to replace bluez-gstreamer 4.32-0ubuntu4 (using .../bluez-gstreamer_4.32-0ubuntu4.1_i386.deb) ...
Unpacking replacement bluez-gstreamer ...
Preparing to replace bluez-utils 4.32-0ubuntu4 (using .../bluez-utils_4.32-0ubuntu4.1_all.deb) ...
Unpacking replacement bluez-utils ...
Preparing to replace libnautilus-extension1 1:2.26.2-0ubuntu1 (using .../libnautilus-extension1_1%3a2.26.2-0ubuntu2_i386.deb) ...
Unpacking replacement libnautilus-extension1 ...
Preparing to replace libbrasero-media0 2.26.0-0ubuntu3 (using .../libbrasero-media0_2.26.1-0ubuntu1_i386.deb) ...
Unpacking replacement libbrasero-media0 ...
Preparing to replace brasero 2.26.0-0ubuntu3 (using .../brasero_2.26.1-0ubuntu1_i386.deb) ...
Unpacking replacement brasero ...
Preparing to replace libhal-storage1 0.5.12~rc1+git20090403-0ubuntu1 (using .../libhal-storage1_0.5.12~rc1+git20090403-0ubuntu4_i386.deb) ...
Unpacking replacement libhal-storage1 ...
Preparing to replace libck-connector0 0.3.0-2ubuntu3 (using .../libck-connector0_0.3.0-2ubuntu4_i386.deb) ...
Unpacking replacement libck-connector0 ...
Preparing to replace consolekit 0.3.0-2ubuntu3 (using .../consolekit_0.3.0-2ubuntu4_i386.deb) ...
Unpacking replacement consolekit ...
Preparing to replace hal 0.5.12~rc1+git20090403-0ubuntu1 (using .../hal_0.5.12~rc1+git20090403-0ubuntu4_i386.deb) ...
 * Stopping Hardware abstraction layer hald                              [ OK ] 
Unpacking replacement hal ...
Preparing to replace checkbox 0.7.1 (using .../checkbox_0.7.2_all.deb) ...
Unpacking replacement checkbox ...
Preparing to replace checkbox-gtk 0.7.1 (using .../checkbox-gtk_0.7.2_all.deb) ...
Unpacking replacement checkbox-gtk ...
Preparing to replace libdecoration0 1:0.8.2-0ubuntu8 (using .../libdecoration0_1%3a0.8.2-0ubuntu8.1_i386.deb) ...
Unpacking replacement libdecoration0 ...
Preparing to replace metacity-common 1:2.25.144-0ubuntu2 (using .../metacity-common_1%3a2.25.144-0ubuntu2.1_all.deb) ...
Unpacking replacement metacity-common ...
Preparing to replace libmetacity0 1:2.25.144-0ubuntu2 (using .../libmetacity0_1%3a2.25.144-0ubuntu2.1_i386.deb) ...
Unpacking replacement libmetacity0 ...
Preparing to replace compizconfig-backend-gconf 0.8.2-0ubuntu1 (using .../compizconfig-backend-gconf_0.8.2-0ubuntu2_i386.deb) ...
Unpacking replacement compizconfig-backend-gconf ...
Preparing to replace compiz-gnome 1:0.8.2-0ubuntu8 (using .../compiz-gnome_1%3a0.8.2-0ubuntu8.1_i386.deb) ...
Unpacking replacement compiz-gnome ...
dpkg: ../../src/filesdb.c:581: findnamenode: Assertion `(*pointerp)->name[0] == '/'' failed.
dpkg-deb: subprocess paste killed by signal (Broken pipe)
E: Sub-process /usr/bin/dpkg exited unexpectedly
scott@Scott-Desktop:~$ 

```


Thanks in advance for any help.

---

### Post by Michael.Godawski on 2009-09-10
What happens if you run:
```
sudo dpkg -configure -a
```

---

### Post by evil_urna on 2009-09-10
> **Michael.Godawski said:**
> What happens if you run:
```
sudo dpkg -configure -a
```

```
scott@Scott-Desktop:~$ sudo dpkg --configure -a
Processing triggers for shared-mime-info ...
*** glibc detected *** update-mime-database.real: corrupted double-linked list: 0x086260d8 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb7d17009]
/lib/tls/i686/cmov/libc.so.6[0xb7d18b8d]
/lib/tls/i686/cmov/libc.so.6(__libc_malloc+0x95)[0xb7d1a9c5]
/usr/lib/libxml2.so.2(xmlDictCreate+0x71)[0xb7fc12c1]
/usr/lib/libxml2.so.2(xmlInitParserCtxt+0x2d3)[0xb7ee7923]
/usr/lib/libxml2.so.2(xmlNewParserCtxt+0x42)[0xb7ee7ba2]
/usr/lib/libxml2.so.2(xmlCreateURLParserCtxt+0x22)[0xb7eea1a2]
/usr/lib/libxml2.so.2(xmlCreateFileParserCtxt+0x19)[0xb7eea279]
/usr/lib/libxml2.so.2(xmlSAXParseFileWithData+0x26)[0xb7f01f56]
/usr/lib/libxml2.so.2(xmlSAXParseFile+0x27)[0xb7f02057]
/usr/lib/libxml2.so.2(xmlParseFile+0x21)[0xb7f020b1]
update-mime-database.real[0x804d518]
update-mime-database.real[0x804e725]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5)[0xb7cbd775]
update-mime-database.real[0x8049ce1]
======= Memory map: ========
08048000-08052000 r-xp 00000000 08:01 692054     /usr/bin/update-mime-database.real
08052000-08053000 r--p 00009000 08:01 692054     /usr/bin/update-mime-database.real
08053000-08054000 rw-p 0000a000 08:01 692054     /usr/bin/update-mime-database.real
08079000-09075000 rw-p 08079000 00:00 0          [heap]
b7b00000-b7b21000 rw-p b7b00000 00:00 0 
b7b21000-b7c00000 ---p b7b21000 00:00 0 
b7c24000-b7c31000 r-xp 00000000 08:01 819213     /lib/libgcc_s.so.1
b7c31000-b7c32000 r--p 0000c000 08:01 819213     /lib/libgcc_s.so.1
b7c32000-b7c33000 rw-p 0000d000 08:01 819213     /lib/libgcc_s.so.1
b7c33000-b7c34000 rw-p b7c33000 00:00 0 
b7c34000-b7c64000 r-xp 00000000 08:01 819272     /lib/libpcre.so.3.12.1
b7c64000-b7c65000 r--p 0002f000 08:01 819272     /lib/libpcre.so.3.12.1
b7c65000-b7c66000 rw-p 00030000 08:01 819272     /lib/libpcre.so.3.12.1
b7c66000-b7c67000 rw-p b7c66000 00:00 0 
b7c67000-b7c8b000 r-xp 00000000 08:01 819363     /lib/tls/i686/cmov/libm-2.9.so
b7c8b000-b7c8c000 r--p 00023000 08:01 819363     /lib/tls/i686/cmov/libm-2.9.so
b7c8c000-b7c8d000 rw-p 00024000 08:01 819363     /lib/tls/i686/cmov/libm-2.9.so
b7c8d000-b7ca1000 r-xp 00000000 08:01 819339     /lib/libz.so.1.2.3.3
b7ca1000-b7ca2000 r--p 00013000 08:01 819339     /lib/libz.so.1.2.3.3
b7ca2000-b7ca3000 rw-p 00014000 08:01 819339     /lib/libz.so.1.2.3.3
b7ca3000-b7ca5000 r-xp 00000000 08:01 819362     /lib/tls/i686/cmov/libdl-2.9.so
b7ca5000-b7ca6000 r--p 00001000 08:01 819362     /lib/tls/i686/cmov/libdl-2.9.so
b7ca6000-b7ca7000 rw-p 00002000 08:01 819362     /lib/tls/i686/cmov/libdl-2.9.so
b7ca7000-b7e03000 r-xp 00000000 08:01 819359     /lib/tls/i686/cmov/libc-2.9.so
b7e03000-b7e04000 ---p 0015c000 08:01 819359     /lib/tls/i686/cmov/libc-2.9.so
b7e04000-b7e06000 r--p 0015c000 08:01 819359     /lib/tls/i686/cmov/libc-2.9.so
b7e06000-b7e07000 rw-p 0015e000 08:01 819359     /lib/tls/i686/cmov/libc-2.9.so
b7e07000-b7e0a000 rw-p b7e07000 00:00 0 
b7e0a000-b7ec0000 r-xp 00000000 08:01 691940     /usr/lib/libglib-2.0.so.0.2000.1
b7ec0000-b7ec1000 r--p 000b5000 08:01 691940     /usr/lib/libglib-2.0.so.0.2000.1
b7ec1000-b7ec2000 rw-p 000b6000 08:01 691940     /usr/lib/libglib-2.0.so.0.2000.1
b7ec2000-b7ff7000 r-xp 00000000 08:01 689430     /usr/lib/libxml2.so.2.6.32
b7ff7000-b7ff8000 ---p 00135000 08:01 689430     /usr/lib/libxml2.so.2.6.32
b7ff8000-b7ffc000 r--p 00135000 08:01 689430     /usr/lib/libxml2.so.2.6.32
b7ffc000-b7ffd000 rw-p 00139000 08:01 689430     /usr/lib/libxml2.so.2.6.32
b7ffd000-b7fff000 rw-p b7ffd000 00:00 0 
b800d000-b800e000 rw-p b800d000 00:00 0 
b800e000-b800f000 r-xp b800e000 00:00 0          [vdso]
b800f000-b802b000 r-xp 00000000 08:01 819214     /lib/ld-2.9.so
b802b000-b802c000 r--p 0001b000 08:01 819214     /lib/ld-2.9.so
b802c000-b802d000 rw-p 0001c000 08:01 819214     /lib/ld-2.9.so
bf818000-bf82d000 rw-p bffeb000 00:00 0          [stack]
Aborted
dpkg: error processing shared-mime-info (--configure):
 subprocess post-installation script returned error exit status 134
Processing triggers for man-db ...
Setting up libhal-storage1 (0.5.12~rc1+git20090403-0ubuntu4) ...

Processing triggers for doc-base ...
Processing 1 changed doc-base file(s)...
Registering documents with scrollkeeper...
Setting up libdecoration0 (1:0.8.2-0ubuntu8.1) ...

Setting up libck-connector0 (0.3.0-2ubuntu4) ...

Setting up bluez-gstreamer (4.32-0ubuntu4.1) ...
Setting up metacity-common (1:2.25.144-0ubuntu2.1) ...
Segmentation fault
dpkg: error processing metacity-common (--configure):
 subprocess post-installation script returned error exit status 139
Setting up cups-common (1.3.9-17ubuntu3.2) ...
dpkg: dependency problems prevent configuration of libmetacity0:
 libmetacity0 depends on metacity-common (>= 1:2.25); however:
  Package metacity-common is not configured yet.
 libmetacity0 depends on metacity-common (<< 1:2.26); however:
  Package metacity-common is not configured yet.
dpkg: error processing libmetacity0 (--configure):
 dependency problems - leaving unconfigured
Setting up consolekit (0.3.0-2ubuntu4) ...
Setting up libpoppler4 (0.10.5-1ubuntu2.2) ...

Processing triggers for ufw ...
Setting up poppler-utils (0.10.5-1ubuntu2.2) ...
Setting up libnautilus-extension1 (1:2.26.2-0ubuntu2) ...

Setting up bluez-utils (4.32-0ubuntu4.1) ...
Setting up compizconfig-backend-gconf (0.8.2-0ubuntu2) ...
Setting up cups (1.3.9-17ubuntu3.2) ...
 * Reloading AppArmor profiles ...                                       [ OK ] 
 * Starting Common Unix Printing System: cupsd                           [ OK ] 

Setting up hal (0.5.12~rc1+git20090403-0ubuntu4) ...
 * Reloading system message bus config...                                [ OK ] 
 * Starting Hardware abstraction layer hald                                     /usr/sbin/hald already running.
                                                                         [ OK ]

Setting up checkbox (0.7.2) ...

Setting up bluez-cups (4.32-0ubuntu4.1) ...
Setting up checkbox-gtk (0.7.2) ...

Setting up libbrasero-media0 (2.26.1-0ubuntu1) ...

Setting up brasero (2.26.1-0ubuntu1) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 shared-mime-info
 metacity-common
 libmetacity0

```

And it still triggers crash reports

---

### Post by evil_urna on 2009-09-10
oh lol.

Ok I did sudo apt-get upgrade in terminal after I killed gnome and it worked. What could have caused that?

---

### Post by evil_urna on 2009-09-10
I continued to have problems. I replaced my Motherboard and it worked

Thanks for all the help

---

