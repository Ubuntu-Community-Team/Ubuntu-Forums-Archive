---
title: "Update Screwed Up Everything"
date: 2009-03-25
forum: New to Ubuntu
---

### Post by Canuck90 on 2009-03-25
Todau, I was prompted for an update, so I clicked on it, it took about 2 hours for it to complete. After restarting once the update was complete, everything has not been working properly, programs won't load, the back button doesn't work in firefox, music in amarok stops playing, all my bookmarks aren't visible, it's a real pain. If it weren't for previous problems that won't allow me to mount my partition containing Windows, I would switch back right now. Any ideas on what I can do to fix this. A system restore would be nice. I think after this latest batch of problems I'll be heading back to Windows on my next computer.

---

### Post by utnubuuser on 2009-03-25
have you tried > sudo dpkg --configure -ain a terminal?

---

### Post by 123456789123456789123456 on 2009-03-25
sounds like a configuration error of some sort.  was the updates normal security updats, or was it a distribution upgrade, like 8.04 to 8.10?  I had a simular problem a while back when I tried to upgrade from 7.04 to 7.10 on a computer I was using for the church.  It had some sort of problems, and the computer was completely screwed up after the upgrade, I had to restore the entire computer to get it working properly.  I know sometimes that interuption in the internet connection while installing/downloading the updates can cause problems.  Please check the install log/update log of the update manager.  Send us the contents, that way we can see if any of the updates did not configure correctly.  We could be better equiped to help you, knowing all bases.

---

### Post by 3rdalbum on 2009-03-25
Go into Synaptic Package Manager and File > History to see what packages you last installed. When you find something that is likely to have caused the problem, do a "find" for it, click on it, and go to Package > Force Version and force the version that you upgraded from.

I haven't had any updates pushed to me lately except in the Proposed repository today. The Proposed repository is only for testing new packages before they get pushed to everybody. If you can't handle possible breakage, then disable the Proposed repository in Software Sources.

---

### Post by Canuck90 on 2009-03-25
I tried the first thing recommended, didn't change anything. I did have some internet connectivity problems today, so that could be the cause. Here is what was upgraded (or should have been):

Commit Log for Wed Mar 25 18:14:03 2009


