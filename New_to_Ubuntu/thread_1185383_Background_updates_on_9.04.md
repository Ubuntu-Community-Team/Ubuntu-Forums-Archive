---
title: "Background updates on 9.04?"
date: 2009-06-12
forum: New to Ubuntu
---

### Post by Idir on 2009-06-12
Hi, I am currently using Jaunty Jackalope and I used to get the Update Manager among the startup programs every time I turn on my computer, offering me to install the updates, however, I always get an error message telling me that “not all updates can be installed” and I then get offered to update using the Distribution Upgrade window.

[IMG]http://www.ubuntu.com/files/u3/update-notification.png[/IMG]
Earlier, when I was on 8.10, I used to get that orange taskbar notifier  which was useful for me as it downloaded and installed updates in background (which is the only way I can update, as there is absolutely no way I can use the “Partial Distribution Upgrade” as my connection would take days for that).

So is there a way to get it the automatic background update to work again? Thanks.

---

### Post by Hospadar on 2009-06-12
What happens when you attempt to update in a terminal?  often the terminal will give some more instructive errors
Applications->Accessories->Terminal
```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by Idir on 2009-06-12
Hi. For sudo apt-get update, I got this:

```
anis@anis-desktop:~$ sudo apt-get update
[sudo] password for anis: 
Hit http://security.ubuntu.com jaunty-security Release.gpg                     
Ign http://security.ubuntu.com jaunty-security/universe Translation-en_US      
Hit http://archive.canonical.com hardy Release.gpg                             
Hit http://archive.ubuntu.com hardy-updates Release.gpg                        
Ign http://security.ubuntu.com jaunty-security/main Translation-en_US          
Ign http://security.ubuntu.com jaunty-security/multiverse Translation-en_US    
Ign http://security.ubuntu.com jaunty-security/restricted Translation-en_US    
Hit http://security.ubuntu.com jaunty-security Release                         
Hit http://security.ubuntu.com jaunty-security/universe Packages               
Hit http://security.ubuntu.com jaunty-security/main Packages                   
Hit http://security.ubuntu.com jaunty-security/multiverse Packages             
Hit http://security.ubuntu.com jaunty-security/restricted Packages             
Hit http://security.ubuntu.com jaunty-security/universe Sources                
Ign http://archive.canonical.com hardy/partner Translation-en_US               
Ign http://archive.ubuntu.com hardy-updates/main Translation-en_US             
Hit http://security.ubuntu.com jaunty-security/main Sources                    
Hit http://security.ubuntu.com jaunty-security/multiverse Sources              
Hit http://security.ubuntu.com jaunty-security/restricted Sources              
Hit http://archive.canonical.com hardy Release                                 
Ign http://archive.ubuntu.com hardy-updates/restricted Translation-en_US       
Ign http://archive.ubuntu.com hardy-updates/universe Translation-en_US        
Hit http://archive.ubuntu.com hardy-security Release.gpg                      
Ign http://archive.ubuntu.com hardy-security/main Translation-en_US           
Ign http://archive.ubuntu.com hardy-security/restricted Translation-en_US     
Ign http://archive.ubuntu.com hardy-security/universe Translation-en_US       
Ign http://archive.canonical.com hardy/partner Packages                       
Hit http://dz.archive.ubuntu.com hardy-backports Release.gpg
Ign http://dz.archive.ubuntu.com hardy-backports/main Translation-en_US
Hit http://archive.ubuntu.com jaunty Release.gpg
Ign http://archive.ubuntu.com jaunty/universe Translation-en_US
Ign http://archive.ubuntu.com jaunty/main Translation-en_US
Ign http://archive.ubuntu.com jaunty/restricted Translation-en_US
Ign http://archive.ubuntu.com jaunty/multiverse Translation-en_US
Ign http://dz.archive.ubuntu.com hardy-backports/restricted Translation-en_US
Ign http://dz.archive.ubuntu.com hardy-backports/universe Translation-en_US
Ign http://dz.archive.ubuntu.com hardy-backports/multiverse Translation-en_US
Hit http://dz.archive.ubuntu.com hardy-backports Release             
Hit http://archive.ubuntu.com jaunty-updates Release.gpg            
Hit http://dz.archive.ubuntu.com hardy-backports/main Packages       
Ign http://archive.ubuntu.com jaunty-updates/universe Translation-en_US
Ign http://archive.ubuntu.com jaunty-updates/main Translation-en_US
Ign http://archive.ubuntu.com jaunty-updates/multiverse Translation-en_US
Ign http://archive.ubuntu.com jaunty-updates/restricted Translation-en_US
Hit http://archive.ubuntu.com hardy-updates Release
Hit http://archive.ubuntu.com hardy-security Release
Hit http://archive.ubuntu.com jaunty Release   
Hit http://dz.archive.ubuntu.com hardy-backports/restricted Packages           
Hit http://dz.archive.ubuntu.com hardy-backports/universe Packages   
Hit http://dz.archive.ubuntu.com hardy-backports/multiverse Packages 
Hit http://dz.archive.ubuntu.com hardy-backports/main Sources        
Ign http://archive.canonical.com hardy/partner Sources               
Hit http://dz.archive.ubuntu.com hardy-backports/restricted Sources  
Hit http://dz.archive.ubuntu.com hardy-backports/universe Sources
Hit http://dz.archive.ubuntu.com hardy-backports/multiverse Sources
Hit http://archive.ubuntu.com jaunty-updates Release
Hit http://archive.ubuntu.com hardy-updates/main Packages           
Hit http://archive.ubuntu.com hardy-updates/restricted Packages
Hit http://archive.ubuntu.com hardy-updates/universe Packages
Hit http://archive.ubuntu.com hardy-updates/main Sources
Hit http://archive.ubuntu.com hardy-updates/restricted Sources
Hit http://archive.ubuntu.com hardy-security/main Packages
Hit http://archive.ubuntu.com hardy-security/restricted Packages
Hit http://archive.ubuntu.com hardy-security/universe Packages
Hit http://archive.ubuntu.com hardy-security/main Sources
Hit http://archive.ubuntu.com hardy-security/restricted Sources
Hit http://archive.ubuntu.com jaunty/universe Packages
Hit http://archive.ubuntu.com jaunty/main Packages
Hit http://archive.ubuntu.com jaunty/restricted Packages
Hit http://archive.canonical.com hardy/partner Packages
Hit http://archive.ubuntu.com jaunty/multiverse Packages
Hit http://archive.ubuntu.com jaunty/universe Sources
Hit http://archive.ubuntu.com jaunty/main Sources
Hit http://archive.ubuntu.com jaunty/multiverse Sources
Hit http://archive.ubuntu.com jaunty/restricted Sources
Hit http://archive.ubuntu.com jaunty-updates/universe Packages
Hit http://archive.ubuntu.com jaunty-updates/main Packages
Hit http://archive.ubuntu.com jaunty-updates/multiverse Packages
Hit http://archive.canonical.com hardy/partner Sources
Hit http://archive.ubuntu.com jaunty-updates/restricted Packages
Hit http://archive.ubuntu.com jaunty-updates/universe Sources
Hit http://archive.ubuntu.com jaunty-updates/main Sources
Hit http://archive.ubuntu.com jaunty-updates/multiverse Sources
Hit http://archive.ubuntu.com jaunty-updates/restricted Sources
Reading package lists... Done
```

And this for sudo apt-get upgrade
```
anis@anis-desktop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  avidemux classpath classpath-common classpath-gtkpeer firefox firefox-3.0
  firefox-3.0-gnome-support flashplugin-nonfree gnome-themes
  gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad
  gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly hwtest
  hwtest-gtk landscape-client lastfm libalut0 libdvdnav4 libjack0 libqt4-core
  libqt4-gui libqt4-sql libquicktime1 usb-creator vlc-nox vlc-plugin-pulse
