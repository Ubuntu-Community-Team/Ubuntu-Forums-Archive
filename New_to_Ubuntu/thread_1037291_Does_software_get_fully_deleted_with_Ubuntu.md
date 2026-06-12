---
title: "Does software get fully deleted with Ubuntu?"
date: 2009-01-11
forum: New to Ubuntu
---

### Post by RedMartin on 2009-01-11
I installed Kubuntu-desktop on my 8.04 set-up. I didn't like it so found some Terminal commands to remove it and all the associated additional software.

During this process VLC player got removed. Assuming it had been deleted I went to Add/Remove and found VLC. Instead of downloading it simply reinstalled.

Does that mean that all the other software (Konqueror et al) is still on the drive but 'invisible'?

Is there an easy way to check?

---

### Post by taurus on 2009-01-11
It depends what command you used to delete KDE from your machine.

[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

---

### Post by RedMartin on 2009-01-11
> **taurus said:**
> It depends what command you used to delete KDE from your machine.

[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

It was *deep breath*
> sudo apt-get remove adept adept-batch adept-common adept-installer adept-manager adept-notifier adept-updater akregator amarok amarok-xine apport-qt ark arts cryptsetup debtags desktop-effects-kde digikam dmsetup dolphin enscript foomatic-db-gutenprint gdebi-kde gnupg-agent gpgsm gtk-qt-engine gwenview hpijs-ppds hplip-gui ijsgutenprint jockey-kde k3b kaddressbook kaffeine kamera karm katapult kate kbstate kcontrol kcron kde-guidance kde-guidance-powermanager kde-icons-mono kde-style-qtcurve kde-systemsettings kdeadmin-kfile-plugins kdebase-bin kdebase-bin-kde3 kdebase-data kdebase-kio-plugins kdebluetooth kdegraphics-kfile-plugins kdelibs-data kdelibs4c2a kdemultimedia-kfile-plugins kdemultimedia-kio-plugins kdenetwork-filesharing kdenetwork-kfile-plugins kdepasswd kdepim-kio-plugins kdepim-kresources kdepim-wizards kdeprint kdesktop kdesudo kdm kdnssd keep kfind kghostview khelpcenter kicker kio-apt kio-locate kio-umountwrapper kipi-plugins klipper kmag kmail kmailcvt kmenuedit kmilo kmix kmousetool kmplayer-base kmplayer-konq-plugins knetworkconf knotes konq-plugins konqueror konqueror-nsplugins konsole kontact konversation kooka kopete korganizer kpdf kpf kppp krdc krfb kscreensaver ksmserver ksnapshot ksvg ksysguard ksysguardd ksystemlog ktorrent kubuntu-artwork-usplash kubuntu-default-settings kubuntu-desktop kubuntu-docs kubuntu-konqueror-shortcuts kvkbd kwalletmanager kwin kwin-style-crystal language-selector-qt libakode2 libarts1-akode libarts1c2a libartsc0 libaudio2 libavahi-qt3-1 libavcodec1d libavutil1d libclucene0ldbl libdbus-qt-1-1c2 libept0 libexiv2-2 libfftw3-3 libflac++6 libgmp3c2 libgsm1 libifp4 libijs-0.35 libjpeg-progs libk3b2 libkbluetooth0 libkcal2b libkcddb1 libkdcraw3 libkdepim1a libkexiv2-3 libkipi0 libkleopatra1 libkmime2 libkonq4 libkpimexchange1 libkpimidentities1 libksba8 libkscan1 libksieve0 libktnef1 liblua50 liblualib50 libmad0 libmimelib1c2a libmodplug0c2 libmpcdec3 libnjb5 libofa0 libpoppler-qt2 libpostproc1d libpq5 libpythonize0 libqt-perl libqt3-mt libqt4-core libqt4-gui librsync1 libruby1.8 libsearchclient0 libskim0 libsmokeqt1 libstreamanalyzer0 libstreams0 libstrigihtmlgui0 libtunepimp5 libxapian15 libxcb-shape0 libxcb-shm0 libxcb-xv0 libxine1 libxine1-bin libxine1-console libxine1-ffmpeg libxine1-misc-plugins libxine1-plugins libxine1-x libxvmc1 network-manager-kde networkstatus openoffice.org-kde openoffice.org-style-crystal perl-suid pinentry-qt poster psutils pykdeextensions python-dev python-kde3 python-qt3 python-qt4 python-qt4-common python-qt4-dbus python-reportlab python-sip4 python2.5-dev qca-tls rdiff-backup ruby ruby1.8 scim-bridge-client-qt scim-qtimm skim software-properties-kde speedcrunch strigi-applet strigi-daemon system-config-printer-kde ttf-arphic-ukai vorbis-tools && sudo apt-get install ubuntu-desktop


---

### Post by ajcham on 2009-01-11
> **RedMartin said:**
> I installed Kubuntu-desktop on my 8.04 set-up. I didn't like it so found some Terminal commands to remove it and all the associated additional software.

During this process VLC player got removed. Assuming it had been deleted I went to Add/Remove and found VLC. Instead of downloading it simply reinstalled.

Does that mean that all the other software (Konqueror et al) is still on the drive but 'invisible'?

Is there an easy way to check?

When you install software the Package Manager downloads the appropriate Deb files for installation.  The Deb files are then kept in **/var/cache/apt/archives** rather than being deleted, preventing the need to download again if you want to reinstall.

If you need to free up space you can use ```
sudo apt-get clean
``` or ```
sudo apt-get autoclean
```
to get rid of them (the first command removes all of them, the second only removes the ones that are no longer in the repos).

---

### Post by RedMartin on 2009-01-11
Thanks Ajcham.

That's sorted it. I love Linux. You literally do learn something new every day.

---

### Post by theozzlives on 2009-01-11
you do have some hidden configuration folders and files hidded in your ~/ directory, unless you know what they are... leave em

---