Upgraded the following packages:
acpi-support (0.109) to 0.109-0hardy2
acpid (1.0.4-5ubuntu9) to 1.0.4-5ubuntu9.1
amarok (2:1.4.9.1-0ubuntu3.1+medibuntu1) to 2:1.4.9.1-0ubuntu3.2
amarok-xine (2:1.4.9.1-0ubuntu3.1+medibuntu1) to 2:1.4.9.1-0ubuntu3.2
app-install-data-commercial (9.3) to 9.4
avahi-autoipd (0.6.22-2ubuntu4) to 0.6.22-2ubuntu4.1
avahi-daemon (0.6.22-2ubuntu4) to 0.6.22-2ubuntu4.1
base-files (4.0.1ubuntu5.8.04.3) to 4.0.1ubuntu5.8.04.4
bind9-host (1:9.4.2.dfsg.P2-2) to 1:9.4.2.dfsg.P2-2ubuntu0.1
bsdutils (1:2.13.1-5ubuntu2) to 1:2.13.1-5ubuntu3
compiz-fusion-plugins-main (0.7.4-0ubuntu6) to 0.7.4-0ubuntu6.2
console-setup (1.21ubuntu8) to 1.21ubuntu9
cupsys (1.3.7-1ubuntu3.1) to 1.3.7-1ubuntu3.3
cupsys-bsd (1.3.7-1ubuntu3.1) to 1.3.7-1ubuntu3.3
cupsys-client (1.3.7-1ubuntu3.1) to 1.3.7-1ubuntu3.3
cupsys-common (1.3.7-1ubuntu3.1) to 1.3.7-1ubuntu3.3
dash (0.5.4-8ubuntu1) to 0.5.4-8ubuntu1.1
dnsutils (1:9.4.2.dfsg.P2-2) to 1:9.4.2.dfsg.P2-2ubuntu0.1
evolution-data-server (2.22.3-0ubuntu2) to 2.22.3-0ubuntu3
evolution-data-server-common (2.22.3-0ubuntu2) to 2.22.3-0ubuntu3
ffmpeg (3:0.cvs20070307-5ubuntu7.1+medibuntu1) to 3:0.cvs20070307-5ubuntu7.3+medibuntu1
fglrx-control (1:8-3+2.6.24.14-21.51) to 1:8-3+2.6.24.16-23.56
firefox (3.0.3+build1+nobinonly-0ubuntu0.8.04.1) to 3.0.7+nobinonly-0ubuntu0.8.04.1
firefox-3.0 (3.0.3+build1+nobinonly-0ubuntu0.8.04.1) to 3.0.7+nobinonly-0ubuntu0.8.04.1
firefox-3.0-gnome-support (3.0.3+build1+nobinonly-0ubuntu0.8.04.1) to 3.0.7+nobinonly-0ubuntu0.8.04.1
firefox-gnome-support (3.0.3+build1+nobinonly-0ubuntu0.8.04.1) to 3.0.7+nobinonly-0ubuntu0.8.04.1
gedit (2.22.3-0ubuntu1) to 2.22.3-0ubuntu2
gedit-common (2.22.3-0ubuntu1) to 2.22.3-0ubuntu2
ghostscript (8.61.dfsg.1-1ubuntu3) to 8.61.dfsg.1-1ubuntu3.1
ghostscript-x (8.61.dfsg.1-1ubuntu3) to 8.61.dfsg.1-1ubuntu3.1
gksu (2.0.0-5ubuntu3) to 2.0.0-5ubuntu3.8.04.1
gnome-power-manager (2.22.1-1ubuntu4) to 2.22.1-1ubuntu4.1
grub (0.97-29ubuntu21) to 0.97-29ubuntu21.1
gstreamer0.10-plugins-good (0.10.7-3ubuntu0.1) to 0.10.7-3ubuntu0.2
guidance-backends (0.8.0svn20080103-0ubuntu16.1) to 0.8.0svn20080103-0ubuntu16.2
hal-info (20081001-0ubuntu1~hardy1) to 20090128-0ubuntu1~hardy2
hpijs (2.8.2+2.8.2-0ubuntu8) to 2.8.2+2.8.2-0ubuntu8.1
hplip (2.8.2-0ubuntu8) to 2.8.2-0ubuntu8.1
hplip-data (2.8.2-0ubuntu8) to 2.8.2-0ubuntu8.1
initramfs-tools (0.85eubuntu39.2) to 0.85eubuntu39.3
initscripts (2.86.ds1-14.1ubuntu45) to 2.86.ds1-14.1ubuntu45.1
jockey-common (0.3.3-0ubuntu8.1) to 0.3.3-0ubuntu8.2
jockey-gtk (0.3.3-0ubuntu8.1) to 0.3.3-0ubuntu8.2
kdelibs-data (4:3.5.10-0ubuntu1~hardy1) to 4:3.5.10-0ubuntu1~hardy1.1
kdelibs4c2a (4:3.5.10-0ubuntu1~hardy1) to 4:3.5.10-0ubuntu1~hardy1.1
language-pack-en (1:8.04+20080805) to 1:8.04+20090105.1
language-pack-en-base (1:8.04+20080527) to 1:8.04+20090105
language-pack-gnome-en (1:8.04+20080805) to 1:8.04+20090105.1
language-pack-gnome-en-base (1:8.04+20080527) to 1:8.04+20090105
libavahi-client3 (0.6.22-2ubuntu4) to 0.6.22-2ubuntu4.1
libavahi-common-data (0.6.22-2ubuntu4) to 0.6.22-2ubuntu4.1
libavahi-common3 (0.6.22-2ubuntu4) to 0.6.22-2ubuntu4.1
libavahi-compat-libdnssd1 (0.6.22-2ubuntu4) to 0.6.22-2ubuntu4.1
libavahi-core5 (0.6.22-2ubuntu4) to 0.6.22-2ubuntu4.1
libavahi-glib1 (0.6.22-2ubuntu4) to 0.6.22-2ubuntu4.1
libavahi-qt3-1 (0.6.22-2ubuntu4) to 0.6.22-2ubuntu4.1
libavahi-ui0 (0.6.22-2ubuntu4) to 0.6.22-2ubuntu4.1
libavcodec-dev (3:0.cvs20070307-5ubuntu7.1+medibuntu1) to 3:0.cvs20070307-5ubuntu7.3+medibuntu1
libavcodec1d (3:0.cvs20070307-5ubuntu7.1+medibuntu1) to 3:0.cvs20070307-5ubuntu7.3+medibuntu1
libavformat-dev (3:0.cvs20070307-5ubuntu7.1+medibuntu1) to 3:0.cvs20070307-5ubuntu7.3+medibuntu1
libavformat1d (3:0.cvs20070307-5ubuntu7.1+medibuntu1) to 3:0.cvs20070307-5ubuntu7.3+medibuntu1
libavutil-dev (3:0.cvs20070307-5ubuntu7.1+medibuntu1) to 3:0.cvs20070307-5ubuntu7.3+medibuntu1
libavutil1d (3:0.cvs20070307-5ubuntu7.1+medibuntu1) to 3:0.cvs20070307-5ubuntu7.3+medibuntu1
libbind9-30 (1:9.4.2.dfsg.P2-2) to 1:9.4.2.dfsg.P2-2ubuntu0.1
libcamel1.2-11 (2.22.3-0ubuntu2) to 2.22.3-0ubuntu3
libcupsimage2 (1.3.7-1ubuntu3.1) to 1.3.7-1ubuntu3.3
libcupsys2 (1.3.7-1ubuntu3.1) to 1.3.7-1ubuntu3.3
libcupsys2-dev (1.3.7-1ubuntu3.1) to 1.3.7-1ubuntu3.3
libcurl3 (7.18.0-1ubuntu2) to 7.18.0-1ubuntu2.1
libcurl3-gnutls (7.18.0-1ubuntu2) to 7.18.0-1ubuntu2.1
libdns35 (1:9.4.2.dfsg.P2-2) to 1:9.4.2.dfsg.P2-2ubuntu0.1
libebook1.2-9 (2.22.3-0ubuntu2) to 2.22.3-0ubuntu3
libecal1.2-7 (2.22.3-0ubuntu2) to 2.22.3-0ubuntu3
libedata-book1.2-2 (2.22.3-0ubuntu2) to 2.22.3-0ubuntu3
libedata-cal1.2-6 (2.22.3-0ubuntu2) to 2.22.3-0ubuntu3
libedataserver1.2-9 (2.22.3-0ubuntu2) to 2.22.3-0ubuntu3
libedataserverui1.2-8 (2.22.3-0ubuntu2) to 2.22.3-0ubuntu3
libegroupwise1.2-13 (2.22.3-0ubuntu2) to 2.22.3-0ubuntu3
libexchange-storage1.2-3 (2.22.3-0ubuntu2) to 2.22.3-0ubuntu3
libgadu3 (1:1.7~rc2-2) to 1:1.7~rc2-2ubuntu0.8.04.1
libgdata-google1.2-1 (2.22.3-0ubuntu2) to 2.22.3-0ubuntu3
libgdata1.2-1 (2.22.3-0ubuntu2) to 2.22.3-0ubuntu3
libglib2.0-0 (2.16.6-0ubuntu1) to 2.16.6-0ubuntu1.1
libgnutls-dev (2.0.4-1ubuntu2.1) to 2.0.4-1ubuntu2.3
libgnutls13 (2.0.4-1ubuntu2.1) to 2.0.4-1ubuntu2.3
libgnutlsxx13 (2.0.4-1ubuntu2.1) to 2.0.4-1ubuntu2.3
libgs8 (8.61.dfsg.1-1ubuntu3) to 8.61.dfsg.1-1ubuntu3.1
libisc35 (1:9.4.2.dfsg.P2-2) to 1:9.4.2.dfsg.P2-2ubuntu0.1
libisccc30 (1:9.4.2.dfsg.P2-2) to 1:9.4.2.dfsg.P2-2ubuntu0.1
libisccfg30 (1:9.4.2.dfsg.P2-2) to 1:9.4.2.dfsg.P2-2ubuntu0.1
libjasper1 (1.900.1-3) to 1.900.1-3ubuntu0.8.04.1
liblcms1 (1.16-7ubuntu1) to 1.16-7ubuntu1.2
liblcms1-dev (1.16-7ubuntu1) to 1.16-7ubuntu1.2
libldap-2.4-2 (2.4.9-0ubuntu0.8.04.1) to 2.4.9-0ubuntu0.8.04.2
liblwres30 (1:9.4.2.dfsg.P2-2) to 1:9.4.2.dfsg.P2-2ubuntu0.1
libmysqlclient15off (5.0.51a-3ubuntu5.3) to 5.0.51a-3ubuntu5.4
libnm-glib0 (0.6.6-0ubuntu5) to 0.6.6-0ubuntu5.8.04.1
libnm-util0 (0.6.6-0ubuntu5) to 0.6.6-0ubuntu5.8.04.1
libnss3-1d (3.12.0.3-0ubuntu0.8.04.4) to 3.12.0.3-0ubuntu0.8.04.5
libntfs-3g23 (1:1.2216-1ubuntu2) to 1:1.2216-1ubuntu3
libperl5.8 (5.8.8-12) to 5.8.8-12ubuntu0.4
libpng12-0 (1.2.15~beta5-3) to 1.2.15~beta5-3ubuntu0.1
libpng12-dev (1.2.15~beta5-3) to 1.2.15~beta5-3ubuntu0.1
libpostproc1d (3:0.cvs20070307-5ubuntu7.1+medibuntu1) to 3:0.cvs20070307-5ubuntu7.3+medibuntu1
libpq5 (8.3.3-0ubuntu0.8.04) to 8.3.6-0ubuntu8.04
libpurple0 (1:2.4.1-1ubuntu2.1) to 1:2.4.1-1ubuntu2.3
libsnmp-base (5.4.1~dfsg-4ubuntu4) to 5.4.1~dfsg-4ubuntu4.2
libsnmp15 (5.4.1~dfsg-4ubuntu4) to 5.4.1~dfsg-4ubuntu4.2
libssl0.9.8 (0.9.8g-4ubuntu3.3) to 0.9.8g-4ubuntu3.4
libswscale1d (3:0.cvs20070307-5ubuntu7.1+medibuntu1) to 3:0.cvs20070307-5ubuntu7.3+medibuntu1
libxine1 (1.1.11.1-1ubuntu3.1) to 1.1.11.1-1ubuntu3.2
libxine1-bin (1.1.11.1-1ubuntu3.1) to 1.1.11.1-1ubuntu3.2
libxine1-console (1.1.11.1-1ubuntu3.1) to 1.1.11.1-1ubuntu3.2
libxine1-ffmpeg (1.1.11.1-1ubuntu3.1) to 1.1.11.1-1ubuntu3.2
libxine1-misc-plugins (1.1.11.1-1ubuntu3.1) to 1.1.11.1-1ubuntu3.2
libxine1-plugins (1.1.11.1-1ubuntu3.1) to 1.1.11.1-1ubuntu3.2
libxine1-x (1.1.11.1-1ubuntu3.1) to 1.1.11.1-1ubuntu3.2
libxml2 (2.6.31.dfsg-2ubuntu1.2) to 2.6.31.dfsg-2ubuntu1.3
libxml2-utils (2.6.31.dfsg-2ubuntu1.2) to 2.6.31.dfsg-2ubuntu1.3
linux-generic (2.6.24.21.23) to 2.6.24.23.25
linux-headers-generic (2.6.24.21.23) to 2.6.24.23.25
linux-image-generic (2.6.24.21.23) to 2.6.24.23.25
linux-libc-dev (2.6.24-21.43) to 2.6.24-23.48
linux-restricted-modules-common (2.6.24.14-21.51) to 2.6.24.16-23.56
linux-restricted-modules-generic (2.6.24.21.23) to 2.6.24.23.25
login (1:4.0.18.2-1ubuntu2.1) to 1:4.0.18.2-1ubuntu2.2
mount (2.13.1-5ubuntu2) to 2.13.1-5ubuntu3
myspell-en-gb (1:2.4.0~m240-1ubuntu1) to 1:2.4.0~m240-1ubuntu1.1
myspell-en-us (1:2.4.0~m240-1ubuntu1) to 1:2.4.0~m240-1ubuntu1.1
myspell-en-za (1:2.4.0~m240-1ubuntu1) to 1:2.4.0~m240-1ubuntu1.1
mysql-common (5.0.51a-3ubuntu5.3) to 5.0.51a-3ubuntu5.4
nautilus-share (0.7.2-0ubuntu5) to 0.7.2-0ubuntu5.1
network-manager (0.6.6-0ubuntu5) to 0.6.6-0ubuntu5.8.04.1
network-manager-gnome (0.6.6-0ubuntu3) to 0.6.6-0ubuntu3.1
ntfs-3g (1:1.2216-1ubuntu2) to 1:1.2216-1ubuntu3
ntpdate (1:4.2.4p4+dfsg-3ubuntu2) to 1:4.2.4p4+dfsg-3ubuntu2.1
openoffice.org-base-core (1:2.4.1-1ubuntu2) to 1:2.4.1-1ubuntu2.1
openoffice.org-calc (1:2.4.1-1ubuntu2) to 1:2.4.1-1ubuntu2.1
openoffice.org-common (1:2.4.1-1ubuntu2) to 1:2.4.1-1ubuntu2.1
openoffice.org-core (1:2.4.1-1ubuntu2) to 1:2.4.1-1ubuntu2.1
openoffice.org-draw (1:2.4.1-1ubuntu2) to 1:2.4.1-1ubuntu2.1
openoffice.org-gnome (1:2.4.1-1ubuntu2) to 1:2.4.1-1ubuntu2.1
openoffice.org-gtk (1:2.4.1-1ubuntu2) to 1:2.4.1-1ubuntu2.1
openoffice.org-help-en-gb (1:2.4.1-1ubuntu2) to 1:2.4.1-1ubuntu2.1
openoffice.org-help-en-us (1:2.4.1-1ubuntu2) to 1:2.4.1-1ubuntu2.1
openoffice.org-impress (1:2.4.1-1ubuntu2) to 1:2.4.1-1ubuntu2.1
openoffice.org-l10n-common (1:2.4.1-1ubuntu2) to 1:2.4.1-1ubuntu2.1
openoffice.org-l10n-en-gb (1:2.4.1-1ubuntu2) to 1:2.4.1-1ubuntu2.1
openoffice.org-l10n-en-za (1:2.4.1-1ubuntu2) to 1:2.4.1-1ubuntu2.1
openoffice.org-style-human (1:2.4.1-1ubuntu2) to 1:2.4.1-1ubuntu2.1
openoffice.org-thesaurus-en-us (1:2.4.0~m240-1ubuntu1) to 1:2.4.0~m240-1ubuntu1.1
openoffice.org-writer (1:2.4.1-1ubuntu2) to 1:2.4.1-1ubuntu2.1
openssl (0.9.8g-4ubuntu3.3) to 0.9.8g-4ubuntu3.4
passwd (1:4.0.18.2-1ubuntu2.1) to 1:4.0.18.2-1ubuntu2.2
perl (5.8.8-12) to 5.8.8-12ubuntu0.4
perl-base (5.8.8-12) to 5.8.8-12ubuntu0.4
perl-modules (5.8.8-12) to 5.8.8-12ubuntu0.4
pidgin (1:2.4.1-1ubuntu2.1) to 1:2.4.1-1ubuntu2.3
pidgin-data (1:2.4.1-1ubuntu2.1) to 1:2.4.1-1ubuntu2.3
python-apt (0.7.4ubuntu7.3) to 0.7.4ubuntu7.4
python-gobject (2.14.2-0ubuntu1) to 2.14.2-0ubuntu2
python-libxml2 (2.6.31.dfsg-2ubuntu1.2) to 2.6.31.dfsg-2ubuntu1.3
python-uno (1:2.4.1-1ubuntu2) to 1:2.4.1-1ubuntu2.1
readahead (1:0.20050517.0220-0ubuntu14) to 1:0.20050517.0220-0ubuntu14.1
sudo (1.6.9p10-1ubuntu3.3) to 1.6.9p10-1ubuntu3.4
sysv-rc (2.86.ds1-14.1ubuntu45) to 2.86.ds1-14.1ubuntu45.1
sysvutils (2.86.ds1-14.1ubuntu45) to 2.86.ds1-14.1ubuntu45.1
totem (2.22.1-0ubuntu2) to 2.22.1-0ubuntu3
totem-common (2.22.1-0ubuntu2) to 2.22.1-0ubuntu3
totem-gstreamer (2.22.1-0ubuntu2) to 2.22.1-0ubuntu3
totem-mozilla (2.22.1-0ubuntu2) to 2.22.1-0ubuntu3
totem-plugins (2.22.1-0ubuntu2) to 2.22.1-0ubuntu3
ttf-opensymbol (1:2.4.1-1ubuntu2) to 1:2.4.1-1ubuntu2.1
tzdata (2008h-0ubuntu0.8.04.1) to 2009b-0ubuntu0.8.04
ubuntu-docs (8.04.2~hardy) to 8.06.1
ufw (0.16.2.3) to 0.16.2.4
util-linux (2.13.1-5ubuntu2) to 2.13.1-5ubuntu3
util-linux-locales (2.13.1-5ubuntu2) to 2.13.1-5ubuntu3
vim-common (1:7.1-138+1ubuntu3) to 1:7.1-138+1ubuntu3.1
vim-tiny (1:7.1-138+1ubuntu3) to 1:7.1-138+1ubuntu3.1
vinagre (0.5.1-0ubuntu1) to 0.5.1-0ubuntu1.1
xorg-driver-fglrx (1:7.1.0-8-3+2.6.24.14-21.51) to 1:7.1.0-8-3+2.6.24.16-23.56
xserver-xorg-video-amd (2.9.0-1ubuntu2.4) to 2.9.0-1ubuntu2.5
xserver-xorg-video-ati (1:6.8.0-1) to 1:6.8.0-1ubuntu1
xserver-xorg-video-geode (2.9.0-1ubuntu2.4) to 2.9.0-1ubuntu2.5
xserver-xorg-video-intel (2:2.2.1-1ubuntu13.7) to 2:2.2.1-1ubuntu13.8
xterm (229-1ubuntu1) to 229-1ubuntu1.1
xulrunner-1.9 (1.9.0.3+build1+nobinonly-0ubuntu0.8.04.1) to 1.9.0.7+nobinonly-0ubuntu0.8.04.1
xulrunner-1.9-gnome-support (1.9.0.3+build1+nobinonly-0ubuntu0.8.04.1) to 1.9.0.7+nobinonly-0ubuntu0.8.04.1

