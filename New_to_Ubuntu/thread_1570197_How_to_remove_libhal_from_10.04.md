---
title: "How to remove libhal from 10.04?"
date: 2010-09-07
forum: New to Ubuntu
---

### Post by outleradam on 2010-09-07
I heard that package hal was being removed from 10.04 and replaced with devicekit

can someone explain to me why it's on my computer and how to remove it?

```
adam@adam-desktop:~$ uname -a
Linux adam-desktop 2.6.32-25-generic #43-Ubuntu SMP Wed Sep 1 09:46:13 UTC 2010 x86_64 GNU/Linux
adam@adam-desktop:~$ sudo apt-get remove libhal1
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libmono-addins-gui0.2-cil liblaunchpad-integration1.0-cil libiso9660-7 libcddb2 libgdict-1.0-6 libdvbpsi5 libbabl-0.0-0 libgegl-0.0-0 libsdl-image1.2 libupnp3 libmatroska0 libxcb-keysyms1
  libgimp2.0 indicator-session vlc-data libtar python-xlib gimp-data libvcdinfo0 libebml0
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  f-spot firefox-gnome-support gbrainy gdm gdm-guest-session gimp gnome-about gnome-applets gnome-mag gnome-orca gnome-panel gnome-pilot gnome-pilot-conduits gnome-power-manager gnome-session
  gnome-utils hdhomerun-config-gui indicator-applet indicator-applet-session indicator-me istanbul libbonoboui2-0 libgail-gnome-module libgnome-pilot2 libgnome-vfs2.0-cil libgnome2-0
  libgnome2-perl libgnome2-vfs-perl libgnome2.24-cil libgnomepanel2.24-cil libgnomeui-0 libgnomevfs2-0 libgnomevfs2-extra libhal-storage1 libhal1 libpanel-applet2-0 libvlc2 libvlccore2
  mousetweaks nautilus-share pnee python-gnome2 python-gnomeapplet python-pyatspi rhythmbox rhythmbox-plugin-cdrecorder rhythmbox-plugins rhythmbox-ubuntuone-music-store screenlets screenlets-doc
  system-config-printer-gnome tomboy tsclient ubuntu-desktop usb-creator-gtk vinagre vlc vlc-nox vlc-plugin-pulse
0 upgraded, 0 newly installed, 59 to remove and 0 not upgraded.
After this operation, 165MB disk space will be freed.
Do you want to continue [Y/n]? n
Abort.
adam@adam-desktop:~$ 


```I'm trying to get my mouse out of hal and into the newer methods.

---

### Post by andrewthomas on 2010-09-07
```
andrew@790Fx:~$ aptitude why hal
i   gnome-device-manager Depends hal
andrew@790Fx:~$ aptitude why gnome-device-manager
i   hal Suggests gnome-device-manager
andrew@790Fx:~$ aptitude why libhal1
i   libgnome-pilot2 Depends libhal1 (>= 0.5.8.1)
andrew@790Fx:~$ aptitude why libgnome-pilot2
i   libpisync1  Suggests gnome-pilot               
pi  gnome-pilot Depends  libgnome-pilot2 (>= 2.0.2)
andrew@790Fx:~$ aptitude why gnome-pilot
i   libpisync1 Suggests gnome-pilot
```so 
 ```
**sudo aptitude remove gnome-pilot gnome-device-manager hal**
```
if you like you could probably add libhal1 & libhal-storage1 to the list

---

### Post by outleradam on 2010-09-07
I can remove hal with no problem.  the problem is removing libhal1

Performing that action attempts to remove gnome and all it's children.

