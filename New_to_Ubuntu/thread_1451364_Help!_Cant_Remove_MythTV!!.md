---
title: "Help! Cant Remove MythTV!!"
date: 2010-04-10
forum: New to Ubuntu
---

### Post by Bondy_uk on 2010-04-10
Hi everyone,

For some reason MythTV doesnt work and I cant uninstall it at all!

After loads of attempts I was finally able to uninstall everything except the MythTV_Backend package. In synaptic I get the following error:
"E: mythtv-backend: subprocess pre-removal script returned error exit status 1"

I would just leave it but I get this error every time I do updates, or install/uninstall any other packages.


Thanks in advance :)

---

### Post by mgranet on 2010-04-10
Does ```
sudo apt-get autoremove mythtv
``` return the error as well?

---

### Post by @rizz on 2010-04-10
TRY

  
apt-get remove myth*

and if that doesn't get it all, then add:

apt-get remove libmyth*

:P hope that helps

---

### Post by Bondy_uk on 2010-04-10
> **mgranet said:**
> Does ```
sudo apt-get autoremove mythtv
``` return the error as well?

I get this...
> 
Package mythtv is not installed, so not removed
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies.
  mythtv-backend: Depends: mythtv-common (= 0.21.0+fixes19961-0ubuntu8) but it is not going to be installed
                  Depends: mythtv-transcode-utils (= 0.21.0+fixes19961-0ubuntu8) but it is not going to be installed
                  Depends: libmyth-0.21-0 (>= 0.21.0+fixes19961) but it is not going to be installed
                  Depends: libmyth-perl but it is not going to be installed
                  Recommends: ntp but it is not going to be installed or
                              time-daemon or
                              ntp-simple but it is not installable
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

---

### Post by Bondy_uk on 2010-04-10
> **@rizz said:**
> TRY

  
apt-get remove myth*