Installed the following packages:
linux-headers-2.6.24-23 (2.6.24-23.48)
linux-headers-2.6.24-23-generic (2.6.24-23.48)
linux-image-2.6.24-23-generic (2.6.24-23.48)
linux-restricted-modules-2.6.24-23-generic (2.6.24.16-23.56)
linux-ubuntu-modules-2.6.24-23-generic (2.6.24-23.37)

---

### Post by HermanAB on 2009-03-25
Unfortunately, people have come to believe that constant updates is a good thing.  This is probably due to constant MS Windows updates, which has a never ending series of small bugs that need fixing. Linux however, is very stable and once you got it to work properly, it is best left alone.  

Think of it this way:  If your machine is working properly, then an update cannot make it better.  At best it will be the same and at worst it will be dead in the water - so not worth the risk.

I never update my machines - I re-install them from scratch every 18 months and then leave them alone and they just keep chugging along.

Cheers,

Herman

---

### Post by davidsrsb on 2009-03-25
I don't think that is good advice for a machine connecting to the Internet
The Firefox updates, for example, are security fixes

---

### Post by kingbilly on 2009-03-25
Are you out of space on a partition?

I have my / and /home mounted to the same partition, while  /home/user/Music and /home/user/Video are on a much larger partition.  Sometimes i forget to move stuff I download to these folders and just leave them in my home directory, or desktop.  This often results in the partition filling up.


