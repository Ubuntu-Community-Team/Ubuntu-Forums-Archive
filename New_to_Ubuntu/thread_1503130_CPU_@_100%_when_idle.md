---
title: "CPU @ 100% when idle"
date: 2010-06-06
forum: New to Ubuntu
---

### Post by hnarwan on 2010-06-06
Hi All,

I have a Toshiba Tecra laptop, dual core 2.66 GHz.

The system seems to run fine but when I check system monitor I see one of the CPU's is running at 100%.

When I check running processes in terminal via the 'top' command I see the process taking 100 is 'background'.

I'm not doing anything that would mean the cpu should be that high, i've rebooted but the same thing happens again. 

Top command results are below.

PID USER  PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
1853 root 20   0  8048 4328 2048 R  100  0.1 609:17.82 backend

---

### Post by hnarwan on 2010-06-06
Sorry so the 'backend' process seems to be the culprit. As it's a dual core one of the CPU's is affected, running at 100%, the other one seems ok.

Any ideas would be great.

---

### Post by NightwishFan on 2010-06-06
Could you post the output of top here, surrounded by CODE tags. The button looks like -> #.

---

### Post by hnarwan on 2010-06-06
I've copied and pasted the whole thing. Not sure if this is what you meant?

top - 18:30:20 up 10:37,  2 users,  load average: 1.23, 1.17, 1.21
Tasks: 164 total,   3 running, 161 sleeping,   0 stopped,   0 zombie
Cpu(s): 44.8%us,  5.5%sy,  0.0%ni, 49.4%id,  0.0%wa,  0.0%hi,  0.3%si,  0.0%st
Mem:   2961024k total,  2638308k used,   322716k free,    95208k buffers
Swap:  8674296k total,        0k used,  8674296k free,  2220112k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 1853 root      20   0  8048 4328 2048 R  100  0.1 626:15.30 backend            
 1112 root      20   0 92624  26m  11m S    1  0.9   5:31.20 Xorg               
 6481 hardeep   20   0  102m  24m 7888 S    1  0.8   0:00.80 compiz             
 6611 hardeep   20   0 47040  12m 9952 S    0  0.4   0:00.12 gnome-terminal     
 6630 hardeep   20   0  2544 1228  924 R    0  0.0   0:00.01 top                
    1 root      20   0  2800 1652 1200 S    0  0.1   0:00.59 init               
    2 root      20   0     0    0    0 S    0  0.0   0:00.00 kthreadd           
    3 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/0        
    4 root      20   0     0    0    0 S    0  0.0   0:00.21 ksoftirqd/0        
    5 root      RT   0     0    0    0 S    0  0.0   0:00.00 watchdog/0         
    6 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/1        
    7 root      20   0     0    0    0 S    0  0.0   0:00.42 ksoftirqd/1        
    8 root      RT   0     0    0    0 S    0  0.0   0:00.00 watchdog/1         
    9 root      20   0     0    0    0 S    0  0.0   0:00.02 events/0           
   10 root      20   0     0    0    0 S    0  0.0   0:23.51 events/1           
   11 root      20   0     0    0    0 S    0  0.0   0:00.00 cpuset             
   12 root      20   0     0    0    0 S    0  0.0   0:00.00 khelper

---

### Post by sdennie on 2010-06-06
There is no "backend" process installed by default on 10.04 so, it must be something you've installed.  Try:

```

dpkg -S `which backend`

```

And report back.

---

### Post by hnarwan on 2010-06-06
I seem to be screwing something up with that command:


hardeep@hardeep-laptop:~$ dpkg -S `which backend`
dpkg-query: --search needs at least one file name pattern argument

Use --help for help about querying packages;
Use --license for copyright licence and lack of warranty (GNU GPL).
hardeep@hardeep-laptop:~$ ^C
hardeep@hardeep-laptop:~$

---

### Post by sdennie on 2010-06-06
> **hnarwan said:**
> I seem to be screwing something up with that command:


hardeep@hardeep-laptop:~$ dpkg -S `which backend`
dpkg-query: --search needs at least one file name pattern argument

Use --help for help about querying packages;
Use --license for copyright licence and lack of warranty (GNU GPL).
hardeep@hardeep-laptop:~$ ^C
hardeep@hardeep-laptop:~$

No, that's useful information.  Now try:

```

locate backend

```

If it only comes back with 1 result, try:

```

dpkg -S `locate backend`

```

---

### Post by hnarwan on 2010-06-06
Thanks sdennie, 

I get a bunch of results from that 'locate backend' command.

Not sure what's causing this, I havent done much on Ubuntu. Installed Jdownloader, Google Chrome, Kvpnc (to remote into my work computers over cisco vpn) and that's about it if memory serves. 

Does the output below point to anything for you?


hardeep@hardeep-laptop:~$ locate backend
/etc/polkit-1/nullbackend.conf.d
/etc/polkit-1/nullbackend.conf.d/50-nullbackend.conf
/usr/lib/libebackend-1.2.so.0
/usr/lib/libebackend-1.2.so.0.0.1
/usr/lib/libkwalletbackend.so.4
/usr/lib/libkwalletbackend.so.4.4.0
/usr/lib/libpolkit-backend-1.so.0
/usr/lib/libpolkit-backend-1.so.0.0.0
/usr/lib/compizconfig/backends
/usr/lib/compizconfig/backends/libgconf.a
/usr/lib/compizconfig/backends/libgconf.la
/usr/lib/compizconfig/backends/libgconf.so
/usr/lib/compizconfig/backends/libini.so
/usr/lib/cups/backend
/usr/lib/cups/backend-available
/usr/lib/cups/backend/beh
/usr/lib/cups/backend/bluetooth
/usr/lib/cups/backend/dnssd
/usr/lib/cups/backend/hp
/usr/lib/cups/backend/hpfax
/usr/lib/cups/backend/http
/usr/lib/cups/backend/ipp
/usr/lib/cups/backend/lpd
/usr/lib/cups/backend/parallel
/usr/lib/cups/backend/scsi
/usr/lib/cups/backend/serial
/usr/lib/cups/backend/smb
/usr/lib/cups/backend/snmp
/usr/lib/cups/backend/socket
/usr/lib/cups/backend/usb
/usr/lib/cups/backend-available/dnssd
/usr/lib/cups/backend-available/http
/usr/lib/cups/backend-available/ipp
/usr/lib/cups/backend-available/lpd
/usr/lib/cups/backend-available/mdns
/usr/lib/cups/backend-available/parallel
/usr/lib/cups/backend-available/scsi
/usr/lib/cups/backend-available/serial
/usr/lib/cups/backend-available/snmp
/usr/lib/cups/backend-available/socket
/usr/lib/cups/backend-available/usb
/usr/lib/erlang/lib/runtime_tools-1.8.2/ebin/observer_backend.beam
/usr/lib/evince/2/backends
/usr/lib/evince/2/backends/comicsdocument.evince-backend
/usr/lib/evince/2/backends/djvudocument.evince-backend
/usr/lib/evince/2/backends/dvidocument.evince-backend
/usr/lib/evince/2/backends/impressdocument.evince-backend
/usr/lib/evince/2/backends/libcomicsdocument.so
/usr/lib/evince/2/backends/libdjvudocument.so
/usr/lib/evince/2/backends/libdvidocument.so
/usr/lib/evince/2/backends/libimpressdocument.so
/usr/lib/evince/2/backends/libpdfdocument.so
/usr/lib/evince/2/backends/libpixbufdocument.so
/usr/lib/evince/2/backends/libpsdocument.so
/usr/lib/evince/2/backends/libtiffdocument.so
/usr/lib/evince/2/backends/pdfdocument.evince-backend
/usr/lib/evince/2/backends/pixbufdocument.evince-backend
/usr/lib/evince/2/backends/psdocument.evince-backend
/usr/lib/evince/2/backends/tiffdocument.evince-backend
/usr/lib/evolution-data-server-1.2/extensions/libebookbackendfile.so
/usr/lib/evolution-data-server-1.2/extensions/libebookbackendgoogle.so
/usr/lib/evolution-data-server-1.2/extensions/libebookbackendgroupwise.so
/usr/lib/evolution-data-server-1.2/extensions/libebookbackendldap.so
/usr/lib/evolution-data-server-1.2/extensions/libebookbackendvcf.so
/usr/lib/evolution-data-server-1.2/extensions/libebookbackendwebdav.so
/usr/lib/evolution-data-server-1.2/extensions/libecalbackendcaldav.so
/usr/lib/evolution-data-server-1.2/extensions/libecalbackendcontacts.so
/usr/lib/evolution-data-server-1.2/extensions/libecalbackendfile.so
/usr/lib/evolution-data-server-1.2/extensions/libecalbackendgoogle.so
/usr/lib/evolution-data-server-1.2/extensions/libecalbackendgroupwise.so
/usr/lib/evolution-data-server-1.2/extensions/libecalbackendhttp.so
/usr/lib/evolution-data-server-1.2/extensions/libecalbackendweather.so
/usr/lib/gtk-2.0/2.10.0/printbackends
/usr/lib/gtk-2.0/2.10.0/printbackends/libprintbackend-cups.so
/usr/lib/gtk-2.0/2.10.0/printbackends/libprintbackend-file.so
/usr/lib/gtk-2.0/2.10.0/printbackends/libprintbackend-lpr.so
/usr/lib/gtk-2.0/2.10.0/printbackends/libprintbackend-test.so
/usr/lib/kde4/plugins/kauth/backend
/usr/lib/kde4/plugins/kauth/backend/kauth_backend_plugin.so
/usr/lib/libgconf2-4/2/libgconfbackend-evoldap.so
/usr/lib/libgconf2-4/2/libgconfbackend-oldxml.so
/usr/lib/libgconf2-4/2/libgconfbackend-xml.so
/usr/lib/polkit-1/extensions/libnullbackend.so
/usr/lib/python2.6/dist-packages/UpdateManager/backend
/usr/lib/python2.6/dist-packages/UpdateManager/backend/InstallBackend.py
/usr/lib/python2.6/dist-packages/UpdateManager/backend/InstallBackend.pyc
/usr/lib/python2.6/dist-packages/UpdateManager/backend/InstallBackendAptdaemon.py
/usr/lib/python2.6/dist-packages/UpdateManager/backend/InstallBackendAptdaemon.pyc
/usr/lib/python2.6/dist-packages/UpdateManager/backend/InstallBackendSynaptic.py
/usr/lib/python2.6/dist-packages/UpdateManager/backend/InstallBackendSynaptic.pyc
/usr/lib/python2.6/dist-packages/UpdateManager/backend/__init__.py
/usr/lib/python2.6/dist-packages/UpdateManager/backend/__init__.pyc
/usr/lib/python2.6/dist-packages/jockey/backend.py
/usr/lib/python2.6/dist-packages/jockey/backend.pyc
/usr/lib/python2.6/dist-packages/ufw/backend.py
/usr/lib/python2.6/dist-packages/ufw/backend.pyc
/usr/lib/python2.6/dist-packages/ufw/backend_iptables.py
/usr/lib/python2.6/dist-packages/ufw/backend_iptables.pyc
/usr/lib/python2.6/dist-packages/usbcreator/backends
/usr/lib/python2.6/dist-packages/usbcreator/backends/__init__.py
/usr/lib/python2.6/dist-packages/usbcreator/backends/__init__.pyc
/usr/lib/python2.6/dist-packages/usbcreator/backends/base
/usr/lib/python2.6/dist-packages/usbcreator/backends/udisks
/usr/lib/python2.6/dist-packages/usbcreator/backends/base/__init__.py
/usr/lib/python2.6/dist-packages/usbcreator/backends/base/__init__.pyc
/usr/lib/python2.6/dist-packages/usbcreator/backends/base/backend.py
/usr/lib/python2.6/dist-packages/usbcreator/backends/base/backend.pyc
/usr/lib/python2.6/dist-packages/usbcreator/backends/udisks/__init__.py
/usr/lib/python2.6/dist-packages/usbcreator/backends/udisks/__init__.pyc
/usr/lib/python2.6/dist-packages/usbcreator/backends/udisks/backend.py
/usr/lib/python2.6/dist-packages/usbcreator/backends/udisks/backend.pyc
/usr/lib/qt4/plugins/phonon_backend
/usr/lib/qt4/plugins/phonon_backend/phonon_xine.so
/usr/lib/soprano/libsoprano_redlandbackend.so
/usr/lib/soprano/libsoprano_virtuosobackend.so
/usr/lib/strigi/strigiindex_nepomukbackend.so
/usr/sbin/system-tools-backends
/usr/share/system-tools-backends-2.0
/usr/share/checkbox/backend
/usr/share/checkbox/plugins/backend_info.py
/usr/share/checkbox/plugins/backend_info.pyc
/usr/share/cups/doc-root/help/man-backend.html
/usr/share/doc/compizconfig-backend-gconf
/usr/share/doc/gvfs-backends
/usr/share/doc/libebackend1.2-0
/usr/share/doc/libpolkit-backend-1-0
/usr/share/doc/phonon-backend-xine
/usr/share/doc/system-tools-backends
/usr/share/doc/compizconfig-backend-gconf/AUTHORS
/usr/share/doc/compizconfig-backend-gconf/changelog.Debian.gz
/usr/share/doc/compizconfig-backend-gconf/copyright
/usr/share/doc/gvfs-backends/AUTHORS
/usr/share/doc/gvfs-backends/NEWS.gz
/usr/share/doc/gvfs-backends/README
/usr/share/doc/gvfs-backends/TODO
/usr/share/doc/gvfs-backends/changelog.Debian.gz
/usr/share/doc/gvfs-backends/copyright
/usr/share/doc/libebackend1.2-0/NEWS.gz
/usr/share/doc/libebackend1.2-0/TODO
/usr/share/doc/libebackend1.2-0/changelog.Debian.gz
/usr/share/doc/libebackend1.2-0/copyright
/usr/share/doc/libpolkit-backend-1-0/NEWS.gz
/usr/share/doc/libpolkit-backend-1-0/changelog.Debian.gz
/usr/share/doc/libpolkit-backend-1-0/copyright
/usr/share/doc/phonon-backend-xine/changelog.Debian.gz
/usr/share/doc/phonon-backend-xine/copyright
/usr/share/doc/system-tools-backends/AUTHORS
/usr/share/doc/system-tools-backends/NEWS.gz
/usr/share/doc/system-tools-backends/README
/usr/share/doc/system-tools-backends/changelog.Debian.gz
/usr/share/doc/system-tools-backends/copyright
/usr/share/jockey/jockey-backend
/usr/share/kde4/services/phononbackends
/usr/share/kde4/services/phononbackends/xine.desktop
/usr/share/kde4/servicetypes/kconfigbackend.desktop
/usr/share/kde4/servicetypes/phononbackend.desktop
/usr/share/lintian/overrides/libebackend1.2-0
/usr/share/locale-langpack/en_AU/LC_MESSAGES/system-tools-backends.mo
/usr/share/locale-langpack/en_CA/LC_MESSAGES/system-tools-backends.mo
/usr/share/locale-langpack/en_GB/LC_MESSAGES/sane-backends.mo
/usr/share/locale-langpack/en_GB/LC_MESSAGES/system-tools-backends.mo
/usr/share/man/de/man7/backend.7.gz
/usr/share/man/fr/man7/backend.7.gz
/usr/share/man/man1/system-tools-backends.1.gz
/usr/share/man/man7/backend.7.gz
/usr/share/pyshared/UpdateManager/backend
/usr/share/pyshared/UpdateManager/backend/InstallBackend.py
/usr/share/pyshared/UpdateManager/backend/InstallBackendAptdaemon.py
/usr/share/pyshared/UpdateManager/backend/InstallBackendSynaptic.py
/usr/share/pyshared/UpdateManager/backend/__init__.py
/usr/share/pyshared/jockey/backend.py
/usr/share/pyshared/ufw/backend.py
/usr/share/pyshared/ufw/backend_iptables.py
/usr/share/pyshared/usbcreator/backends
/usr/share/pyshared/usbcreator/backends/__init__.py
/usr/share/pyshared/usbcreator/backends/base
/usr/share/pyshared/usbcreator/backends/udisks
/usr/share/pyshared/usbcreator/backends/base/__init__.py
/usr/share/pyshared/usbcreator/backends/base/backend.py
/usr/share/pyshared/usbcreator/backends/udisks/__init__.py
/usr/share/pyshared/usbcreator/backends/udisks/backend.py
/usr/share/software-center/softwarecenter/backend
/usr/share/software-center/softwarecenter/backend/__init__.py
/usr/share/software-center/softwarecenter/backend/__init__.pyc
/usr/share/software-center/softwarecenter/backend/aptd.py
/usr/share/software-center/softwarecenter/backend/aptd.pyc
/usr/share/software-center/softwarecenter/backend/channel.py
/usr/share/software-center/softwarecenter/backend/channel.pyc
/usr/share/software-center/softwarecenter/backend/config.py
/usr/share/software-center/softwarecenter/backend/config.pyc
/usr/share/software-center/softwarecenter/backend/paths.py
/usr/share/software-center/softwarecenter/backend/paths.pyc
/usr/share/software-center/softwarecenter/backend/transactionswatcher.py
/usr/share/software-center/softwarecenter/backend/transactionswatcher.pyc
/usr/share/soprano/plugins/redlandbackend.desktop
/usr/share/soprano/plugins/virtuosobackend.desktop
/usr/share/system-tools-backends-2.0/files
/usr/share/system-tools-backends-2.0/scripts
/usr/share/system-tools-backends-2.0/files/general_gprs_chatscript
/usr/share/system-tools-backends-2.0/files/general_isdn_ppp_options
/usr/share/system-tools-backends-2.0/files/general_pppoe_ppp_options
/usr/share/system-tools-backends-2.0/scripts/GroupConfig.pm
/usr/share/system-tools-backends-2.0/scripts/GroupsConfig.pm
/usr/share/system-tools-backends-2.0/scripts/HostsConfig.pm
/usr/share/system-tools-backends-2.0/scripts/IfacesConfig.pm
/usr/share/system-tools-backends-2.0/scripts/Init
/usr/share/system-tools-backends-2.0/scripts/NFSConfig.pm
/usr/share/system-tools-backends-2.0/scripts/NTPConfig.pm
/usr/share/system-tools-backends-2.0/scripts/Network
/usr/share/system-tools-backends-2.0/scripts/Platform.pm
/usr/share/system-tools-backends-2.0/scripts/SMBConfig.pm
/usr/share/system-tools-backends-2.0/scripts/SelfConfig.pm
/usr/share/system-tools-backends-2.0/scripts/ServiceConfig.pm
/usr/share/system-tools-backends-2.0/scripts/ServicesConfig.pm
/usr/share/system-tools-backends-2.0/scripts/Shares
/usr/share/system-tools-backends-2.0/scripts/StbObject.pm
/usr/share/system-tools-backends-2.0/scripts/SystemToolsBackends.pl
/usr/share/system-tools-backends-2.0/scripts/Time
/usr/share/system-tools-backends-2.0/scripts/TimeConfig.pm
/usr/share/system-tools-backends-2.0/scripts/UserConfig.pm
/usr/share/system-tools-backends-2.0/scripts/Users
/usr/share/system-tools-backends-2.0/scripts/UsersConfig.pm
/usr/share/system-tools-backends-2.0/scripts/Utils
/usr/share/system-tools-backends-2.0/scripts/Init/Services.pm
/usr/share/system-tools-backends-2.0/scripts/Init/ServicesList.pm
/usr/share/system-tools-backends-2.0/scripts/Network/Hosts.pm
/usr/share/system-tools-backends-2.0/scripts/Network/Ifaces.pm
/usr/share/system-tools-backends-2.0/scripts/Shares/NFS.pm
/usr/share/system-tools-backends-2.0/scripts/Shares/SMB.pm
/usr/share/system-tools-backends-2.0/scripts/Time/NTP.pm
/usr/share/system-tools-backends-2.0/scripts/Time/TimeDate.pm
/usr/share/system-tools-backends-2.0/scripts/Users/Groups.pm
/usr/share/system-tools-backends-2.0/scripts/Users/Shells.pm
/usr/share/system-tools-backends-2.0/scripts/Users/Users.pm
/usr/share/system-tools-backends-2.0/scripts/Utils/Backend.pm
/usr/share/system-tools-backends-2.0/scripts/Utils/DBus.pm
/usr/share/system-tools-backends-2.0/scripts/Utils/File.pm
/usr/share/system-tools-backends-2.0/scripts/Utils/Monitor.pm
/usr/share/system-tools-backends-2.0/scripts/Utils/Parse.pm
/usr/share/system-tools-backends-2.0/scripts/Utils/Platform.pm
/usr/share/system-tools-backends-2.0/scripts/Utils/Replace.pm
/usr/share/system-tools-backends-2.0/scripts/Utils/Report.pm
/usr/share/system-tools-backends-2.0/scripts/Utils/Util.pm
/usr/share/system-tools-backends-2.0/scripts/Utils/XML.pm
/usr/src/linux-headers-2.6.32-22/arch/alpha/include/asm/agp_backend.h
/usr/src/linux-headers-2.6.32-22/include/linux/agp_backend.h
/usr/src/linux-headers-2.6.32-22/include/linux/fsnotify_backend.h
/usr/src/linux-headers-2.6.32-22-generic/include/linux/agp_backend.h
/usr/src/linux-headers-2.6.32-22-generic/include/linux/fsnotify_backend.h
/var/cache/apt/archives/gvfs-backends_1.6.1-0ubuntu1build1_i386.deb
/var/cache/apt/archives/packagekit-backend-apt_0.5.7-0ubuntu2_i386.deb
/var/cache/apt/archives/phonon-backend-xine_4%3a4.4.0-0ubuntu2_i386.deb
/var/lib/dpkg/info/compizconfig-backend-gconf.list
/var/lib/dpkg/info/compizconfig-backend-gconf.md5sums
/var/lib/dpkg/info/gvfs-backends.list
/var/lib/dpkg/info/gvfs-backends.md5sums
/var/lib/dpkg/info/gvfs-backends.postinst
/var/lib/dpkg/info/libebackend1.2-0.list
/var/lib/dpkg/info/libebackend1.2-0.md5sums
/var/lib/dpkg/info/libebackend1.2-0.postinst
/var/lib/dpkg/info/libebackend1.2-0.postrm
/var/lib/dpkg/info/libebackend1.2-0.shlibs
/var/lib/dpkg/info/libpolkit-backend-1-0.list
/var/lib/dpkg/info/libpolkit-backend-1-0.md5sums
/var/lib/dpkg/info/libpolkit-backend-1-0.postinst
/var/lib/dpkg/info/libpolkit-backend-1-0.postrm
/var/lib/dpkg/info/libpolkit-backend-1-0.shlibs
/var/lib/dpkg/info/libpolkit-backend-1-0.symbols
/var/lib/dpkg/info/packagekit-backend-apt.list
/var/lib/dpkg/info/packagekit-backend-apt.postrm
/var/lib/dpkg/info/phonon-backend-xine.list
/var/lib/dpkg/info/phonon-backend-xine.md5sums
/var/lib/dpkg/info/system-tools-backends.conffiles
/var/lib/dpkg/info/system-tools-backends.list
/var/lib/dpkg/info/system-tools-backends.md5sums
/var/lib/dpkg/info/system-tools-backends.postrm
/var/lib/dpkg/info/system-tools-backends.preinst
hardeep@hardeep-laptop:~$