The following packages will be upgraded:
  acpi acpid app-install-data-commercial apport apport-gtk apturl ash
  avidemux-common bluetooth bluez bluez-cups bluez-utils cacao cdrdao
  compizconfig-backend-gconf consolekit cpp-4.2 cron cups cups-bsd cups-client
  cups-common epiphany-browser epiphany-browser-data epiphany-gecko escputil
  evince evolution-data-server-common evolution-documentation-en fdutils
  firefox-gnome-support foomatic-db-engine fortune-mod fortunes-min freeglut3
  gcc-4.2 gcc-4.2-base gisomount gnome-about gnome-app-install gnome-applets
  gnome-applets-data gnome-desktop-data gnome-netstatus-applet
  gnome-settings-daemon gnome-system-tools gnome-volume-manager gparted
  gtkpod-aac guile-1.6-libs hal hunspell-fr ifrench-gut inkscape java-common
  language-pack-kde-fr language-pack-kde-fr-base libao2 libaudio2
  libbluetooth3 libboost-date-time1.34.1 libboost-filesystem1.34.1
  libboost-python1.34.1 libboost-thread1.34.1 libcamel1.2-14 libcdaudio1
  libck-connector0 libconsole libcups2 libcupsimage2 libcurl3 libdc1394-13
  libdvbpsi4 libebackend1.2-0 libebook1.2-9 libecal1.2-7 libedata-book1.2-2
  libedata-cal1.2-6 libedataserver1.2-11 libedataserverui1.2-8 libeel2-2
  libeel2-data libegroupwise1.2-13 libelfg0 libevdocument1 libevview1
  libexchange-storage1.2-3 libfreebob0 libfreetype6 libgcj-common
  libgdata-google1.2-1 libgdata1.2-1 libgl1-mesa-dri libgl1-mesa-glx
  libglu1-mesa libgmyth0 libgnome-desktop-2-11 libguile-ltdl-1
  libgweather-common libgweather1 libhal-storage1 libhal1 libical0
  libinklevel4 libiptcdata0 libiso9660-5 liblzo2-2 libmad0 libmagick++10
  libmagickcore1 libmagickwand1 libmatroska0 libmetacity0 libmms0
  libmodplug0c2 libmp4v2-0 libmpeg2-4 libmpfr1ldbl libmysqlclient15off
  libnautilus-extension1 libpam-ck-connector libportaudio0 libpq5 libpurple0
  libqthreads-12 libscrollkeeper0 libsidplay1 libsoundtouch1c2
  libsoup-gnome2.4-1 libsoup2.4-1 libsqlite3-0 libtar libtracker-gtk0
  libtrackerclient0 libudev0 libvolume-id1 libwmf0.2-7 libwmf0.2-7-gtk
  libwxbase2.6-0 libwxgtk2.6-0 libx11-xcb1 libxosd2 mesa-utils metacity
  metacity-common myspell-de-de mysql-common nautilus nautilus-actions
  nautilus-cd-burner nautilus-data notification-daemon ntp ntpdate
  nvidia-kernel-common odbcinst1debian1 openssl-blacklist pidgin pidgin-data
  pidgin-musictracker powermanagement-interface powernowd powertop privoxy
  python-apport python-cupshelpers python-elementtree python-problem-report
  python2.5 python2.5-minimal rar screen-profiles splix sqlite3 sun-java5-bin
  sun-java5-jre sun-java5-plugin sun-java6-bin sun-java6-jre sun-java6-plugin
  synaptic system-config-printer-common system-config-printer-gnome tsocks
  ttf-dejavu ttf-dejavu-extra ttf-kochi-gothic ttf-kochi-mincho
  ttf-malayalam-fonts ubuntu-docs udev unixodbc update-manager
  update-manager-core wfrench xulrunner-1.9 xulrunner-1.9-gnome-support xutils
  xutils-dev