```
adam@adam-test-VM:~$ sudo aptitude why libhal-storage1
[sudo] password for adam: 
i   hal Depends libhal-storage1 (>= 0.5.11~rc2)
adam@adam-test-VM:~$ sudo aptitude why hal
i   pitivi Recommends hal
adam@adam-test-VM:~$ sudo aptitude remove pitivi
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
The following packages will be REMOVED:
  linux-headers-2.6.32-21{u} linux-headers-2.6.32-21-generic{u} pitivi 
0 packages upgraded, 0 newly installed, 3 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 88.2MB will be freed.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
(Reading database ... 145943 files and directories currently installed.)
Removing linux-headers-2.6.32-21-generic ...
Removing linux-headers-2.6.32-21 ...
Removing pitivi ...
Processing triggers for shared-mime-info ...
Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for hicolor-icon-theme ...
Processing triggers for python-support ...
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done

adam@adam-test-VM:~$ sudo aptitude remove hal
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
The following packages will be REMOVED:
  hal 
0 packages upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 1,692kB will be freed.
Writing extended state information... Done
(Reading database ... 127379 files and directories currently installed.)
Removing hal ...
Processing triggers for man-db ...
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done

adam@adam-test-VM:~$ sudo aptitude why libhal1
i   libhal-storage1 Depends libhal1 (>= 0.5.8.1)
adam@adam-test-VM:~$ sudo aptitude why libhal-storage1
i   libgnomevfs2-0 Depends libhal-storage1 (>= 0.5.8.1)
adam@adam-test-VM:~$ sudo aptitude why libgnomevfs2-0
i   firefox-gnome-support Depends libgnomevfs2-0 (>= 1:2.17.90)
adam@adam-test-VM:~$ sudo aptitude why firefox-gnome-support
i   ubuntu-desktop Recommends firefox-gnome-support
adam@adam-test-VM:~$ sudo aptitude remove hal libhal1 libhal-storage1 libgnomevfs2-0 firefox-gnome-support
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
The following packages are BROKEN:
  evolution evolution-couchdb evolution-exchange evolution-indicator 
  evolution-plugins libgnome-pilot2 libgnome-vfs2.0-cil libgnome2-0 
  libgnome2-perl libgnome2-vfs-perl libgnomeui-0 libgnomevfs2-extra 
  python-gnome2 python-gnomeapplet 
The following packages will be REMOVED:
  firefox-gnome-support libgnomevfs2-0 libhal-storage1 libhal1 
0 packages upgraded, 0 newly installed, 4 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 1,343kB will be freed.
The following packages have unmet dependencies:
  python-gnome2: Depends: libgnomevfs2-0 (>= 1:2.17.90) but it is not installable
  libgnome2-0: Depends: libgnomevfs2-0 (>= 1:2.17.90) but it is not installable
  evolution-indicator: Depends: libgnomevfs2-0 (>= 1:2.17.90) but it is not installable
  evolution-exchange: Depends: libgnomevfs2-0 (>= 1:2.17.90) but it is not installable
  evolution: Depends: libgnomevfs2-0 (>= 1:2.17.90) but it is not installable
  libgnome2-perl: Depends: libgnomevfs2-0 (>= 1:2.17.90) but it is not installable
  libgnome-pilot2: Depends: libgnomevfs2-0 (>= 1:2.17.90) but it is not installable
                   Depends: libhal1 (>= 0.5.8.1) but it is not installable
  libgnome2-vfs-perl: Depends: libgnomevfs2-0 (>= 1:2.17.90) but it is not installable
  libgnomeui-0: Depends: libgnomevfs2-0 (>= 1:2.17.90) but it is not installable
  python-gnomeapplet: Depends: libgnomevfs2-0 (>= 1:2.17.90) but it is not installable
  evolution-plugins: Depends: libgnomevfs2-0 (>= 1:2.17.90) but it is not installable
  libgnomevfs2-extra: Depends: libgnomevfs2-0 (>= 1:2.17.90) but it is not installable
  libgnome-vfs2.0-cil: Depends: libgnomevfs2-0 (>= 1:2.17.90) but it is not installable
  evolution-couchdb: Depends: libgnomevfs2-0 (>= 1:2.17.90) but it is not installable
The following actions will resolve these dependencies:

Remove the following packages:
evolution
evolution-couchdb
evolution-exchange
evolution-indicator
evolution-plugins
f-spot
gbrainy
gdm
gdm-guest-session
gnome-about
gnome-applets
gnome-mag
gnome-orca
gnome-panel
gnome-power-manager
gnome-session
gnome-utils
indicator-applet
indicator-applet-session
indicator-me
libbonoboui2-0
libgail-gnome-module
libgnome-pilot2
libgnome-vfs2.0-cil
libgnome2-0
libgnome2-perl
libgnome2-vfs-perl
libgnome2.24-cil
libgnomepanel2.24-cil
libgnomeui-0
libgnomevfs2-extra
liblpint-bonobo0
libpanel-applet2-0
mousetweaks
nautilus-share
python-gnome2
python-gnomeapplet
python-pyatspi
rhythmbox
rhythmbox-plugin-cdrecorder
rhythmbox-plugins
rhythmbox-ubuntuone-music-store
system-config-printer-gnome
tomboy
tsclient
ubuntu-desktop
usb-creator-gtk
vinagre

Leave the following dependencies unresolved:
alacarte recommends gnome-panel
apturl recommends libgnome2-perl
gdebi recommends libgnome2-perl
indicator-messages recommends indicator-applet | indicator-renderer
indicator-session recommends indicator-applet (>= 0.2) | indicator-renderer
metacity recommends gnome-session | x-session-manager
evolution-common recommends evolution
gedit recommends python-gnome2
gnome-control-center recommends gnome-session
gnome-control-center recommends mousetweaks
gnome-panel-data recommends gnome-panel
gnome-screensaver recommends gnome-power-manager | xfce4-power-manager
synaptic recommends libgnome2-perl
Score is 766

Accept this solution? [Y/n/q/?] Y
The following packages will be REMOVED:
  evolution{a} evolution-couchdb{a} evolution-exchange{a} 
  evolution-indicator{a} evolution-plugins{a} f-spot{a} 
  firefox-gnome-support gbrainy{a} gdm{a} gdm-guest-session{a} 
  gnome-about{a} gnome-applets{a} gnome-mag{a} gnome-orca{a} gnome-panel{a} 
  gnome-power-manager{a} gnome-session{a} gnome-utils{a} 
  indicator-applet{a} indicator-applet-session{a} indicator-me{a} 
  libbonoboui2-0{a} libgail-gnome-module{a} libgnome-pilot2{a} 
  libgnome-vfs2.0-cil{a} libgnome2-0{a} libgnome2-perl{a} 
  libgnome2-vfs-perl{a} libgnome2.24-cil{a} libgnomepanel2.24-cil{a} 
  libgnomeui-0{a} libgnomevfs2-0 libgnomevfs2-extra{a} libhal-storage1 
  libhal1 liblpint-bonobo0{a} libpanel-applet2-0{a} mousetweaks{a} 
  nautilus-share{a} python-gnome2{a} python-gnomeapplet{a} 
  python-pyatspi{a} rhythmbox{a} rhythmbox-plugin-cdrecorder{a} 
  rhythmbox-plugins{a} rhythmbox-ubuntuone-music-store{a} 
  system-config-printer-gnome{a} tomboy{a} tsclient{a} ubuntu-desktop{a} 
  usb-creator-gtk{a} vinagre{a} 
0 packages upgraded, 0 newly installed, 52 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 125MB will be freed.
Do you want to continue? [Y/n/?] Y
Writing extended state information... Done
(Reading database ... 127255 files and directories currently installed.)
Removing evolution-plugins ...
Removing evolution-indicator ...
Removing evolution-exchange ...
Removing evolution-couchdb ...
Removing evolution ...
Removing f-spot ...
Removing firefox-gnome-support ...
Removing gbrainy ...
Removing ubuntu-desktop ...
Removing gdm-guest-session ...
Removing gdm ...
Removing indicator-me ...
Removing indicator-applet-session ...
Removing indicator-applet ...
Removing gnome-session ...
Removing gnome-applets ...
Removing gnome-panel ...
Removing gnome-about ...
Removing gnome-mag ...
Removing gnome-orca ...
Removing gnome-power-manager ...
Removing gnome-utils ...
Removing vinagre ...
Removing tsclient ...
Removing python-gnomeapplet ...
Removing mousetweaks ...
Removing tomboy ...
Removing libgnomepanel2.24-cil ...
Removing libgnomepanel2.24-cil from Mono
Removing libgail-gnome-module ...
Removing libpanel-applet2-0 ...
Removing system-config-printer-gnome ...
Removing rhythmbox-ubuntuone-music-store ...
Removing rhythmbox-plugins ...
Removing rhythmbox-plugin-cdrecorder ...
Removing rhythmbox ...
Removing python-pyatspi ...
Removing usb-creator-gtk ...
Removing python-gnome2 ...
Removing liblpint-bonobo0 ...
Removing nautilus-share ...
Removing libgnome2.24-cil ...
Removing libgnome2.24-cil from Mono
Removing libgnome2-perl ...
Removing libgnome-pilot2 ...
Removing libgnomeui-0 ...
Removing libbonoboui2-0 ...
Removing libgnome-vfs2.0-cil ...
Removing libgnome-vfs2.0-cil from Mono
Removing libgnome2-0 ...
Removing libgnome2-vfs-perl ...
Removing libgnomevfs2-extra ...
Removing libgnomevfs2-0 ...
Removing libhal-storage1 ...
Removing libhal1 ...
Processing triggers for man-db ...
Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for hicolor-icon-theme ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Processing triggers for python-support ...
Processing triggers for shared-mime-info ...
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done

adam@adam-test-VM:~$ 
```Removing libhal1 removes everything.