---

### Post by hnarwan on 2010-06-06
[IMG]file:///home/hardeep/Desktop/Screenshot.png[/IMG]

Hoping i've managed to copy a screenshot of system monitor showing the problem.

---

### Post by hnarwan on 2010-06-06
Guess not!

---

### Post by NightwishFan on 2010-06-06
Top tells us anything the sysmon would, but if you want to post it, scroll below when you are posting, and push "Manage Attachments".

---

### Post by sdennie on 2010-06-06
That output narrowed it down but, the output of this would be useful:

```

cat /proc/`pgrep backend`/cmdline

```

---

### Post by hnarwan on 2010-06-06
I installed htop, and tried to kill the high cpu process, not sure if that did it or the restart but it looks like it's back to normal. this seems to be a bug in Ubuntu, been reported by multiple users where 'backend' is taking 100, those could be from different apps but certainly something ubuntu should deal with better. 

anyway i'll keep an eye on things and make sure I start shutting down my laptop at night in case it comes back and starts a fire in my house!

---

### Post by Wragie on 2010-07-19
I've just run across this thread and wondering if the exact cause is known. I have a Tecra A8 1.66 dual core, one is running 0-2% and the other 92-100% and its running hot as result. This is one a fresh clean install of ubuntu 10.4. This is a dual boot with xp pro with ubunto on its own partition etc. 
I've got 4gb of ram and only seeing 3.2 as well. 

I used to run a slack box a few ice ages ago so I'm still in catch up mode ie I know it can do this but....;)

I've managed to get everything else sorted out on this but these heat and load issues. They are not present when booting into xp.

Any hints at what or where to look?

Dave

---