199 upgraded, 0 newly installed, 0 to remove and 27 not upgraded.
Need to get 105MB/180MB of archives.
After this operation, 7782kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://archive.ubuntu.com jaunty/multiverse sun-java6-bin 6-13-1 [28.3MB]
20% [1 sun-java6-bin 21376074/28.3MB 75%]    
```

---

### Post by meeples on 2009-06-12
> **Idir said:**
> Hi. For sudo apt-get update, I got this:

```
anis@anis-desktop:~$ sudo apt-get update
[sudo] password for anis: 
Hit http://security.ubuntu.com jaunty-security Release.gpg                     
Ign http://security.ubuntu.com jaunty-security/universe Translation-en_US      
Hit http://archive.canonical.com hardy Release.gpg                             
Hit http://archive.ubuntu.com hardy-updates Release.gpg                        
Ign http://security.ubuntu.com jaunty-security/main Translation-en_US          
Ign http://security.ubuntu.com jaunty-security/multiverse Translation-en_US    
Ign http://security.ubuntu.com jaunty-security/restricted Translation-en_US    
Hit http://security.ubuntu.com jaunty-security Release                         
Hit http://security.ubuntu.com jaunty-security/universe Packages               
Hit http://security.ubuntu.com jaunty-security/main Packages                   
Hit http://security.ubuntu.com jaunty-security/multiverse Packages             
Hit http://security.ubuntu.com jaunty-security/restricted Packages             
Hit http://security.ubuntu.com jaunty-security/universe Sources                
Ign http://archive.canonical.com hardy/partner Translation-en_US               
Ign http://archive.ubuntu.com hardy-updates/main Translation-en_US             
Hit http://security.ubuntu.com jaunty-security/main Sources                    
Hit http://security.ubuntu.com jaunty-security/multiverse Sources              
Hit http://security.ubuntu.com jaunty-security/restricted Sources              
Hit http://archive.canonical.com hardy Release                                 
Ign http://archive.ubuntu.com hardy-updates/restricted Translation-en_US       
Ign http://archive.ubuntu.com hardy-updates/universe Translation-en_US        
Hit http://archive.ubuntu.com hardy-security Release.gpg                      
Ign http://archive.ubuntu.com hardy-security/main Translation-en_US           
Ign http://archive.ubuntu.com hardy-security/restricted Translation-en_US     
Ign http://archive.ubuntu.com hardy-security/universe Translation-en_US       
Ign http://archive.canonical.com hardy/partner Packages                       
Hit http://dz.archive.ubuntu.com hardy-backports Release.gpg
Ign http://dz.archive.ubuntu.com hardy-backports/main Translation-en_US
Hit http://archive.ubuntu.com jaunty Release.gpg
Ign http://archive.ubuntu.com jaunty/universe Translation-en_US
Ign http://archive.ubuntu.com jaunty/main Translation-en_US
Ign http://archive.ubuntu.com jaunty/restricted Translation-en_US
Ign http://archive.ubuntu.com jaunty/multiverse Translation-en_US
Ign http://dz.archive.ubuntu.com hardy-backports/restricted Translation-en_US
Ign http://dz.archive.ubuntu.com hardy-backports/universe Translation-en_US
Ign http://dz.archive.ubuntu.com hardy-backports/multiverse Translation-en_US
Hit http://dz.archive.ubuntu.com hardy-backports Release             
Hit http://archive.ubuntu.com jaunty-updates Release.gpg            
Hit http://dz.archive.ubuntu.com hardy-backports/main Packages       
Ign http://archive.ubuntu.com jaunty-updates/universe Translation-en_US
Ign http://archive.ubuntu.com jaunty-updates/main Translation-en_US
Ign http://archive.ubuntu.com jaunty-updates/multiverse Translation-en_US
Ign http://archive.ubuntu.com jaunty-updates/restricted Translation-en_US
Hit http://archive.ubuntu.com hardy-updates Release
Hit http://archive.ubuntu.com hardy-security Release
Hit http://archive.ubuntu.com jaunty Release   
Hit http://dz.archive.ubuntu.com hardy-backports/restricted Packages           
Hit http://dz.archive.ubuntu.com hardy-backports/universe Packages   
Hit http://dz.archive.ubuntu.com hardy-backports/multiverse Packages 
Hit http://dz.archive.ubuntu.com hardy-backports/main Sources        
Ign http://archive.canonical.com hardy/partner Sources               
Hit http://dz.archive.ubuntu.com hardy-backports/restricted Sources  
Hit http://dz.archive.ubuntu.com hardy-backports/universe Sources
Hit http://dz.archive.ubuntu.com hardy-backports/multiverse Sources
Hit http://archive.ubuntu.com jaunty-updates Release
Hit http://archive.ubuntu.com hardy-updates/main Packages           
Hit http://archive.ubuntu.com hardy-updates/restricted Packages
Hit http://archive.ubuntu.com hardy-updates/universe Packages
Hit http://archive.ubuntu.com hardy-updates/main Sources
Hit http://archive.ubuntu.com hardy-updates/restricted Sources
Hit http://archive.ubuntu.com hardy-security/main Packages
Hit http://archive.ubuntu.com hardy-security/restricted Packages
Hit http://archive.ubuntu.com hardy-security/universe Packages
Hit http://archive.ubuntu.com hardy-security/main Sources
Hit http://archive.ubuntu.com hardy-security/restricted Sources
Hit http://archive.ubuntu.com jaunty/universe Packages
Hit http://archive.ubuntu.com jaunty/main Packages
Hit http://archive.ubuntu.com jaunty/restricted Packages
Hit http://archive.canonical.com hardy/partner Packages
Hit http://archive.ubuntu.com jaunty/multiverse Packages
Hit http://archive.ubuntu.com jaunty/universe Sources
Hit http://archive.ubuntu.com jaunty/main Sources
Hit http://archive.ubuntu.com jaunty/multiverse Sources
Hit http://archive.ubuntu.com jaunty/restricted Sources
Hit http://archive.ubuntu.com jaunty-updates/universe Packages
Hit http://archive.ubuntu.com jaunty-updates/main Packages
Hit http://archive.ubuntu.com jaunty-updates/multiverse Packages
Hit http://archive.canonical.com hardy/partner Sources
Hit http://archive.ubuntu.com jaunty-updates/restricted Packages
Hit http://archive.ubuntu.com jaunty-updates/universe Sources
Hit http://archive.ubuntu.com jaunty-updates/main Sources
Hit http://archive.ubuntu.com jaunty-updates/multiverse Sources
Hit http://archive.ubuntu.com jaunty-updates/restricted Sources
Reading package lists... Done
```

And this for sudo apt-get upgrade
```
anis@anis-desktop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  avidemux classpath classpath-common classpath-gtkpeer firefox firefox-3.0
  firefox-3.0-gnome-support flashplugin-nonfree gnome-themes
  gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad
  gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly hwtest
  hwtest-gtk landscape-client lastfm libalut0 libdvdnav4 libjack0 libqt4-core
  libqt4-gui libqt4-sql libquicktime1 usb-creator vlc-nox vlc-plugin-pulse