```
adam@adam-test-VM:~$ sudo aptitude install ubuntu-desktop
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
The following NEW packages will be installed:
  evolution evolution-couchdb evolution-exchange evolution-indicator 
  evolution-plugins{a} f-spot firefox-gnome-support gbrainy gdm 
  gdm-guest-session gnome-about gnome-applets gnome-mag gnome-orca 
  gnome-panel{a} gnome-power-manager gnome-session{a} gnome-utils hal{a} 
  indicator-applet{a} indicator-applet-session indicator-me{a} 
  libbonoboui2-0{a} libgail-gnome-module libgnome-pilot2{a} 
  libgnome-vfs2.0-cil{a} libgnome2-0{a} libgnome2-perl 
  libgnome2-vfs-perl{a} libgnome2.24-cil{a} libgnomepanel2.24-cil{a} 
  libgnomeui-0{a} libgnomevfs2-0{a} libgnomevfs2-extra{a} 
  libhal-storage1{a} libhal1{a} liblpint-bonobo0{a} libpanel-applet2-0{a} 
  mousetweaks nautilus-share pitivi python-gnome2{a} python-gnomeapplet{a} 
  python-pyatspi{a} rhythmbox rhythmbox-plugin-cdrecorder{a} 
  rhythmbox-plugins{a} rhythmbox-ubuntuone-music-store 
  system-config-printer-gnome tomboy tsclient ubuntu-desktop 
  usb-creator-gtk vinagre 
0 packages upgraded, 54 newly installed, 0 to remove and 0 not upgraded.
Need to get 6,140kB/16.2MB of archives. After unpacking 129MB will be used.
Do you want to continue? [Y/n/?]
```
package ubuntu-desktop installs libhal1!   