This means applications can't use /tmp.
**I had some of the same problems you did**

1) Music player not loading
2) Firefox loads, but there are no bookmarks!

Run ```
df -h
``` in a terminal, anything getting close to 100% usage?

---

### Post by Canuck90 on 2009-03-25
That sounds like it's the problem, my ubuntu partition is 100% full, I don't have a separate partition for /home. If I clear some space is there a way to fix the problem? Like redoing the updates?

---

### Post by kingbilly on 2009-03-25
Do you have any big videos or anything you can delete or copy onto removable media?

How big is your hard drive?
Is the trash empty?

I don't know much about removing packages, but there is a way to delete unneeded packages, as well as other junk.

---

### Post by Canuck90 on 2009-03-25
I've cleared 4GB of space, I figure that should be enough. Now I just need to figure out how to remove the packages.

---

### Post by cudBwrong on 2009-03-25
> **davidsrsb said:**
> I don't think that is good advice for a machine connecting to the Internet
The Firefox updates, for example, are security fixes

I agree, I've been reading the descriptions of recent updates, and a very high proportion are security related, including, I believe, many on Canuck90's list.  I'm in the middle of rebuilding 5 MS Windows boxes that all had Master Boot Record rootkits, even though we are very careful about upgrades and where we surf.  Each box takes about a day, to reinstall everything.  Most likely the exploits came in through browser and plugin vulnerabilites.  Unfortunately, the bad guys are winning, and it's only a matter of time before they turn more of their attention to Linux.