> ian@ian-Ubuntu64:~$ sudo apt-get remove myth*
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting mythtv-database for regex ‘myth*’
Note, selecting mythbuntu-lirc-generator for regex ‘myth*’
Note, selecting mythmusic for regex ‘myth*’
Note, selecting mythexport for regex ‘myth*’
Note, selecting mythappearance for regex ‘myth*’
Note, selecting mythtv for regex ‘myth*’
Note, selecting mythtv-theme-mythcenter-wide for regex ‘myth*’
Note, selecting mythphone for regex ‘myth*’
Note, selecting mytharchive for regex ‘myth*’
Note, selecting libmyth-dev for regex ‘myth*’
Note, selecting mythtv-status for regex ‘myth*’
Note, selecting mythtv-themes for regex ‘myth*’
Note, selecting mythbuntu-artwork-usplash for regex ‘myth*’
Note, selecting mythtv-theme-blootube-osd for regex ‘myth*’
Note, selecting mythcontrols for regex ‘myth*’
Note, selecting mythtv-theme-metallurgy-osd for regex ‘myth*’
Note, selecting ubiquity-frontend-mythbuntu for regex ‘myth*’
Note, selecting mythtv-theme-metallurgy-wide for regex ‘myth*’
Note, selecting mythbuntu-common for regex ‘myth*’
Note, selecting mythdvd for regex ‘myth*’
Note, selecting mythvideo instead of mythdvd
Note, selecting mythplugins for regex ‘myth*’
Note, selecting mythtv-theme-projectgrayhem for regex ‘myth*’
Note, selecting mythbuntu-gdm-theme for regex ‘myth*’
Note, selecting libgmythupnp0 for regex ‘myth*’
Note, selecting gtk2-engines-mythbuntu for regex ‘myth*’
Note, selecting mythbuntu-diskless-server-standalone for regex ‘myth*’
Note, selecting mythbuntu-control-centre for regex ‘myth*’
Note, selecting libmyth-perl for regex ‘myth*’
Note, selecting mythgallery for regex ‘myth*’
Note, selecting mythbuntu-apple-trailers for regex ‘myth*’
Note, selecting mythgame for regex ‘myth*’
Note, selecting libmyth-python for regex ‘myth*’
Note, selecting mythnettv-gui for regex ‘myth*’
Note, selecting libmyth-0.21-dev for regex ‘myth*’
Note, selecting mythtv-theme-blootubelite-wide for regex ‘myth*’
Note, selecting mythtv-common for regex ‘myth*’
Note, selecting mythtvfs for regex ‘myth*’
Note, selecting mythnettv for regex ‘myth*’
Note, selecting mytop for regex ‘myth*’
Note, selecting mythtv-theme-iulius-osd for regex ‘myth*’
Note, selecting mythflix for regex ‘myth*’
Note, selecting mythweb for regex ‘myth*’
Note, selecting mythtv-theme-glass-wide for regex ‘myth*’
Note, selecting mythtv-backend for regex ‘myth*’
Note, selecting mythbuntu-diskless-client for regex ‘myth*’
Note, selecting mythtv-theme-iulius for regex ‘myth*’
Note, selecting mythnettv-svn for regex ‘myth*’
Note, selecting mythmovies for regex ‘myth*’
Note, selecting gmyth-utils for regex ‘myth*’
Note, selecting mythbuntu-desktop for regex ‘myth*’
Note, selecting libgmyth-dev for regex ‘myth*’
Note, selecting mythbuntu-log-grabber for regex ‘myth*’
Note, selecting mythtv-theme-neon-wide for regex ‘myth*’
Note, selecting mythtv-theme-blootube-wide for regex ‘myth*’
Note, selecting mythtv-theme-titivillus for regex ‘myth*’
Note, selecting mythtv-theme-minimalist-wide for regex ‘myth*’
Note, selecting mythtv-doc for regex ‘myth*’
Note, selecting mythstream for regex ‘myth*’
Note, selecting mythtv-theme-titivillus-osd for regex ‘myth*’
Note, selecting mythtv-theme-retro-osd for regex ‘myth*’
Note, selecting mythtv-theme-projectgrayhem-wide for regex ‘myth*’
Note, selecting mythtv-backend-master for regex ‘myth*’
Note, selecting libmythes-dev for regex ‘myth*’
Note, selecting mythimport for regex ‘myth*’
Note, selecting mythtv-theme-isthmus for regex ‘myth*’
Note, selecting mythweather for regex ‘myth*’
Note, selecting mythvideo for regex ‘myth*’
Note, selecting mythtv-frontend for regex ‘myth*’
Note, selecting libmyth-0.21-0 for regex ‘myth*’
Note, selecting mythbuntu-live-autostart for regex ‘myth*’
Note, selecting libgmyth0 for regex ‘myth*’
Note, selecting mythtv-theme-mythbuntu for regex ‘myth*’
Note, selecting mytharchive-data for regex ‘myth*’
Note, selecting mythtv-theme-gray-osd for regex ‘myth*’
Note, selecting libgmythupnp-dev for regex ‘myth*’
Note, selecting libmyth-0.21-0-dev for regex ‘myth*’
Note, selecting libmyth-dev instead of libmyth-0.21-0-dev
Note, selecting mythtv-theme-projectgrayhem-osd for regex ‘myth*’
Note, selecting mythzoneminder for regex ‘myth*’
Note, selecting mythnews for regex ‘myth*’
Note, selecting mythtv-theme-mythcenter for regex ‘myth*’
Note, selecting mythbuntu-live for regex ‘myth*’
Note, selecting mythbuntu-default-settings for regex ‘myth*’
Note, selecting mythtv-theme-blootube for regex ‘myth*’
Note, selecting mythtv-theme-retro for regex ‘myth*’
Note, selecting mythtv-transcode-utils for regex ‘myth*’
Note, selecting mythbuntu-diskless-server for regex ‘myth*’
The following packages were automatically installed and are no longer required:
  libnet-daemon-perl libdbi-perl libhtml-template-perl mysql-server-core-5.0
  libnet-upnp-perl libdbd-mysql-perl libqt3-mt-mysql mysql-client libcdaudio1
  libplrpc-perl mysql-client-5.0
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED
  mythtv-backend
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 3064kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 245041 files and directories currently installed.)
Removing mythtv-backend ...
ln: creating symbolic link `/home/mythtv/.mythtv/mysql.txt': File exists
invoke-rc.d: initscript mythtv-backend, action "stop" failed.
dpkg: error processing mythtv-backend (--remove):
 subprocess pre-removal script returned error exit status 1
ln: creating symbolic link `/home/mythtv/.mythtv/mysql.txt': File exists
invoke-rc.d: initscript mythtv-backend, action "start" failed.
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 mythtv-backend
E: Sub-process /usr/bin/dpkg returned an error code (1)


> **@rizz said:**
> 
and if that doesn't get it all, then add:

apt-get remove libmyth*

I have managed to remove everything except mythtv-backend.
However, I still gave it a try in case I was wrong

> ian@ian-Ubuntu64:~$ sudo apt-get remove libmyth*
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting libmyth-dev for regex ‘libmyth*’
Note, selecting libmyth-perl for regex ‘libmyth*’
Note, selecting libmyth-python for regex ‘libmyth*’
Note, selecting libmyth-0.21-dev for regex ‘libmyth*’
Note, selecting libmythes-dev for regex ‘libmyth*’
Note, selecting libmyth-0.21-0 for regex ‘libmyth*’
Note, selecting libmyth-0.21-0-dev for regex ‘libmyth*’
Note, selecting libmyth-dev instead of libmyth-0.21-0-dev
E: Couldn't find package libmyth*

---

### Post by mgranet on 2010-04-11
Try ```
sudo apt-get -f install
```
This will install the missing dependencies that are messing things up. Then you can run the code from my first post to remove the program.

---

### Post by Bondy_uk on 2010-04-11
> **mgranet said:**
> Try ```
sudo apt-get -f install
```
This will install the missing dependencies that are messing things up. Then you can run the code from my first post to remove the program.

Thank You!

That worked perfectly!

---

