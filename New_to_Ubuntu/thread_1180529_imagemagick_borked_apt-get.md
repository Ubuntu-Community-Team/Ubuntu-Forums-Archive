---
title: "imagemagick borked apt-get?"
date: 2009-06-06
forum: New to Ubuntu
---

### Post by lunaz on 2009-06-06
i tried to install imagemagick on my server and got errors like the following. after that i tried to purge, autoclean, clean, remove, reinstall, for each package in the list, all getting nowhere. i also tried to dpkg --configure -a with no results.

```

luna@teh-serverer:~$ sudo apt-get update && sudo apt-get upgrade
[sudo] password for luna:
Hit http://security.ubuntu.com intrepid-security Release.gpg
Ign http://security.ubuntu.com intrepid-security/main Translation-en_US
Hit http://us.archive.ubuntu.com intrepid Release.gpg
Ign http://us.archive.ubuntu.com intrepid/main Translation-en_US
Ign http://security.ubuntu.com intrepid-security/restricted Translation-en_US
Ign http://security.ubuntu.com intrepid-security/universe Translation-en_US
Ign http://security.ubuntu.com intrepid-security/multiverse Translation-en_US
Hit http://security.ubuntu.com intrepid-security Release
Ign http://us.archive.ubuntu.com intrepid/restricted Translation-en_US
Ign http://us.archive.ubuntu.com intrepid/universe Translation-en_US
Ign http://us.archive.ubuntu.com intrepid/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com intrepid-updates Release.gpg
Ign http://us.archive.ubuntu.com intrepid-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com intrepid-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com intrepid-updates/universe Translation-en_US
Ign http://us.archive.ubuntu.com intrepid-updates/multiverse Translation-en_US
Hit http://security.ubuntu.com intrepid-security/main Packages
Hit http://us.archive.ubuntu.com intrepid Release
Hit http://us.archive.ubuntu.com intrepid-updates Release
Hit http://security.ubuntu.com intrepid-security/restricted Packages
Hit http://security.ubuntu.com intrepid-security/main Sources
Hit http://security.ubuntu.com intrepid-security/restricted Sources
Hit http://security.ubuntu.com intrepid-security/universe Packages
Hit http://us.archive.ubuntu.com intrepid/main Packages
Hit http://us.archive.ubuntu.com intrepid/restricted Packages
Hit http://us.archive.ubuntu.com intrepid/main Sources
Hit http://us.archive.ubuntu.com intrepid/restricted Sources
Hit http://security.ubuntu.com intrepid-security/universe Sources
Hit http://security.ubuntu.com intrepid-security/multiverse Packages
Hit http://security.ubuntu.com intrepid-security/multiverse Sources
Hit http://us.archive.ubuntu.com intrepid/universe Packages
Hit http://us.archive.ubuntu.com intrepid/universe Sources
Hit http://us.archive.ubuntu.com intrepid/multiverse Packages
Hit http://us.archive.ubuntu.com intrepid/multiverse Sources
Hit http://us.archive.ubuntu.com intrepid-updates/main Packages
Hit http://us.archive.ubuntu.com intrepid-updates/restricted Packages
Hit http://us.archive.ubuntu.com intrepid-updates/main Sources
Hit http://us.archive.ubuntu.com intrepid-updates/restricted Sources
Hit http://us.archive.ubuntu.com intrepid-updates/universe Packages
Hit http://us.archive.ubuntu.com intrepid-updates/universe Sources
Hit http://us.archive.ubuntu.com intrepid-updates/multiverse Packages
Hit http://us.archive.ubuntu.com intrepid-updates/multiverse Sources
Reading package lists... Done
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages have been kept back:
  linux-image-server linux-server
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
14 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up fontconfig (2.6.0-1ubuntu4) ...
/var/lib/dpkg/info/fontconfig.postinst: 13: defoma-subst: not found
/var/lib/dpkg/info/fontconfig.postinst: 13: defoma-subst: not found
dpkg: error processing fontconfig (--configure):
 subprocess post-installation script returned error exit status 127
Setting up gsfonts (1:8.11+urwcyr1.0.7~pre43-2) ...
(Re-)registering PostScript fonts...
/var/lib/dpkg/info/gsfonts.postinst: 37: defoma-font: not found
dpkg: error processing gsfonts (--configure):
 subprocess post-installation script returned error exit status 127
dpkg: dependency problems prevent configuration of ghostscript:
 ghostscript depends on gsfonts (>= 6.0-1); however:
  Package gsfonts is not configured yet.
dpkg: error processing ghostscript (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          dpkg: dependency problems prevent configuration of libpango1.0-common:
 libpango1.0-common depends on fontconfig (>= 2.1.91); however:
  Package fontconfig is not configured yet.
dpkg: error processing libpango1.0-common (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of libpango1.0-0:
 libpango1.0-0 depends on libpango1.0-common (>= 1.22.2-0ubuntu1.1); however:
  Package libpango1.0-common is not configured yet.
dpkg: error processing libpango1.0-0 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of libgraphviz4:
 libgraphviz4 depends on libpango1.0-0 (>= 1.21.3); however:
  Package libpango1.0-0 is not configured yet.
dpkg: error processing libgraphviz4 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of libgtk2.0-0:
 libgtk2.0-0 depends on libpango1.0-0 (>= 1.21.6); however:
  Package libpango1.0-0 is not configured yet.
dpkg: error processing libgtk2.0-0 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of librsvg2-2:
 librsvg2-2 depends on libgtk2.0-0 (>= 2.14.1); however:
  Package libgtk2.0-0 is not configured yet.
 librsvg2-2 depends on libpango1.0-0 (>= 1.21.6); however:
  Package libpango1.0-0 is not configured yet.
dpkg: error processing librsvg2-2 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of libwmf0.2-7:
 libwmf0.2-7 depends on gtk2.0-binver-2.10.0; however:
  Package gtk2.0-binver-2.10.0 is not installed.
  Package libgtk2.0-0 which provides gtk2.0-binver-2.10.0 is not configured yet.
 libwmf0.2-7 depends on gsfonts; however:
  Package gsfonts is not configured yet.
dpkg: error processing libwmf0.2-7 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of libmagick10:
 libmagick10 depends on libgraphviz4 (>= 2.18); however:
  Package libgraphviz4 is not configured yet.
 libmagick10 depends on libgtk2.0-0 (>= 2.13.6); however:
  Package libgtk2.0-0 is not configured yet.
 libmagick10 depends on librsvg2-2 (>= 2.18.1); however:
  Package librsvg2-2 is not configured yet.
 libmagick10 depends on libwmf0.2-7 (>= 0.2.8.4); however:
  Package libwmf0.2-7 is not configured yet.
dpkg: error processing libmagick10 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of imagemagick:
 imagemagick depends on libmagick10; however:
  Package libmagick10 is not configured yet.
dpkg: error processing imagemagick (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of libgtk2.0-bin:
 libgtk2.0-bin depends on libgtk2.0-0 (>= 2.14.4-0ubuntu1); however:
  Package libgtk2.0-0 is not configured yet.
dpkg: error processing libgtk2.0-bin (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Setting up psfontmgr (0.11.10-0.2ubuntu1) ...
/var/lib/dpkg/info/psfontmgr.postinst: 12: /usr/bin/defoma-app: not found
dpkg: error processing psfontmgr (--configure):
 subprocess post-installation script returned error exit status 127
Setting up x-ttcidfont-conf (29) ...
No apport report written because MaxReports is reached already
                                                              dpkg: error processing x-ttcidfont-conf (--configure):
 subprocess post-installation script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 fontconfig
 gsfonts
 ghostscript
 libpango1.0-common
 libpango1.0-0
 libgraphviz4
 libgtk2.0-0
 librsvg2-2
 libwmf0.2-7
 libmagick10
 imagemagick
 libgtk2.0-bin
 psfontmgr
 x-ttcidfont-conf
E: Sub-process /usr/bin/dpkg returned an error code (1)
luna@teh-serverer:~$

```

