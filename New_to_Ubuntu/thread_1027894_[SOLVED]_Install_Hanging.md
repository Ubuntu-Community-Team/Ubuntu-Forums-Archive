---
title: "[SOLVED] Install Hanging"
date: 2009-01-01
forum: New to Ubuntu
---

### Post by dragonwolf on 2009-01-01
Hey guys as you have gathered from the placement of this thread that I am new to Linux distro's specifically ubuntu.

Anyways as the title reads I am having some installation issues-
when I try to install ubuntu on a blank HD I get to-

```
loading please wait.....

Busybbox v.1.10.2 (Ubuntu 1:1.10.2-1ubuntu6) built-in shell (ash)
Enter "help" for a list of built-in commands.

(initramfs) {  99.675944} sd 6:0:0:2: {sdc} Asuming drive cache: write thru
{  99:680927} sd 6:0:0:2: {sdc} Assuming drive cache: write thru

```
and it hangs here untill I tell it to exit then I get

```
cp: cannot create '/root/var/log/': no such file or directory
mount: mounting /root/dev on /dev..static/dev/ failed: no such file or directory
mounting /sys on /root.sys/failed: no such file or directory
mount: mounting /proc on root/proc faialed: no such fiel or directory

Target filesystem doesn't have /sbin/init
no init found. try passing init= bootarg

```
back to the busybox promt

little hardware description here-

XFX Nvidea 750a SLI Mobo
80GB Sata HD
4 GB DDR2 Ram
AMD Phenom 8650 Processor
13-1 Media card Reader
generic PCI USB Expansion card(6port)
2port PCI 1394 Expansion card
Nvidia 9800 GT PCIe Graphics card
1 IDE DVD Burner
1 SATA DVD Burner
1 Floppy Drive
all other peripherals have been removed

the installation media does work I know this due to the fact that this is normally a windows box I used VMware inside windows to ply with ubuntu prior to trying it on this HArd drive windows HD is a 750gb sata

installation media is ubuntu 8.10 desktop from ubuntu not downloaded I waited the 10 weeks to get it

anyways if I'm thinking right this is a driver issue similar to the f6 driver for windows my issue is 2 fold if that is the problem the nforce chipset linux drivers it seems are for just about every major distro of linux but ubuntu so any idea which one to use? and then once that is solved how do I use it

if that is even the issue.

---

### Post by HotShotDJ on 2009-01-01
I'm not exactly sure what the issue is here, although I suspect that the standard Desktop graphical installation is having problems with your video card.  Again, this is just a guess, but it is the most common problem.  You can get around this by using the [Alternate Installer]("http://www.ubuntu.com/getubuntu/downloadmirrors#alternate"), which is text-based.  Once you've successfully installed, you should be able to get your hardware configured properly.

---

### Post by dragonwolf on 2009-01-01
Well it seems the issue was 2 fold one it was due to a hardware conflict form some or one of the extra hardware I have, finally got in the install after unplugging the sata drive after unplugging everything else, however still not seeing the hard drive I know the HD works as I have tested it on windows so gotta be a sata driver for the mobo now I gotta figure out which one and how to use it

---

### Post by cariboo on 2009-01-01
You may want to check the BIOS to see if it is emulation mode, for Ubuntu change the emulation mode to ACHI. If you don't have an up-to-date xp installation you may have a problem booting, but if you are updated to sp3 you  shouldn't have a problem.

Jim

---

### Post by dragonwolf on 2009-01-01
not trying to dual boot and I have checked the bios changeed to shci with linux mode whatever that is also not dual booting this hard drive simply ubuntu only hd I ran ubuntu ina vm on my windows hd

---

### Post by dragonwolf on 2009-01-01
ok it's official it's a driver for my hd that ubuntu does not have

finally got into the install and it does not see the hd  there are chipset drivers avail on nvidias site however not of them are specifically for ubuntu

choices are

fedora6
rhel3_u7
rhel3_u8
rhel4_u4
rhel4_u5
rhel5
sles10
suse10.2

so which one do I use and how?

my bios at this point are set ahci enabled and Change the AHCI DID for Linuz is enabled( I have tried this both ways to no avail):confused:

---

### Post by hyper_ch on 2009-01-02
the distros normally don't have "individual" drivers, they are normally stored in the kernel. So if you the kernel on another distro is the same and on the one you try it should both have same drivers.

---

### Post by dragonwolf on 2009-01-02
> **hyper_ch said:**
> the distros normally don't have "individual" drivers, they are normally stored in the kernel. So if you the kernel on another distro is the same and on the one you try it should both have same drivers.
 ok mind you when it comes to linux I'm a newb so exactly how do I figure that out and then once I do then what? Don't mind doing the work but I'm no coder but I am serious on learning this and making it work so I could really use the help.

---

### Post by dragonwolf on 2009-01-02
well I was partially correct the issue is that ubuntu does not see my sata hd after some research this is actually quite common with my chipset and motherboard even though the only working resolution I have found so far is to go kubuntu which I relly didn't want to do I prefer the gnome desktop as opposed to the kde desktop oh well this will atleast get me going. Seems by all I've found that its a kernel issue insider ubuntu and unfortunatly the workaround is to use the pci=nomsi on the kernel line of the boot loader that with this distro of ubuntu I cannot get to so it does me no good, tried kubuntu just out of curiosity and found the hd right away.

Might still have a video issue once it finished installing but thats up in the air as I'm not using onboard graphics rather using a pcie card. will def have to update drivers for it though. oh well kubuntu it is sucks feels to much like windows to me, lol