What happened to HALsecotmy?  [https://wiki.ubuntu.com/Halsectomy](https://wiki.ubuntu.com/Halsectomy)

---

### Post by andrewthomas on 2010-09-07
I only have the ubuntu-minimal & ubuntu-standard metapackages installed. I would just have to remove gimp.
```
andrew@790Fx:~$ sudo aptitude remove gnome-pilot gnome-device-manager hal libhal-storage1 libhal1 libgnome-pilot2
The following packages will be REMOVED:  
  gnome-device-manager hal libgnome-device-manager0{u} libgnome-pilot2 libhal-storage1 libhal1 
0 packages upgraded, 0 newly installed, 6 to remove and 1 not upgraded.
Need to get 0B of archives. After unpacking 3,023kB will be freed.
The following packages have unmet dependencies:
  gimp: Depends: libhal1 (>= 0.5.8.1) but it is not going to be installed.
The following actions will resolve these dependencies:

     Remove the following packages:              
1)     gimp                                      

     Leave the following dependencies unresolved:
2)     gimp-data recommends gimp                 
3)     kdebase-runtime recommends hal            
4)     libgimp2.0 recommends gimp                


Accept this solution? [Y/n/q/?] 
```

---

### Post by sandyd on 2010-09-07
> **outleradam said:**
> I can remove hal with no problem.  the problem is removing libhal1

Performing that action attempts to remove gnome and all it's children.

```
adam@adam-test-VM:~$ sudo aptitude why libhal-storage1
[sudo] password for adam: 
i   hal Depends libhal-storage1 (>= 0.5.11~rc2)
adam@adam-test-VM:~$ sudo aptitude why hal
i   pitivi Recommends hal
adam@adam-test-VM:~$ sudo aptitude remove pitivi
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
The following packages will be REMOVED:
  linux-headers-2.6.32-21{u} linux-headers-2.6.32-21-generic{u} pitivi 
0 packages upgraded, 0 newly installed, 3 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 88.2MB will be freed.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
(Reading database ... 145943 files and directories currently installed.)
Removing linux-headers-2.6.32-21-generic ...
Removing linux-headers-2.6.32-21 ...
Removing pitivi ...
Processing triggers for shared-mime-info ...
Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for hicolor-icon-theme ...
Processing triggers for python-support ...
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done

adam@adam-test-VM:~$ sudo aptitude remove hal
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
The following packages will be REMOVED:
  hal 
0 packages upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 1,692kB will be freed.
Writing extended state information... Done
(Reading database ... 127379 files and directories currently installed.)
Removing hal ...
Processing triggers for man-db ...
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done

adam@adam-test-VM:~$ sudo aptitude why libhal1
i   libhal-storage1 Depends libhal1 (>= 0.5.8.1)
adam@adam-test-VM:~$ sudo aptitude why libhal-storage1
i   libgnomevfs2-0 Depends libhal-storage1 (>= 0.5.8.1)
adam@adam-test-VM:~$ sudo aptitude why libgnomevfs2-0
i   firefox-gnome-support Depends libgnomevfs2-0 (>= 1:2.17.90)
adam@adam-test-VM:~$ sudo aptitude why firefox-gnome-support
i   ubuntu-desktop Recommends firefox-gnome-support
adam@adam-test-VM:~$ sudo aptitude remove hal libhal1 libhal-storage1 libgnomevfs2-0 firefox-gnome-support
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
The following packages are BROKEN:
  evolution evolution-couchdb evolution-exchange evolution-indicator 
  evolution-plugins libgnome-pilot2 libgnome-vfs2.0-cil libgnome2-0 
  libgnome2-perl libgnome2-vfs-perl libgnomeui-0 libgnomevfs2-extra 
  python-gnome2 python-gnomeapplet 
The following packages will be REMOVED:
  firefox-gnome-support libgnomevfs2-0 libhal-storage1 libhal1 
0 packages upgraded, 0 newly installed, 4 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 1,343kB will be freed.
The following packages have unmet dependencies:
  python-gnome2: Depends: libgnomevfs2-0 (>= 1:2.17.90) but it is not installable
  libgnome2-0: Depends: libgnomevfs2-0 (>= 1:2.17.90) but it is not installable
  evolution-indicator: Depends: libgnomevfs2-0 (>= 1:2.17.90) but it is not installable
  evolution-exchange: Depends: libgnomevfs2-0 (>= 1:2.17.90) but it is not installable
  evolution: Depends: libgnomevfs2-0 (>= 1:2.17.90) but it is not installable
  libgnome2-perl: Depends: libgnomevfs2-0 (>= 1:2.17.90) but it is not installable
  libgnome-pilot2: Depends: libgnomevfs2-0 (>= 1:2.17.90) but it is not installable
                   Depends: libhal1 (>= 0.5.8.1) but it is not installable
  libgnome2-vfs-perl: Depends: libgnomevfs2-0 (>= 1:2.17.90) but it is not installable
  libgnomeui-0: Depends: libgnomevfs2-0 (>= 1:2.17.90) but it is not installable
  python-gnomeapplet: Depends: libgnomevfs2-0 (>= 1:2.17.90) but it is not installable
  evolution-plugins: Depends: libgnomevfs2-0 (>= 1:2.17.90) but it is not installable
  libgnomevfs2-extra: Depends: libgnomevfs2-0 (>= 1:2.17.90) but it is not installable
  libgnome-vfs2.0-cil: Depends: libgnomevfs2-0 (>= 1:2.17.90) but it is not installable
  evolution-couchdb: Depends: libgnomevfs2-0 (>= 1:2.17.90) but it is not installable
The following actions will resolve these dependencies:

Remove the following packages:
evolution
evolution-couchdb
evolution-exchange
evolution-indicator
evolution-plugins
f-spot
gbrainy
gdm
gdm-guest-session
gnome-about
gnome-applets
gnome-mag
gnome-orca
gnome-panel
gnome-power-manager
gnome-session
gnome-utils
indicator-applet
indicator-applet-session
indicator-me
libbonoboui2-0
libgail-gnome-module
libgnome-pilot2
libgnome-vfs2.0-cil
libgnome2-0
libgnome2-perl
libgnome2-vfs-perl
libgnome2.24-cil
libgnomepanel2.24-cil
libgnomeui-0
libgnomevfs2-extra
liblpint-bonobo0
libpanel-applet2-0
mousetweaks
nautilus-share
python-gnome2
python-gnomeapplet
python-pyatspi
rhythmbox
rhythmbox-plugin-cdrecorder
rhythmbox-plugins
rhythmbox-ubuntuone-music-store
system-config-printer-gnome
tomboy
tsclient
ubuntu-desktop
usb-creator-gtk
vinagre

Leave the following dependencies unresolved:
alacarte recommends gnome-panel
apturl recommends libgnome2-perl
gdebi recommends libgnome2-perl
indicator-messages recommends indicator-applet | indicator-renderer
indicator-session recommends indicator-applet (>= 0.2) | indicator-renderer
metacity recommends gnome-session | x-session-manager
evolution-common recommends evolution
gedit recommends python-gnome2
gnome-control-center recommends gnome-session
gnome-control-center recommends mousetweaks
gnome-panel-data recommends gnome-panel
gnome-screensaver recommends gnome-power-manager | xfce4-power-manager
synaptic recommends libgnome2-perl
Score is 766

Accept this solution? [Y/n/q/?] Y
The following packages will be REMOVED:
  evolution{a} evolution-couchdb{a} evolution-exchange{a} 
  evolution-indicator{a} evolution-plugins{a} f-spot{a} 
  firefox-gnome-support gbrainy{a} gdm{a} gdm-guest-session{a} 
  gnome-about{a} gnome-applets{a} gnome-mag{a} gnome-orca{a} gnome-panel{a} 
  gnome-power-manager{a} gnome-session{a} gnome-utils{a} 
  indicator-applet{a} indicator-applet-session{a} indicator-me{a} 
  libbonoboui2-0{a} libgail-gnome-module{a} libgnome-pilot2{a} 
  libgnome-vfs2.0-cil{a} libgnome2-0{a} libgnome2-perl{a} 
  libgnome2-vfs-perl{a} libgnome2.24-cil{a} libgnomepanel2.24-cil{a} 
  libgnomeui-0{a} libgnomevfs2-0 libgnomevfs2-extra{a} libhal-storage1 
  libhal1 liblpint-bonobo0{a} libpanel-applet2-0{a} mousetweaks{a} 
  nautilus-share{a} python-gnome2{a} python-gnomeapplet{a} 
  python-pyatspi{a} rhythmbox{a} rhythmbox-plugin-cdrecorder{a} 
  rhythmbox-plugins{a} rhythmbox-ubuntuone-music-store{a} 
  system-config-printer-gnome{a} tomboy{a} tsclient{a} ubuntu-desktop{a} 
  usb-creator-gtk{a} vinagre{a} 
0 packages upgraded, 0 newly installed, 52 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 125MB will be freed.
Do you want to continue? [Y/n/?] Y
Writing extended state information... Done
(Reading database ... 127255 files and directories currently installed.)
Removing evolution-plugins ...
Removing evolution-indicator ...
Removing evolution-exchange ...
Removing evolution-couchdb ...
Removing evolution ...
Removing f-spot ...
Removing firefox-gnome-support ...
Removing gbrainy ...
Removing ubuntu-desktop ...
Removing gdm-guest-session ...
Removing gdm ...
Removing indicator-me ...
Removing indicator-applet-session ...
Removing indicator-applet ...
Removing gnome-session ...
Removing gnome-applets ...
Removing gnome-panel ...
Removing gnome-about ...
Removing gnome-mag ...
Removing gnome-orca ...
Removing gnome-power-manager ...
Removing gnome-utils ...
Removing vinagre ...
Removing tsclient ...
Removing python-gnomeapplet ...
Removing mousetweaks ...
Removing tomboy ...
Removing libgnomepanel2.24-cil ...
Removing libgnomepanel2.24-cil from Mono
Removing libgail-gnome-module ...
Removing libpanel-applet2-0 ...
Removing system-config-printer-gnome ...
Removing rhythmbox-ubuntuone-music-store ...
Removing rhythmbox-plugins ...
Removing rhythmbox-plugin-cdrecorder ...
Removing rhythmbox ...
Removing python-pyatspi ...
Removing usb-creator-gtk ...
Removing python-gnome2 ...
Removing liblpint-bonobo0 ...
Removing nautilus-share ...
Removing libgnome2.24-cil ...
Removing libgnome2.24-cil from Mono
Removing libgnome2-perl ...
Removing libgnome-pilot2 ...
Removing libgnomeui-0 ...
Removing libbonoboui2-0 ...
Removing libgnome-vfs2.0-cil ...
Removing libgnome-vfs2.0-cil from Mono
Removing libgnome2-0 ...
Removing libgnome2-vfs-perl ...
Removing libgnomevfs2-extra ...
Removing libgnomevfs2-0 ...
Removing libhal-storage1 ...
Removing libhal1 ...
Processing triggers for man-db ...
Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for hicolor-icon-theme ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Processing triggers for python-support ...
Processing triggers for shared-mime-info ...
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done

adam@adam-test-VM:~$ 
```Removing libhal1 removes everything.

```
adam@adam-test-VM:~$ sudo aptitude install ubuntu-desktop
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
The following NEW packages will be installed:
  evolution evolution-couchdb evolution-exchange evolution-indicator 
  evolution-plugins{a} f-spot firefox-gnome-support gbrainy gdm 
  gdm-guest-session gnome-about gnome-applets gnome-mag gnome-orca 
  gnome-panel{a} gnome-power-manager gnome-session{a} gnome-utils hal{a} 
  indicator-applet{a} indicator-applet-session indicator-me{a} 
  libbonoboui2-0{a} libgail-gnome-module libgnome-pilot2{a} 
  libgnome-vfs2.0-cil{a} libgnome2-0{a} libgnome2-perl 
  libgnome2-vfs-perl{a} libgnome2.24-cil{a} libgnomepanel2.24-cil{a} 
  libgnomeui-0{a} libgnomevfs2-0{a} libgnomevfs2-extra{a} 
  libhal-storage1{a} libhal1{a} liblpint-bonobo0{a} libpanel-applet2-0{a} 
  mousetweaks nautilus-share pitivi python-gnome2{a} python-gnomeapplet{a} 
  python-pyatspi{a} rhythmbox rhythmbox-plugin-cdrecorder{a} 
  rhythmbox-plugins{a} rhythmbox-ubuntuone-music-store 
  system-config-printer-gnome tomboy tsclient ubuntu-desktop 
  usb-creator-gtk vinagre 
0 packages upgraded, 54 newly installed, 0 to remove and 0 not upgraded.
Need to get 6,140kB/16.2MB of archives. After unpacking 129MB will be used.
Do you want to continue? [Y/n/?]
```package ubuntu-desktop installs libhal1!   

What happened to HALsecotmy?  [https://wiki.ubuntu.com/Halsectomy](https://wiki.ubuntu.com/Halsectomy)
 HalSectomy is not fully implemented yet.
Currently, HAL is **removed** from the startup applications, but not **removed from the system. **However, since there are still programs that have no been fixed to work  without hal, they will require HAL to be installed.
In this case, gnomevfs is the blocker thats causing everything to be removed 


Looking at the debian logs, they are still investigating compiling libgnomevfs without HAL. Until they get that working, HAL will have to be installed, if you run a FULL gnome installation, unless you are using a non-debian OS such as Gentoo, Sabayon, or other *nix distros.

However, if you really want it to be removed, you can simply install gnome-minimal and remove hal.
**note that still, you cannot install Gimp, Cheese, or any of the apps here ->[https://wiki.ubuntu.com/Halsectomy](https://wiki.ubuntu.com/Halsectomy) and [http://wiki.debian.org/HALRemoval](http://wiki.debian.org/HALRemoval) (Ubuntu is based on the unstable branch of Debian, so im just refering to Debian's list because its a little more thorough)*

---

### Post by outleradam on 2010-09-08
It says on that site that GDM has the HALsectomy.  However, installing package gdm installs hal!

For some reason my mouse is grabbing hal rather then udev.  That's the problem I'm having and was trying to correct when I went on the rant here.  I was able to work around it by mapping buttons in compiz by manually editing the config files rather then through the GUI though, so it's no longer an issue.

---

### Post by sandyd on 2010-09-08
> **outleradam said:**
> It says on that site that GDM has the HALsectomy.  However, installing package gdm installs hal!

For some reason my mouse is grabbing hal rather then udev.  That's the problem I'm having and was trying to correct when I went on the rant here.  I was able to work around it by mapping buttons in compiz by manually editing the config files rather then through the GUI though, so it's no longer an issue.
check in /etc/hal/fdi/policy for the HAL policies

---

