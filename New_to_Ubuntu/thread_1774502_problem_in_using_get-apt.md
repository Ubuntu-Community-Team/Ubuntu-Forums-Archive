---
title: "problem in using get-apt"
date: 2011-06-03
forum: New to Ubuntu
---

### Post by newlearner1 on 2011-06-03
Hey I am new to ubuntu, I was trying to install some software in ubuntu 11.04 using apt-get for eg VLC by sudo apt-get install vlc but i am gettin the following error. even the update is not working
# apt-get update
Failed to exec method /usr/lib/apt/methods/
Failed to exec method /usr/lib/apt/methods/
E: Method  has died unexpectedly!
E: Sub-process  returned an error code (100)
E: Method /usr/lib/apt/methods/ did not start correctly
E: Method  has died unexpectedly!
E: Sub-process  returned an error code (100)
E: Method /usr/lib/apt/methods/ did not start correctly

My source.list file looks like ....

# deb cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1)]/ natty main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty main restricted #Added by software-properties

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) natty-backports main restricted universe multiverse
# deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) natty-backports main restricted universe multiverse
#############################################################
################### OFFICIAL UBUNTU REPOS ###################
#############################################################

###### Ubuntu Main Repos
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) natty main restricted universe multiverse 
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) natty main restricted universe multiverse 

###### Ubuntu Update Repos
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) natty-security main restricted universe multiverse 
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) natty-updates main restricted universe multiverse 
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) natty-proposed main restricted universe multiverse 
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) natty-backports main restricted universe multiverse 
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) natty-security main restricted universe multiverse 
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) natty-updates main restricted universe multiverse 
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) natty-proposed main restricted universe multiverse 
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) natty-backports main restricted universe multiverse 

###### Ubuntu Partner Repo
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) natty partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) natty partner

##############################################################
##################### UNOFFICIAL  REPOS ######################
##############################################################

###### 3rd Party Binary Repos

## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys     1024R/BB901940
deb [http://ppa.launchpad.net/audacity-team/daily/ubuntu](http://ppa.launchpad.net/audacity-team/daily/ubuntu) natty main  # Audacity - [http://audacity.sourceforge.net/](http://audacity.sourceforge.net/)

## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys BF810CD5
deb [http://ppa.launchpad.net/awn-testing/ppa/ubuntu](http://ppa.launchpad.net/awn-testing/ppa/ubuntu) natty main # AWN (Avant Window Navigator) Testing Packages - [http://awn-project.org/](http://awn-project.org/)

## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 6E80C6B7
deb [http://ppa.launchpad.net/banshee-team/ppa/ubuntu](http://ppa.launchpad.net/banshee-team/ppa/ubuntu) natty main # Banshee - [https://edge.launchpad.net/~banshee-team]("https://edge.launchpad.net/%7Ebanshee-team")

## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 4E5E17B5
deb [http://ppa.launchpad.net/chromium-daily/ppa/ubuntu](http://ppa.launchpad.net/chromium-daily/ppa/ubuntu) natty main # Chromium Project - [http://code.google.com/chromium/](http://code.google.com/chromium/)

## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 3C8E2A7F
deb [http://ppa.launchpad.net/alexey-smirnov/deadbeef/ubuntu](http://ppa.launchpad.net/alexey-smirnov/deadbeef/ubuntu) natty main # DeaDBeeF - [http://deadbeef.sourceforge.net/](http://deadbeef.sourceforge.net/)

## Run this command: wget -q -O - [http://repo.palatinus.cz/repo.key](http://repo.palatinus.cz/repo.key) | sudo apt-key add -
deb [http://repo.palatinus.cz/stable](http://repo.palatinus.cz/stable) /  # Esmska - [http://code.google.com/p/esmska/](http://code.google.com/p/esmska/) 

## Run this command: [http://www.fbreader.org/desktop/debian/geometer.fbreader.org.asc](http://www.fbreader.org/desktop/debian/geometer.fbreader.org.asc) -O- | sudo apt-key add -
deb [http://www.fbreader.org/desktop/debian](http://www.fbreader.org/desktop/debian) stable main  # FBReader - [http://www.fbreader.org/desktop/](http://www.fbreader.org/desktop/)

## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys F2A61FE5
deb [http://ppa.launchpad.net/flacon/ppa/ubuntu](http://ppa.launchpad.net/flacon/ppa/ubuntu) natty main # Flacon - [http://kde-apps.org/content/show.php?content=113388](http://kde-apps.org/content/show.php?content=113388)

## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-key 928EDC6B
deb [http://ppa.launchpad.net/stevi/ppa/ubuntu](http://ppa.launchpad.net/stevi/ppa/ubuntu) natty main # Fritz Fun (ffgtk) - [http://www.tabos.org/ffgtk/index.php](http://www.tabos.org/ffgtk/index.php)

## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 5BE6AD9A
deb [http://ppa.launchpad.net/gcstar/gcstar-dev/ubuntu](http://ppa.launchpad.net/gcstar/gcstar-dev/ubuntu) natty main # GCstar - [http://www.gcstar.org/](http://www.gcstar.org/)

## Run this command: wget -q -O- [http://archive.getdeb.net/getdeb-archive.key](http://archive.getdeb.net/getdeb-archive.key) | sudo apt-key add -
deb [http://archive.getdeb.net/ubuntu](http://archive.getdeb.net/ubuntu) natty-getdeb apps # GetDeb - [http://www.getdeb.net](http://www.getdeb.net)

## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys E80D6BF5
deb [http://ppa.launchpad.net/cairo-dock-team/weekly/ubuntu](http://ppa.launchpad.net/cairo-dock-team/weekly/ubuntu) natty main # Glx-Dock / Cairo-Dock - [http://www.glx-dock.org](http://www.glx-dock.org)

## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 
deb [http://ppa.launchpad.net/gnuzilla-team/ppa/ubuntu](http://ppa.launchpad.net/gnuzilla-team/ppa/ubuntu) natty main   # GNUzilla and IceCat - [http://www.gnu.org/software/gnuzilla/](http://www.gnu.org/software/gnuzilla/)

## Run this command: wget -q [https://dl-ssl.google.com/linux/linux_signing_key.pub](https://dl-ssl.google.com/linux/linux_signing_key.pub) -O- | sudo apt-key add -
deb [http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) stable non-free # Google Linux Software Repositories - [http://www.google.com/linuxrepositories/index.html](http://www.google.com/linuxrepositories/index.html)

## Run this command: wget -q -O - [https://dl-ssl.google.com/linux/linux_signing_key.pub](https://dl-ssl.google.com/linux/linux_signing_key.pub) | sudo apt-key add  -
deb [http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) testing non-free # Google Linux Software Repositories (Testing) - [http://www.google.com/linuxrepositories/index.html](http://www.google.com/linuxrepositories/index.html)

## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 72D340A3
deb [http://ppa.launchpad.net/gwibber-daily/ppa/ubuntu](http://ppa.launchpad.net/gwibber-daily/ppa/ubuntu) natty main # Gwibber (Daily) - [https://launchpad.net/gwibber](https://launchpad.net/gwibber)

## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 816950D8
deb [http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu](http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu) natty main # HandBrake Releases - [http://handbrake.fr/](http://handbrake.fr/)

## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 816950D8
deb [http://ppa.launchpad.net/stebbins/handbrake-snapshots/ubuntu](http://ppa.launchpad.net/stebbins/handbrake-snapshots/ubuntu) natty main # HandBrake Snapshots - [http://handbrake.fr/](http://handbrake.fr/)

## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 8AC93F7A
deb [http://ppa.launchpad.net/kubuntu-ppa/backports/ubuntu](http://ppa.launchpad.net/kubuntu-ppa/backports/ubuntu) natty main # Kubuntu Backports - [https://edge.launchpad.net/~kubuntu-ppa/+archive/backports]("https://edge.launchpad.net/%7Ekubuntu-ppa/+archive/backports")

## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 8AC93F7A
deb [http://ppa.launchpad.net/kubuntu-ppa/beta/ubuntu](http://ppa.launchpad.net/kubuntu-ppa/beta/ubuntu) natty main # Kubuntu Beta Backports - [https://launchpad.net/~kubuntu-ppa/+archive/beta]("https://launchpad.net/%7Ekubuntu-ppa/+archive/beta")

## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 493B3065
deb [http://ppa.launchpad.net/kubuntu-ppa/experimental/ubuntu](http://ppa.launchpad.net/kubuntu-ppa/experimental/ubuntu) natty main # Kubuntu Experimental - [https://launchpad.net/~kubuntu-ppa/+archive/experimental]("https://launchpad.net/%7Ekubuntu-ppa/+archive/experimental")

## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 8AC93F7A
deb [http://ppa.launchpad.net/kubuntu-ppa/ppa/ubuntu](http://ppa.launchpad.net/kubuntu-ppa/ppa/ubuntu) natty main  # Kubuntu Updates - [https://edge.launchpad.net/~kubuntu-ppa/+archive/ppa]("https://edge.launchpad.net/%7Ekubuntu-ppa/+archive/ppa")

## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 1378B444
deb [http://ppa.launchpad.net/libreoffice/ppa/ubuntu](http://ppa.launchpad.net/libreoffice/ppa/ubuntu) natty main # LibreOffice 3.3 - [http://www.documentfoundation.org/download/](http://www.documentfoundation.org/download/)

## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 412F055D
deb [http://ppa.launchpad.net/liferea/liferea-unstable/ubuntu](http://ppa.launchpad.net/liferea/liferea-unstable/ubuntu) natty main # Liferea Unstable - [http://liferea.sourceforge.net/](http://liferea.sourceforge.net/)

## Run this command: sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update 
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) natty free non-free # Medibuntu - [http://www.medibuntu.org/](http://www.medibuntu.org/) 

## Run this command: no gpg keys supplied
deb [http://www.mendeley.com/repositories/xUbuntu_11.04](http://www.mendeley.com/repositories/xUbuntu_11.04) / # Mendeley Desktop - [http://www.mendeley.com/](http://www.mendeley.com/)

## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys A69241F1
deb [http://ppa.launchpad.net/midori/ppa/ubuntu](http://ppa.launchpad.net/midori/ppa/ubuntu) natty main # Midori - [https://launchpad.net/~midori/+archive/ppa]("https://launchpad.net/%7Emidori/+archive/ppa")

## Run this command: wget -q [http://www.bunkus.org/gpg-pub-moritzbunkus.txt](http://www.bunkus.org/gpg-pub-moritzbunkus.txt) -O- | sudo apt-key add -
deb [http://www.bunkus.org/ubuntu/natty/](http://www.bunkus.org/ubuntu/natty/) ./ # MKVToolnix - [http://www.bunkus.org/videotools/mkvtoolnix/](http://www.bunkus.org/videotools/mkvtoolnix/)

## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv 7F0CEB10
deb [http://downloads-distro.mongodb.org/repo/ubuntu-upstart](http://downloads-distro.mongodb.org/repo/ubuntu-upstart) dist 10gen # MongoDB - [http://www.mongodb.org/](http://www.mongodb.org/)

## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys  247510BE
deb [http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu) natty main # Mozilla Daily Build Team - [http://edge.launchpad.net/~ubuntu-mozilla-daily/+archive/ppa]("http://edge.launchpad.net/%7Eubuntu-mozilla-daily/+archive/ppa")

## Run this command: sudo wget -O - [http://apt.mucommander.com/apt.key](http://apt.mucommander.com/apt.key) | sudo apt-key add - 
deb [http://apt.mucommander.com](http://apt.mucommander.com) stable main non-free contrib   # muCommander - [http://www.mucommander.com/](http://www.mucommander.com/)

## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys B9BA26FA
deb [http://ppa.launchpad.net/openshot.developers/ppa/ubuntu](http://ppa.launchpad.net/openshot.developers/ppa/ubuntu) natty main # OpenShot - [http://www.openshotvideo.com](http://www.openshotvideo.com)

## Run this command: sudo wget -O - [http://deb.opera.com/archive.key](http://deb.opera.com/archive.key) | sudo apt-key add -
deb [http://deb.opera.com/opera/](http://deb.opera.com/opera/) lenny non-free # Opera - [http://www.opera.com/](http://www.opera.com/)

## Run this command: sudo wget -O - [http://deb.opera.com/archive.key](http://deb.opera.com/archive.key) | sudo apt-key add -
deb [http://deb.opera.com/opera-beta/](http://deb.opera.com/opera-beta/) lenny non-free # Opera Beta - [http://www.opera.com/](http://www.opera.com/)

## Run this command: wget [http://oss.oracle.com/el4/RPM-GPG-KEY-oracle](http://oss.oracle.com/el4/RPM-GPG-KEY-oracle)  -O- | sudo apt-key add -
deb [http://oss.oracle.com/debian](http://oss.oracle.com/debian) unstable main non-free # Oracle 10g DB - [http://oss.oracle.com](http://oss.oracle.com)

## Run this command: wget -q -O - [http://deb.paissad.net/public-key.asc](http://deb.paissad.net/public-key.asc) | sudo apt-key add -
deb [http://deb.paissad.net](http://deb.paissad.net) unstable main contrib non-free personal # Paissad's Repo - [http://deb.paissad.net](http://deb.paissad.net)

## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys A1F196A8
deb [http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu](http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu) natty main # Pidgin - [http://pidgin.im](http://pidgin.im)

## Run this command: wget -O- [http://archive.getdeb.net/getdeb-archive.key](http://archive.getdeb.net/getdeb-archive.key) | sudo apt-key add -
deb [http://archive.getdeb.net/ubuntu](http://archive.getdeb.net/ubuntu) natty-getdeb games # Playdeb - [http://www.playdeb.net/](http://www.playdeb.net/)

## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 47B4D1C4
deb [http://ppa.launchpad.net/hydr0g3n/ppa/ubuntu](http://ppa.launchpad.net/hydr0g3n/ppa/ubuntu) natty main # qBittorrent - [http://qbittorrent.sourceforge.net/](http://qbittorrent.sourceforge.net/)

## Run this command:  sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 4BB9F05F
deb [http://ppa.launchpad.net/jcfp/ppa/ubuntu](http://ppa.launchpad.net/jcfp/ppa/ubuntu) natty main # SABnzbd - [http://sabnzbd.org/](http://sabnzbd.org/)

## Run this command: gpg --keyserver subkeys.pgp.net --recv 886DDD89 && gpg --export --armor 94C09C7F  | sudo apt-key add -
deb [http://deb.torproject.org/torproject.org](http://deb.torproject.org/torproject.org) lucid main # Tor: anonymity online - [http://www.torproject.org/](http://www.torproject.org/)

## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 0624A220
deb [http://ppa.launchpad.net/tualatrix/ubuntu](http://ppa.launchpad.net/tualatrix/ubuntu) natty main # Ubuntu Tweak - [http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)

## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys FC91AE7E
deb [http://ppa.launchpad.net/gezakovacs/ppa/ubuntu](http://ppa.launchpad.net/gezakovacs/ppa/ubuntu) natty main # UNetbootin - [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

## Run this command: wget -q [http://download.virtualbox.org/virtualbox/debian/oracle_vbox.asc](http://download.virtualbox.org/virtualbox/debian/oracle_vbox.asc) -O- | sudo apt-key add -
deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) natty contrib # VirtualBox - [http://www.virtualbox.org](http://www.virtualbox.org)

## Run this command: sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 40130828
deb [http://ppa.launchpad.net/c-korn/ppa/ubuntu](http://ppa.launchpad.net/c-korn/ppa/ubuntu) maverick main  # VLC Media Player  - [http://www.videolan.org/vlc/](http://www.videolan.org/vlc/)

## Run this command: wget [http://www.webmin.com/jcameron-key.asc](http://www.webmin.com/jcameron-key.asc) -O- | sudo apt-key add -
deb [http://download.webmin.com/download/repository](http://download.webmin.com/download/repository) sarge contrib # Webmin - [http://www.webmin.com](http://www.webmin.com)

## Run this command:  sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys F9CB8DB0
deb [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu) natty main # Wine - [https://launchpad.net/~ubuntu-wine/+archive/ppa/]("https://launchpad.net/%7Eubuntu-wine/+archive/ppa/")

## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys AF1CDFA9
deb [http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu](http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu) natty main # X Updates - [https://launchpad.net/~ubuntu-x-swat/+archive/x-updates/]("https://launchpad.net/%7Eubuntu-x-swat/+archive/x-updates/")

## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 8844C542  
deb [http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu](http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu) natty main # Xorg Edgers - [https://launchpad.net/~xorg-edgers]("https://launchpad.net/%7Exorg-edgers")

deb [http://update.yuuguu.com/repositories/apt](http://update.yuuguu.com/repositories/apt) hardy multiverse # Yuuguu - [http://yuuguu.com](http://yuuguu.com)


####### 3rd Party Source Repos

## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys     1024R/BB901940
deb-src [http://ppa.launchpad.net/audacity-team/daily/ubuntu](http://ppa.launchpad.net/audacity-team/daily/ubuntu) natty main  # Audacity (Source) - [http://audacity.sourceforge.net/](http://audacity.sourceforge.net/)

## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys BF810CD5
deb-src [http://ppa.launchpad.net/awn-testing/ppa/ubuntu](http://ppa.launchpad.net/awn-testing/ppa/ubuntu) natty main # AWN (Avant Window Navigator) Testing Packages (Source) - [http://awn-project.org/](http://awn-project.org/)

## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 6E80C6B7
deb-src [http://ppa.launchpad.net/banshee-team/ppa/ubuntu](http://ppa.launchpad.net/banshee-team/ppa/ubuntu) natty main # Banshee (Source) - [https://edge.launchpad.net/~banshee-team]("https://edge.launchpad.net/%7Ebanshee-team")

## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 4E5E17B5
deb-src [http://ppa.launchpad.net/chromium-daily/ppa/ubuntu](http://ppa.launchpad.net/chromium-daily/ppa/ubuntu) natty main # Chromium Project (Source) - [http://code.google.com/chromium/](http://code.google.com/chromium/)

## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 3C8E2A7F
deb-src [http://ppa.launchpad.net/alexey-smirnov/deadbeef/ubuntu](http://ppa.launchpad.net/alexey-smirnov/deadbeef/ubuntu) natty main # DeaDBeeF (Source) - [http://deadbeef.sourceforge.net/](http://deadbeef.sourceforge.net/)

## Run this command: [http://www.fbreader.org/desktop/debian/geometer.fbreader.org.asc](http://www.fbreader.org/desktop/debian/geometer.fbreader.org.asc) -O- | sudo apt-key add -
deb-src [http://www.fbreader.org/desktop/debian](http://www.fbreader.org/desktop/debian) stable main  # FBReader (Source) - [http://www.fbreader.org/desktop/](http://www.fbreader.org/desktop/)

## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys F2A61FE5
deb-src [http://ppa.launchpad.net/flacon/ppa/ubuntu](http://ppa.launchpad.net/flacon/ppa/ubuntu) natty main # Flacon (Source) - [http://kde-apps.org/content/show.php?content=113388](http://kde-apps.org/content/show.php?content=113388)

## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-key 928EDC6B
deb-src [http://ppa.launchpad.net/stevi/ppa/ubuntu](http://ppa.launchpad.net/stevi/ppa/ubuntu) natty main # Fritz Fun (ffgtk) (Source) - [http://www.tabos.org/ffgtk/index.php](http://www.tabos.org/ffgtk/index.php)

## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 5BE6AD9A
deb-src [http://ppa.launchpad.net/gcstar/gcstar-dev/ubuntu](http://ppa.launchpad.net/gcstar/gcstar-dev/ubuntu) natty main # GCstar (Source) - [http://www.gcstar.org/](http://www.gcstar.org/)

## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys E80D6BF5
deb-src [http://ppa.launchpad.net/cairo-dock-team/weekly/ubuntu](http://ppa.launchpad.net/cairo-dock-team/weekly/ubuntu) natty main # Glx-Dock / Cairo-Dock (Source) - [http://www.glx-dock.org](http://www.glx-dock.org)

## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 
deb-src [http://ppa.launchpad.net/gnuzilla-team/ppa/ubuntu](http://ppa.launchpad.net/gnuzilla-team/ppa/ubuntu) natty main   # GNUzilla and IceCat (Source) - [http://www.gnu.org/software/gnuzilla/](http://www.gnu.org/software/gnuzilla/)

## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 72D340A3
deb-src [http://ppa.launchpad.net/gwibber-daily/ppa/ubuntu](http://ppa.launchpad.net/gwibber-daily/ppa/ubuntu) natty main # Gwibber (Daily) (Source) - [https://launchpad.net/gwibber](https://launchpad.net/gwibber)

## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 816950D8
deb-src [http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu](http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu) natty main # HandBrake Releases (Source) - [http://handbrake.fr/](http://handbrake.fr/)

## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 816950D8
deb-src [http://ppa.launchpad.net/stebbins/handbrake-snapshots/ubuntu](http://ppa.launchpad.net/stebbins/handbrake-snapshots/ubuntu) natty main # HandBrake Snapshots (Source) - [http://handbrake.fr/](http://handbrake.fr/)

## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 8AC93F7A
deb-src [http://ppa.launchpad.net/kubuntu-ppa/backports/ubuntu](http://ppa.launchpad.net/kubuntu-ppa/backports/ubuntu) natty main # Kubuntu Backports (Source) - [https://edge.launchpad.net/~kubuntu-ppa/+archive/backports]("https://edge.launchpad.net/%7Ekubuntu-ppa/+archive/backports")

## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 8AC93F7A
deb-src [http://ppa.launchpad.net/kubuntu-ppa/beta/ubuntu](http://ppa.launchpad.net/kubuntu-ppa/beta/ubuntu) natty main # Kubuntu Beta Backports (Source) - [https://launchpad.net/~kubuntu-ppa/+archive/beta]("https://launchpad.net/%7Ekubuntu-ppa/+archive/beta")

## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 493B3065
deb-src [http://ppa.launchpad.net/kubuntu-ppa/experimental/ubuntu](http://ppa.launchpad.net/kubuntu-ppa/experimental/ubuntu) natty main # Kubuntu Experimental (Source) - [https://launchpad.net/~kubuntu-ppa/+archive/experimental]("https://launchpad.net/%7Ekubuntu-ppa/+archive/experimental")

## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 8AC93F7A
deb-src [http://ppa.launchpad.net/kubuntu-ppa/ppa/ubuntu](http://ppa.launchpad.net/kubuntu-ppa/ppa/ubuntu) natty main  # Kubuntu Updates (Source) - [https://edge.launchpad.net/~kubuntu-ppa/+archive/ppa]("https://edge.launchpad.net/%7Ekubuntu-ppa/+archive/ppa")

## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 1378B444
deb-src [http://ppa.launchpad.net/libreoffice/ppa/ubuntu](http://ppa.launchpad.net/libreoffice/ppa/ubuntu) natty main # LibreOffice 3.3 (Source) - [http://www.documentfoundation.org/download/](http://www.documentfoundation.org/download/)

## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 412F055D
deb-src [http://ppa.launchpad.net/liferea/liferea-unstable/ubuntu](http://ppa.launchpad.net/liferea/liferea-unstable/ubuntu) natty main # Liferea Unstable (Source) - [http://liferea.sourceforge.net/](http://liferea.sourceforge.net/)

## Run this command: sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update 
deb-src [http://packages.medibuntu.org/](http://packages.medibuntu.org/) natty free non-free # Medibuntu (Source) - [http://www.medibuntu.org/](http://www.medibuntu.org/) 

## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys A69241F1
deb-src [http://ppa.launchpad.net/midori/ppa/ubuntu](http://ppa.launchpad.net/midori/ppa/ubuntu) natty main # Midori (Source) - [https://launchpad.net/~midori/+archive/ppa]("https://launchpad.net/%7Emidori/+archive/ppa")

## Run this command: wget -q [http://www.bunkus.org/gpg-pub-moritzbunkus.txt](http://www.bunkus.org/gpg-pub-moritzbunkus.txt) -O- | sudo apt-key add -
deb-src [http://www.bunkus.org/ubuntu/natty/](http://www.bunkus.org/ubuntu/natty/) ./  # MKVToolnix (Source) - [http://www.bunkus.org/videotools/mkvtoolnix/](http://www.bunkus.org/videotools/mkvtoolnix/)

## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys  247510BE
deb-src [http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu) natty main # Mozilla Daily Build Team (Source) - [http://edge.launchpad.net/~ubuntu-mozilla-daily/+archive/ppa]("http://edge.launchpad.net/%7Eubuntu-mozilla-daily/+archive/ppa")

## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys B9BA26FA
deb-src [http://ppa.launchpad.net/openshot.developers/ppa/ubuntu](http://ppa.launchpad.net/openshot.developers/ppa/ubuntu) natty main # OpenShot (Source) - [http://www.openshotvideo.com](http://www.openshotvideo.com)

## Run this command: wget -q -O - [http://deb.paissad.net/public-key.asc](http://deb.paissad.net/public-key.asc) | sudo apt-key add -
deb-src [http://deb.paissad.net](http://deb.paissad.net) unstable main contrib non-free personal # Paissad's Repo (Source) - [http://deb.paissad.net](http://deb.paissad.net)

## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys A1F196A8
deb-src [http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu](http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu) natty main # Pidgin (Source) - [http://pidgin.im](http://pidgin.im)

## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 47B4D1C4
deb-src [http://ppa.launchpad.net/hydr0g3n/ppa/ubuntu](http://ppa.launchpad.net/hydr0g3n/ppa/ubuntu) natty main # qBittorrent (Source) - [http://qbittorrent.sourceforge.net/](http://qbittorrent.sourceforge.net/)

## Run this command: gpg --keyserver subkeys.pgp.net --recv 886DDD89 && gpg --export --armor 94C09C7F  | sudo apt-key add -
deb-src [http://deb.torproject.org/torproject.org](http://deb.torproject.org/torproject.org) lucid main # Tor: anonymity online (Source) - [http://www.torproject.org/](http://www.torproject.org/)

## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 0624A220
deb-src [http://ppa.launchpad.net/tualatrix/ubuntu](http://ppa.launchpad.net/tualatrix/ubuntu) natty main # Ubuntu Tweak (Source) - [http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)

## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys FC91AE7E
deb-src [http://ppa.launchpad.net/gezakovacs/ppa/ubuntu](http://ppa.launchpad.net/gezakovacs/ppa/ubuntu) natty main # UNetbootin (Source) - [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

## Run this command: sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 40130828
deb-src [http://ppa.launchpad.net/c-korn/ppa/ubuntu](http://ppa.launchpad.net/c-korn/ppa/ubuntu) maverick main # VLC Media Player  (Source) - [http://www.videolan.org/vlc/](http://www.videolan.org/vlc/)

## Run this command:  sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys F9CB8DB0
deb-src [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu) natty main  # Wine (Source) - [https://launchpad.net/~ubuntu-wine/+archive/ppa/]("https://launchpad.net/%7Eubuntu-wine/+archive/ppa/")

## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys AF1CDFA9
deb-src [http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu](http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu) natty main # X Updates (Source) - [https://launchpad.net/~ubuntu-x-swat/+archive/x-updates/]("https://launchpad.net/%7Eubuntu-x-swat/+archive/x-updates/")

## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 8844C542  
deb-src [http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu](http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu) natty main # Xorg Edgers (Source) - [https://launchpad.net/~xorg-edgers]("https://launchpad.net/%7Exorg-edgers")




deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty-security main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty-security restricted main multiverse universe #Added by software-properties
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty-security universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
 deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) natty partner
 deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) natty partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) natty main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) natty main
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main multiverse

    #

    # deb cdrom:[Debian GNU/Linux 6.0.0 _Squeeze_ - Official amd64 DVD Binary-1 20110205-18:15]/ squeeze contrib main

    # deb cdrom:[Debian GNU/Linux 6.0.0 _Squeeze_ - Official amd64 DVD Binary-1 20110205-18:15]/ squeeze contrib main

    deb [http://ftp.us.debian.org/debian/](http://ftp.us.debian.org/debian/) squeeze main non-free contrib
    deb-src [http://ftp.us.debian.org/debian/](http://ftp.us.debian.org/debian/) squeeze main non-free contrib #Added by software-properties

    deb [http://security.debian.org/](http://security.debian.org/) squeeze/updates main contrib non-free
    deb-src [http://security.debian.org/](http://security.debian.org/) squeeze/updates main contrib non-free #Added by software-properties

    deb [http://ftp.us.debian.org/debian/](http://ftp.us.debian.org/debian/) squeeze-updates main contrib non-free
    deb-src [http://ftp.us.debian.org/debian/](http://ftp.us.debian.org/debian/) squeeze-updates main contrib non-free






Please please help..i have already wasted many days struggling this problem...Thanx in advance

---

### Post by coffeecat on 2011-06-03
Welcome to the forum.

I don't know why you are getting that error, but I am not surprised you are getting some sort of error when trying to update. You have enabled the backports and proposed repositories and I lost count of how many 3rd party repositories.

Let me introduce you to what the Ubuntu community documentation says about the proposed repository. This page:

[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

> This repository is recommended only to those interested in helping to test updates and provide feedback.As someone "new to Ubuntu" you should not be using it. This page's comment is stronger:

[https://help.ubuntu.com/community/UbuntuUpdates](https://help.ubuntu.com/community/UbuntuUpdates)

> Enabling the proposed updates repository can break your system. It is not recommended for inexperienced users.So what about the 3rd party repositories? The potential for conflicts and breakages by enabling so many  non-official repositories would be enormous, I would think. See what others recommend, but I suggest you start over with a fresh installation and enable only those repositories that you **need**, rather than those that look vaguely interesting.

I am very reluctant to suggest re-installing to anyone. Most broken systems are repairable but I think you may well have broken not just a system, but some sort of record with so many 3rd party repos. :-s

I say all this with kind intentions. :) Good luck! :wink:

---

### Post by Joe of loath on 2011-06-03
Why do you have the debian repos at the end of your sources.list file?

---

### Post by Rubi1200 on 2011-06-03
I am not normally a big fan of suggesting a reinstall, but sometimes it is necessary. 

I agree with coffeecat about not enabling the proposed repository and you should probably also avoid backports. As far as 3rd party repos are concerned, this is always a potential security risk unless you are absolutely sure about the source.

In any event, in an attempt to try and fix this before you consider reinstalling, please run the following commands:

```
sudo apt-get autoremove

sudo apt-get update
```

If this doesn't work from within Ubuntu, you may need to use a LiveCD and chroot into the system to do this.

But, first things first.

---

### Post by jimwatson on 2011-06-17
Hi,

I had a similar problem a couple of days ago with a fairly standard install of 11.04 (I'd not enabled any other repos or modified sources.list in any way, the only additional repos on my machine are associated with dropbox and google chrome in the sources subdirectory). Synaptic was set up to use my local server (Saudi Arabia) and I see that you're using the Indian servers - switching to the 'main' server and reloading fixed the problem for me.

jim

---

### Post by arpit22x on 2011-06-26
I also had this problem but I uncheck both 'proposed' and 'backports' updates from software sources and reloaded. This solved my problem.

---

### Post by sagar13 on 2012-11-07
You might find this a pain to debug. There are a few things that seem to cause this problem: (2nd point worked for me)

  
[LIST]
[*]corrupt sources.list entry, you have an entry in your sources.list file (or a file included from sources.list.d) which contains a deb or deb-src  line which has a malformed uri method (see sources.list(5) for a list  of valid methods) or is just an incorrect entry. Fix the malformed  entry, run apt-get update and then all should be well.
[*]corrupt entry in /var/lib/apt/lists - if your sources.list  files are ok, you may have a corrupt entry in one of the lists that  have been downloaded. To resolve this you can backup the files  somewhere,  remove the existing files, and then run apt-get update, it’ll download a new set of lists. You then should be able to install/update packages.
[/LIST]


courtesy: [http://blog.vicecity.co.uk/post/27117588816/apt-get-update-failing-with-method-died-error](http://blog.vicecity.co.uk/post/27117588816/apt-get-update-failing-with-method-died-error)

---

### Post by coffeecat on 2012-11-07
Old thread - closed.

---