i can provide more outputs for each command when i get home; if there's any more info i missed let me know :)

---

### Post by aysiu on 2009-06-07
Maybe you can edit the /var/lib/dpkg/info/psfontmgr.postinst manually and take out whatever parameters it says it needs for removal (but clearly can't execute).

---

### Post by lunaz on 2009-06-09
thanks for the help :)

this seems to have fixed it:

cd /usr/bin/dpkg

sudo mv info/* info.bak/
sudo rm -rf info
sudo mv info.bak info

then do updates as needed. taken from
[https://answers.launchpad.net/ubuntu/+question/41235](https://answers.launchpad.net/ubuntu/+question/41235)

---

### Post by lunaz on 2009-06-17
update:

i tried to update my system today and the error came back but involves different packages. i tried to remove them and update again, but no luck. apt-get -f install and dpkg --configure -a made no difference.

```

luna@teh-serverer:~$ sudo apt-get update
Hit http://security.ubuntu.com intrepid-security Release.gpg                
Ign http://security.ubuntu.com intrepid-security/main Translation-en_US     
Hit http://us.archive.ubuntu.com intrepid Release.gpg
Ign http://us.archive.ubuntu.com intrepid/main Translation-en_US
Ign http://security.ubuntu.com intrepid-security/restricted Translation-en_US
Ign http://security.ubuntu.com intrepid-security/universe Translation-en_US
Ign http://security.ubuntu.com intrepid-security/multiverse Translation-en_US
Hit http://security.ubuntu.com intrepid-security Release
Ign http://us.archive.ubuntu.com intrepid/restricted Translation-en_US
Ign http://us.archive.ubuntu.com intrepid/universe Translation-en_US
Ign http://us.archive.ubuntu.com intrepid/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com intrepid-updates Release.gpg
Ign http://us.archive.ubuntu.com intrepid-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com intrepid-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com intrepid-updates/universe Translation-en_US
Ign http://us.archive.ubuntu.com intrepid-updates/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com intrepid Release
Hit http://security.ubuntu.com intrepid-security/main Packages      
Hit http://us.archive.ubuntu.com intrepid-updates Release
Hit http://security.ubuntu.com intrepid-security/restricted Packages
Hit http://security.ubuntu.com intrepid-security/main Sources
Hit http://security.ubuntu.com intrepid-security/restricted Sources
Hit http://security.ubuntu.com intrepid-security/universe Packages
Hit http://us.archive.ubuntu.com intrepid/main Packages
Hit http://us.archive.ubuntu.com intrepid/restricted Packages
Hit http://us.archive.ubuntu.com intrepid/main Sources
Hit http://us.archive.ubuntu.com intrepid/restricted Sources
Hit http://security.ubuntu.com intrepid-security/universe Sources
Hit http://security.ubuntu.com intrepid-security/multiverse Packages
Hit http://security.ubuntu.com intrepid-security/multiverse Sources
Hit http://us.archive.ubuntu.com intrepid/universe Packages
Hit http://us.archive.ubuntu.com intrepid/universe Sources
Hit http://us.archive.ubuntu.com intrepid/multiverse Packages
Hit http://us.archive.ubuntu.com intrepid/multiverse Sources
Hit http://us.archive.ubuntu.com intrepid-updates/main Packages
Hit http://us.archive.ubuntu.com intrepid-updates/restricted Packages
Hit http://us.archive.ubuntu.com intrepid-updates/main Sources
Hit http://us.archive.ubuntu.com intrepid-updates/restricted Sources
Hit http://us.archive.ubuntu.com intrepid-updates/universe Packages
Hit http://us.archive.ubuntu.com intrepid-updates/universe Sources
Hit http://us.archive.ubuntu.com intrepid-updates/multiverse Packages
Hit http://us.archive.ubuntu.com intrepid-updates/multiverse Sources
Reading package lists... Done
luna@teh-serverer:~$

```

```

luna@teh-serverer:~$ sudo apt-get upgrade > error.txt
y
No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already
                                            No apport report written because MaxReports is reached already
                          No apport report written because MaxReports is reached already
        E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