---

### Post by LowSky on 2009-01-02
once you install kubuntu just install ubuntu-desktop package and then remove kde packages its very simple... its an extra step but it works

[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)
the code i'm providing will remove kde and install gnome it works for 8.10, if using another version see the link above
```
sudo apt-get remove adept akregator amarok amarok-common amarok-engine-xine apport-qt ark dolphin dragonplayer exiv2 foomatic-db-gutenprint gdebi-kde gnupg-agent gtk-qt-engine guidance-power-manager gwenview hpijs-ppds hplip-gui ijsgutenprint imagemagick install-package jockey-kde k3b k3b-data kaddressbook kamera kate kde-icons-oxygen kde-printer-applet kde-window-manager kde-zeroconf kdebase-bin kdebase-data kdebase-plasma kdebase-runtime kdebase-runtime-bin-kde4 kdebase-runtime-data kdebase-runtime-data-common kdebase-workspace-bin kdebase-workspace-data kdebase-workspace-libs4+5 kdebluetooth kdegraphics-strigi-plugins kdelibs-bin kdelibs-data kdelibs4c2a kdelibs5 kdelibs5-data kdemultimedia-kio-plugins kdepasswd kdepim-kresources kdepim-strigi-plugins kdepim-wizards kdepimlibs-data kdepimlibs5 kdeplasma-addons kdeplasma-addons-data kdeplasma-addons-libs4 kdesudo kdm kfind kgrubeditor khelpcenter4 klipper kmag kmail kmix kmousetool knotes konqueror konqueror-nsplugins konqueror-plugin-searchbar konsole kontact konversation kopete korganizer krdc krfb ksnapshot ksysguard ksysguardd ksystemlog ktimetracker ktorrent kubuntu-artwork-usplash kubuntu-default-settings kubuntu-desktop kubuntu-docs kubuntu-konqueror-shortcuts kuser kvkbd kwalletmanager language-selector-qt libakonadiprivate1 libarts1c2a libartsc0 libaudio2 libavahi-qt3-1 libcapseo0 libcaptury0 libclucene0ldbl libdbus-1-qt3 libdbus-qt-1-1c2 libexiv2-4 libfftw3-3 libflac++6 libgeoip1 libifp4 libk3b3 libkcddb4 libkdecorations4 libkdepim4 libkholidays4 libkipi-common libkipi5 libkleo4 libkonq5 libkonq5-templates libkpgp4 libksieve4 libkwineffects1 liblua50 liblualib50 libmimelib4 libmodplug0c2 libmpcdec3 libmysqlclient15off libnjb5 libofa0 libokularcore1 libphonon4 libplasma2 libpoppler-qt4-3 libpq5 libqca2 libqca2-plugin-ossl libqimageblitz4 libqt3-mt libqt4-assistant libqt4-core libqt4-dbus libqt4-designer libqt4-help libqt4-network libqt4-opengl libqt4-qt3support libqt4-script libqt4-sql libqt4-sql-mysql libqt4-svg libqt4-test libqt4-webkit libqt4-xml libqt4-xmlpatterns libqtcore4 libqtgui4 libraptor1 librasqal0 librdf0 libruby1.8 libsearchclient0 libsoprano4 libstreamanalyzer0 libstreams0 libstrigihtmlgui0 libstrigiqtdbusclient0 libtunepimp5 libvncserver0 libxcb-shape0 libxcb-shm0 libxcb-xv0 libxine1 libxine1-bin libxine1-console libxine1-misc-plugins libxine1-x libxvmc1 libzip1 mediamanager mysql-common network-manager-kde okular okular-extra-backends openoffice.org-kde openoffice.org-style-crystal oxygen-cursor-theme phonon phonon-backend-gstreamer phonon-backend-xine pinentry-gtk2 pinentry-qt4 plasmoid-quickaccess python-kde4 python-qt3 python-qt4 python-qt4-common python-qt4-dbus python-reportlab python-sip4 qt4-qtconfig raptor-utils redland-utils ruby ruby1.8 software-properties-kde soprano-daemon speedcrunch strigi-client strigi-daemon system-config-printer-kde systemsettings ttf-dustin update-manager-kde update-notifier-kde && sudo apt-get install ubuntu-desktop
```

---

### Post by dragonwolf on 2009-01-06
ty ty guys all were very helpful I now have kubuntu set up the way I want on that HD, BUT I switched to xubuntu as I like the way things are working overall on it much better I know fairweather ubuntu fan huh anyways thankx again for the help and I did learn alot in this phase of my into to ubuntu.

---

### Post by dragonwolf on 2009-01-12
UPDATE- I have gotten all versions of Ubuntu to install on this system using the pci=nomsi switch in the text based install

---

### Post by HotShotDJ on 2009-01-12
> **dragonwolf said:**
> UPDATE- I have gotten all versions of Ubuntu to install on this system using the pci=nomsi switch in the text based installThank you for that update!  Now when others search with the same problem you had, they will know how to fix it.  So many people get things fixed and then don't bother to report back.  Again, thank you.

---

### Post by dragonwolf on 2009-01-12
> **HotShotDJ said:**
> Thank you for that update!  Now when others search with the same problem you had, they will know how to fix it.  So many people get things fixed and then don't bother to report back.  Again, thank you.

Might take me a while to update status's and such but I will always make the attempt as I know how frustrating not finding the answer is so if I can help someone else then so be it!

---

