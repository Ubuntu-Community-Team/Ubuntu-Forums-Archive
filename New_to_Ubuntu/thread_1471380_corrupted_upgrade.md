---
title: "corrupted upgrade"
date: 2010-05-03
forum: New to Ubuntu
---

### Post by richie3418 on 2010-05-03
I have made a couple posts for a broken flash plug in. I tried to follow the answers but still haven't got anywhere. Just now I tried to get something from the package manager and it wouldn't let me because of the broken package with this error:E: flashplugin-nonfree: Package is in a very bad inconsistent state - you should reinstall it before attempting a removal.
Do you think it would be a good idea to download the cd version then see how to install it over what I have or delete to ubuntu partition and star over which I dread doing. I can't use it like this.

---

### Post by Calash on 2010-05-03
I would not reinstall Ubuntu just for a broken flash player.  Try typing the following in the terminal

```

sudo apt-get remove flashplugin-nonfree
sudo apt-get install flashplugin-nonfree

```

The first line will remove it, the second will reinstall it from the repositories.  Let us know what happens.

---

### Post by utnubuuser on 2010-05-03
Well i f the package manager is saying to reinstall before removing, why not do that?> sudo apt-get install --reinstall flashplugin-nonfreethen> sudo apt-get remove flashplugin-nonfree --purgethen> sudo apt-get install flashplugin-nonfree

---

### Post by richie3418 on 2010-05-03
It will not let me sudo anything in the terminal, it gives me this:Sorry, try again.
[sudo] password for user, and I can't type anything after that.

---

### Post by sixthwheel on 2010-05-03
> **richie3418 said:**
> It will not let me sudo anything in the terminal, it gives me this:Sorry, try again.
[sudo] password for user, and I can't type anything after that.
When you're typing a password in the terminal. you will not see the bullets.
just type your password anyway, and hit enter

---

### Post by richie3418 on 2010-05-03
OK I got in and tried the steps in #3 and got this:
richie3418@richie3418-desktop:~$ sudo apt-get install --reinstall flashplugin-nonfree 
[sudo] password for richie3418: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  flashplugin-nonfree: Depends: flashplugin-installer but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
richie3418@richie3418-desktop:~$ sudo apt-get remove flashplugin-nonfree --purge 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.24-19-generic libfreebob0 libqt4-opengl libqt4-assistant
  libavutil1d hal-cups-utils libdc1394-13 libots0 libwxgtk2.6-0 libqt4-test
  libqt4-dbus blubuntu-gdm-theme libaiksaurusgtk-1.2-0c2a
  libaiksaurus-1.2-0c2a openoffice.org-hyphenation-en-us
  openoffice.org-writer2latex libqt4-core libpostproc1d mysql-common
  libservlet2.4-java libdvbpsi4 libavformat1d binutils-static python-ipy
  libxosd2 cryptsetup libmysqlclient15off link-grammar-dictionaries-en
  tango-icon-theme libx264-57 libvlc0 nvidia-kernel-common libwpd-stream8c2a
  bsh python-sip libqt4-gui libaiksaurus-1.2-data python-sip4 libgdome2-0
  libjaxp1.3-java libwxbase2.6-0 libpoppler2 libjline-java libxerces2-java
  libmjpegtools0c2a libqt4-svg libxalan2-java libiso9660-5 libdvdread3
  libqt4-xml libqt4-network libqt4-designer libgdome2-cpp-smart0c2a
  libavcodec1d libgmyth0 liblink-grammar4 libqt4-script libaudit0
  linux-headers-2.6.24-19 libfaad0
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  flashplugin-nonfree*
0 upgraded, 0 newly installed, 1 to remove and 14 not upgraded.
1 not fully installed or removed.
After this operation, 168kB disk space will be freed.
Do you want to continue [Y/n]? y
dpkg: error processing flashplugin-nonfree (--purge):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 flashplugin-nonfree
E: Sub-process /usr/bin/dpkg returned an error code (1)
richie3418@richie3418-desktop:~$ sudo apt-get install flashplugin-nonfree 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  flashplugin-nonfree: Depends: flashplugin-installer but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
richie3418@richie3418-desktop:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.24-19-generic libfreebob0 libqt4-opengl libqt4-assistant
  libavutil1d hal-cups-utils libdc1394-13 libots0 libwxgtk2.6-0 libqt4-test
  libqt4-dbus blubuntu-gdm-theme libaiksaurusgtk-1.2-0c2a
  libaiksaurus-1.2-0c2a openoffice.org-hyphenation-en-us
  openoffice.org-writer2latex libqt4-core libpostproc1d mysql-common
  libservlet2.4-java libdvbpsi4 libavformat1d binutils-static python-ipy
  libxosd2 cryptsetup libmysqlclient15off link-grammar-dictionaries-en
  tango-icon-theme libx264-57 libvlc0 nvidia-kernel-common libwpd-stream8c2a
  bsh python-sip libqt4-gui libaiksaurus-1.2-data python-sip4 libgdome2-0
  libjaxp1.3-java libwxbase2.6-0 libpoppler2 libjline-java libxerces2-java
  libmjpegtools0c2a libqt4-svg libxalan2-java libiso9660-5 libdvdread3
  libqt4-xml libqt4-network libqt4-designer libgdome2-cpp-smart0c2a
  libavcodec1d libgmyth0 liblink-grammar4 libqt4-script libaudit0
  linux-headers-2.6.24-19 libfaad0
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  flashplugin-installer flashplugin-nonfree
Suggested packages:
  konqueror-nsplugins ttf-xfree86-nonfree xfs
The following NEW packages will be installed:
  flashplugin-installer
The following packages will be upgraded:
  flashplugin-nonfree
1 upgraded, 1 newly installed, 0 to remove and 14 not upgraded.
1 not fully installed or removed.
Need to get 0B/21.4kB of archives.
After this operation, 61.4kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Preconfiguring packages ...
dpkg: error processing flashplugin-nonfree (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 flashplugin-nonfree
E: Sub-process /usr/bin/dpkg returned an error code (1)
richie3418@richie3418-desktop:~$

---

### Post by richie3418 on 2010-05-03
I have to leave for awhile will check this in the AM. I hope someone has a better idea, also I am still looking.

---

### Post by utnubuuser on 2010-05-04
The solution to reported bug:> sudo rm /var/lib/dpkg/info/flashplugin-nonfree.prerm

sudo dpkg --remove --force-remove-reinstreq flashplugin-nonfree
sudo dpkg --purge --force-remove-reinstreq flashplugin-nonfree

I just updated my system too and got the same problem you described.  There's a sticky:> [http://ubuntuforums.org/showthread.php?t=1469475&highlight=can%27t+remove+flashplugin]("http://ubuntuforums.org/showthread.php?t=1469475&highlight=can%27t+remove+flashplugin")

I followed the instructions, and on the last command it refused to complete because the directory /var/cache/flashplugin-nonfree wasn't empty, so I emptied it manually then completed the instructions and afterwards installed the new flashplugin with:> sudo apt-get install flashplugin-installer flashplugin-nonfree

---

### Post by richie3418 on 2010-05-04
Thank you utnubuser for the last. I don't think I will ever know what happened. I went to the bug report and put your 3 sudo commands with no results, either files not found to super user needed. I kept going through the bug report and came to: "sudo aptitude install flashplugin-installer" in post #26, almost like your last cmd. Anyway after putting that in all the broken items dissappeared. I will most likely have to install the adobe flash player I don't know because it is in the not installed list. So I guess this thread can be closed for now, thanks all of you.

---