The following packages will be upgraded:
  acpi acpid app-install-data-commercial apport apport-gtk apturl ash
  avidemux-common bluetooth bluez bluez-cups bluez-utils cacao cdrdao
  compizconfig-backend-gconf consolekit cpp-4.2 cron cups cups-bsd cups-client
  cups-common epiphany-browser epiphany-browser-data epiphany-gecko escputil
  evince evolution-data-server-common evolution-documentation-en fdutils
  firefox-gnome-support foomatic-db-engine fortune-mod fortunes-min freeglut3
  gcc-4.2 gcc-4.2-base gisomount gnome-about gnome-app-install gnome-applets
  gnome-applets-data gnome-desktop-data gnome-netstatus-applet
  gnome-settings-daemon gnome-system-tools gnome-volume-manager gparted
  gtkpod-aac guile-1.6-libs hal hunspell-fr ifrench-gut inkscape java-common
  language-pack-kde-fr language-pack-kde-fr-base libao2 libaudio2
  libbluetooth3 libboost-date-time1.34.1 libboost-filesystem1.34.1
  libboost-python1.34.1 libboost-thread1.34.1 libcamel1.2-14 libcdaudio1
  libck-connector0 libconsole libcups2 libcupsimage2 libcurl3 libdc1394-13
  libdvbpsi4 libebackend1.2-0 libebook1.2-9 libecal1.2-7 libedata-book1.2-2
  libedata-cal1.2-6 libedataserver1.2-11 libedataserverui1.2-8 libeel2-2
  libeel2-data libegroupwise1.2-13 libelfg0 libevdocument1 libevview1
  libexchange-storage1.2-3 libfreebob0 libfreetype6 libgcj-common
  libgdata-google1.2-1 libgdata1.2-1 libgl1-mesa-dri libgl1-mesa-glx
  libglu1-mesa libgmyth0 libgnome-desktop-2-11 libguile-ltdl-1
  libgweather-common libgweather1 libhal-storage1 libhal1 libical0
  libinklevel4 libiptcdata0 libiso9660-5 liblzo2-2 libmad0 libmagick++10
  libmagickcore1 libmagickwand1 libmatroska0 libmetacity0 libmms0
  libmodplug0c2 libmp4v2-0 libmpeg2-4 libmpfr1ldbl libmysqlclient15off
  libnautilus-extension1 libpam-ck-connector libportaudio0 libpq5 libpurple0
  libqthreads-12 libscrollkeeper0 libsidplay1 libsoundtouch1c2
  libsoup-gnome2.4-1 libsoup2.4-1 libsqlite3-0 libtar libtracker-gtk0
  libtrackerclient0 libudev0 libvolume-id1 libwmf0.2-7 libwmf0.2-7-gtk
  libwxbase2.6-0 libwxgtk2.6-0 libx11-xcb1 libxosd2 mesa-utils metacity
  metacity-common myspell-de-de mysql-common nautilus nautilus-actions
  nautilus-cd-burner nautilus-data notification-daemon ntp ntpdate
  nvidia-kernel-common odbcinst1debian1 openssl-blacklist pidgin pidgin-data
  pidgin-musictracker powermanagement-interface powernowd powertop privoxy
  python-apport python-cupshelpers python-elementtree python-problem-report
  python2.5 python2.5-minimal rar screen-profiles splix sqlite3 sun-java5-bin
  sun-java5-jre sun-java5-plugin sun-java6-bin sun-java6-jre sun-java6-plugin
  synaptic system-config-printer-common system-config-printer-gnome tsocks
  ttf-dejavu ttf-dejavu-extra ttf-kochi-gothic ttf-kochi-mincho
  ttf-malayalam-fonts ubuntu-docs udev unixodbc update-manager
  update-manager-core wfrench xulrunner-1.9 xulrunner-1.9-gnome-support xutils
  xutils-dev