---

### Post by Canuck90 on 2009-03-25
I used deborphan to find and clear all the orphaned packages and so far so good, Firefox is working well, Amarok seems to work, and I can shut down the computer without having to just hold down the power button. Thanks for the help!

---

### Post by cudBwrong on 2009-03-25
> **Canuck90 said:**
> I've cleared 4GB of space, I figure that should be enough. Now I just need to figure out how to remove the packages.

Will the synaptic package manager or update manager function at all?  If they do, you might want to try going forward instead of backwards and just update the machine.  Now that you have space, it may all just work properly.

If these applications don't work, you could try the command line package manager "aptitude."

Synaptic has an option to "remove all."  You can search for old versions of the kernel that you may not need (careful, keep the 2 latest) and free up some space.  It will rebuild your grub menu.

---

### Post by 123456789123456789123456 on 2009-03-26
the solution should be the following, clean as much space as you can, several hundred megs, burn things to cd/dvd, so on.  Go to the update manager, search for updates, and try updating,  From what I noticed, it looked like it downloaded all the files it needed, but was only able to update very little if any of them.  Update manager should have kept the list to itself, and should go ahead and attempt to install the updates after.  if not, synaptic packet manager may be able to, by clicking on the mark updates.  It will search and find the packages that are in need of updating, after that click apply changes.  That should get them updated.
A system restore should not be needed.

---