199 upgraded, 0 newly installed, 0 to remove and 27 not upgraded.
Need to get 105MB/180MB of archives.
After this operation, 7782kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://archive.ubuntu.com jaunty/multiverse sun-java6-bin 6-13-1 [28.3MB]
20% [1 sun-java6-bin 21376074/28.3MB 75%]    
```

your using both the hardy repositories and the jaunty ones?

was this on purpose?

---

### Post by Idir on 2009-06-13
No? Is there a way to fix that?

---

### Post by Michael.Godawski on 2009-06-13
hi, 

yes, there is, or at least should be a way. ;)

Can you please post the output of 

```
cat /etc/apt/sources.list
```

---

### Post by meeples on 2009-06-13
yea, you only need the jaunty repositories, im thinking maybe be because your using the hardy ones too, you might be getting a lot more updates than you need.


so yeah, what Michael.Godawski said. :)

---

### Post by Idir on 2009-06-13
```
anis@anis-desktop:~$ cat /etc/apt/sources.list
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.


## Major bug fix updates produced after the final release of the
## distribution.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.

deb http://archive.ubuntu.com/ubuntu/ jaunty-security main restricted universe
deb-src http://archive.ubuntu.com/ubuntu/ jaunty-security main restricted
deb http://archive.ubuntu.com/ubuntu/ jaunty universe main restricted multiverse
deb-src http://archive.ubuntu.com/ubuntu/ jaunty universe main multiverse restricted #Added by software-properties
deb http://security.ubuntu.com/ubuntu/ jaunty-security universe main multiverse restricted
deb-src http://security.ubuntu.com/ubuntu/ jaunty-security universe main multiverse restricted
deb http://archive.ubuntu.com/ubuntu/ jaunty-updates universe main multiverse restricted
deb-src http://archive.ubuntu.com/ubuntu/ jaunty-updates universe main multiverse restricted
# deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)]/ jaunty main restricted
```

---

### Post by meeples on 2009-06-13
i dont understand how your getting hardy updates then ...

hmm, because according to your sources list, you've only got jaunty repositories.

which is what you should have, yet when you do an apt-get update,, your getting package lists from the hardy repositories as well..


now that is a thinker.

---

### Post by scorp123 on 2009-06-13
> **meeples said:**
> i dont understand how your getting hardy updates then ... Probably additional repos underneath /etc/apt/sources.list.d/ ... 

@OP: Do you have any *.list files in that location? /etc/apt/sources.list.d/ ... 

Their syntax is the same as for the sources.list file. Could be that you defined some additional repos there.

---

### Post by Idir on 2009-06-14
> **scorp123 said:**
> Probably additional repos underneath /etc/apt/sources.list.d/ ... 

@OP: Do you have any *.list files in that location? /etc/apt/sources.list.d/ ... 

Their syntax is the same as for the sources.list file. Could be that you defined some additional repos there.

I don't have any files there (even if displaying hidden files)

---

### Post by Elfy on 2009-06-14
Not only is it a hardy repo but also it is the backports repo.

Can you run this command and post the output please.

```
sudo find /etc -type f -iname *.list* -print
```

---

### Post by Idir on 2009-06-14
> **forestpixie said:**
> Not only is it a hardy repo but also it is the backports repo.

Can you run this command and post the output please.

```
sudo find /etc -type f -iname *.list* -print
```


```
/etc/apt/sources.list
/etc/apt/sources.list.save
/etc/apt/sources.list.distUpgrade
/etc/gnome/defaults.list

```

---

