---
title: "A couple of questions..."
date: 2009-12-02
forum: New to Ubuntu
---

### Post by MightyVikingJim on 2009-12-02
Hi, all.  I just installed Karmic on an IBM Thinkpad R40 and I've run into a couple of problems.

First, I've been trying to change the default colour depth from 24 to 16 in an effort to make the Desktop effects usable or, at the very least, allow me to view the System Monitor.

Second, when I install any new updates or packages, I get the following error at the end of the installation:

E: xulrunner-1.9.1: subprocess installed post-installation script returned error exit status 135
E: firefox-3.5: dependency problems - leaving unconfigured
E: firefox-3.5-branding: dependency problems - leaving unconfigured
E: firefox: dependency problems - leaving unconfigured
E: sun-java6-plugin: dependency problems - leaving unconfigured
E: ubufox: dependency problems - leaving unconfigured
E: xulrunner-1.9.1-gnome-support: dependency problems - leaving unconfigured

The package installs without problem, but I'm concerned about the dependency problems.

Thanks very much for your help!

-Jim

---

### Post by sandyd on 2009-12-02
run
```

sudo apt-get -f install

```
and post the output if there are errors.

---

### Post by sandyd on 2009-12-02
p.s. for the color depth, you will need to define the monitor size AND the color depth in the same line. (in xorg.conf)

---

### Post by MightyVikingJim on 2009-12-02
Sure thing.

Here are the results:

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
7 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up xulrunner-1.9.1 (1.9.1.5+nobinonly-0ubuntu0.9.10.1) ...
Bus error
dpkg: error processing xulrunner-1.9.1 (--configure):
 subprocess installed post-installation script returned error exit status 135
dpkg: dependency problems prevent configuration of firefox-3.5:
 firefox-3.5 depends on xulrunner-1.9.1 (>= 1.9.1); however:
  Package xulrunner-1.9.1 is not configured yet.
dpkg: error processing firefox-3.5 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of firefox-3.5-branding:
 firefox-3.5-branding depends on firefox-3.5 (= 3.5.5+nobinonly-0ubuntu0.9.10.1); however:
  Package firefox-3.5 is not configured yet.
dpkg: error processing firefox-3.5-branding (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of firefox:
 firefox depends on firefox-3.5; however:
  Package firefox-3.5 is not configured yet.
 firefox depends on firefox-3.5-branding; however:
  Package firefox-3.5-branding is not configured yet.
dpkg: error processing firefox (No apport report written because the error message indicates its a followup error from a previous failure.
                                                          No apport report written because the error message indicates its a followup error from a previous failure.
    No apport report written because MaxReports is reached already
                                                                  No apport report written because MaxReports is reached already
                                                No apport report written because MaxReports is reached already
                              No apport report written because MaxReports is reached already
            --configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of sun-java6-plugin:
 sun-java6-plugin depends on firefox | firefox-2 | iceweasel | mozilla-firefox | iceape-browser | mozilla-browser | epiphany-gecko | epiphany-webkit | epiphany-browser | galeon | midbrowser | xulrunner | xulrunner-1.9; however:
  Package firefox is not configured yet.
  Package firefox-2 is not installed.
  Package iceweasel is not installed.
  Package mozilla-firefox is not installed.
  Package iceape-browser is not installed.
  Package mozilla-browser is not installed.
  Package epiphany-gecko is not installed.
  Package epiphany-webkit is not installed.
  Package epiphany-browser is not installed.
  Package galeon is not installed.
  Package midbrowser is not installed.
  Package xulrunner is not installed.
  Package xulrunner-1.9 is not installed.
dpkg: error processing sun-java6-plugin (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubufox:
 ubufox depends on firefox | abrowser | firefox-3.0 | firefox-2; however:
  Package firefox is not configured yet.
  Package abrowser is not installed.
  Package firefox-3.0 is not installed.
  Package firefox-3.5 which provides firefox-3.0 is not configured yet.
  Package firefox-2 is not installed.
dpkg: error processing ubufox (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xulrunner-1.9.1-gnome-support:
 xulrunner-1.9.1-gnome-support depends on xulrunner-1.9.1 (= 1.9.1.5+nobinonly-0ubuntu0.9.10.1); however:
  Package xulrunner-1.9.1 is not configured yet.
dpkg: error processing xulrunner-1.9.1-gnome-support (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 xulrunner-1.9.1
 firefox-3.5
 firefox-3.5-branding
 firefox
 sun-java6-plugin
 ubufox
 xulrunner-1.9.1-gnome-support

```

Insofar as the colour depth goes, I've gathered that I'll need to define those variables, but I cannot find any xorg.conf file in the /etc/X11 folder.

Thanks.

---

### Post by sandyd on 2009-12-02
> **MightyVikingJim said:**
> Sure thing.

Here are the results:

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
7 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up xulrunner-1.9.1 (1.9.1.5+nobinonly-0ubuntu0.9.10.1) ...
Bus error
dpkg: error processing xulrunner-1.9.1 (--configure):
 subprocess installed post-installation script returned error exit status 135
dpkg: dependency problems prevent configuration of firefox-3.5:
 firefox-3.5 depends on xulrunner-1.9.1 (>= 1.9.1); however:
  Package xulrunner-1.9.1 is not configured yet.
dpkg: error processing firefox-3.5 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of firefox-3.5-branding:
 firefox-3.5-branding depends on firefox-3.5 (= 3.5.5+nobinonly-0ubuntu0.9.10.1); however:
  Package firefox-3.5 is not configured yet.
dpkg: error processing firefox-3.5-branding (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of firefox:
 firefox depends on firefox-3.5; however:
  Package firefox-3.5 is not configured yet.
 firefox depends on firefox-3.5-branding; however:
  Package firefox-3.5-branding is not configured yet.
dpkg: error processing firefox (No apport report written because the error message indicates its a followup error from a previous failure.
                                                          No apport report written because the error message indicates its a followup error from a previous failure.
    No apport report written because MaxReports is reached already
                                                                  No apport report written because MaxReports is reached already
                                                No apport report written because MaxReports is reached already
                              No apport report written because MaxReports is reached already
            --configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of sun-java6-plugin:
 sun-java6-plugin depends on firefox | firefox-2 | iceweasel | mozilla-firefox | iceape-browser | mozilla-browser | epiphany-gecko | epiphany-webkit | epiphany-browser | galeon | midbrowser | xulrunner | xulrunner-1.9; however:
  Package firefox is not configured yet.
  Package firefox-2 is not installed.
  Package iceweasel is not installed.
  Package mozilla-firefox is not installed.
  Package iceape-browser is not installed.
  Package mozilla-browser is not installed.
  Package epiphany-gecko is not installed.
  Package epiphany-webkit is not installed.
  Package epiphany-browser is not installed.
  Package galeon is not installed.
  Package midbrowser is not installed.
  Package xulrunner is not installed.
  Package xulrunner-1.9 is not installed.
dpkg: error processing sun-java6-plugin (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubufox:
 ubufox depends on firefox | abrowser | firefox-3.0 | firefox-2; however:
  Package firefox is not configured yet.
  Package abrowser is not installed.
  Package firefox-3.0 is not installed.
  Package firefox-3.5 which provides firefox-3.0 is not configured yet.
  Package firefox-2 is not installed.
dpkg: error processing ubufox (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xulrunner-1.9.1-gnome-support:
 xulrunner-1.9.1-gnome-support depends on xulrunner-1.9.1 (= 1.9.1.5+nobinonly-0ubuntu0.9.10.1); however:
  Package xulrunner-1.9.1 is not configured yet.
dpkg: error processing xulrunner-1.9.1-gnome-support (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 xulrunner-1.9.1
 firefox-3.5
 firefox-3.5-branding
 firefox
 sun-java6-plugin
 ubufox
 xulrunner-1.9.1-gnome-support

```Insofar as the colour depth goes, I've gathered that I'll need to define those variables, but I cannot find any xorg.conf file in the /etc/X11 folder.

Thanks.
howto create xorg.conf```
sudo Xorg -configure
```ill look into your other errors

fixing firefox:
```

sudo dpkg --remove --force-remove-reinstreq --force-depends xulrunner-1.9
sudo apt-get autoremove
sudo apt-get remove firefox*
sudo apt-get install firefox

```

---

### Post by MightyVikingJim on 2009-12-02
> **carlee said:**
> howto create xorg.conf```
sudo Xorg -configure
```ill look into your other errors

fixing firefox:
```

sudo dpkg --remove --force-remove-reinstreq --force-depends xulrunner-1.9
sudo apt-get autoremove
sudo apt-get remove firefox*
sudo apt-get install firefox

```

Thanks so much for your help.  I'm still getting some problems, though.

Here's the rsults when I run ```
sudo Xorg -configure
```:
```
_XSERVTransSocketUNIXCreateListener: ...SocketCreateListener() failed
_XSERVTransMakeAllCOTSServerListeners: server already running

Fatal server error:
Cannot establish any listening sockets - Make sure an X server isn't already running

Please consult the The X.Org Foundation support 
	 at http://wiki.x.org
 for help. 
Please also check the log file at "/var/log/Xorg.0.log" for additional information.

 ddxSigGiveUp: Closing log
```

Again, thanks so much for your help!

---

### Post by sandyd on 2009-12-02
> **MightyVikingJim said:**
> Thanks so much for your help.  I'm still getting some problems, though.

Here's the rsults when I run ```
sudo Xorg -configure
```:
```
_XSERVTransSocketUNIXCreateListener: ...SocketCreateListener() failed
_XSERVTransMakeAllCOTSServerListeners: server already running

Fatal server error:
Cannot establish any listening sockets - Make sure an X server isn't already running

Please consult the The X.Org Foundation support 
     at http://wiki.x.org
 for help. 
Please also check the log file at "/var/log/Xorg.0.log" for additional information.

 ddxSigGiveUp: Closing log
```Again, thanks so much for your help!
press ctrl+alt+f1
login
type this all in
```

sudo killall gdm
sudo Xorg -configure
sudo gdm

```

---

### Post by wojox on 2009-12-02
I think it's:

```
sudo X -configure
```

And it gets stored in /root called xorg.conf.new

---

### Post by MightyVikingJim on 2009-12-02
> **carlee said:**
> press ctrl+alt+f1
login
type this all in
```

sudo killall gdm
sudo Xorg -configure
sudo gdm

```

Unfortunately, I got the same error.

Again, though, I really appreciate the help.

---

### Post by sandyd on 2009-12-03
> **MightyVikingJim said:**
> Unfortunately, I got the same error.

Again, though, I really appreciate the help.
alright...
```

gksudo gedit /etc/X11/xorg.conf

```
paste this in
```

# xorg.conf (X.Org X Window System server configuration file)                                                                 
#                                                                                                                             
# This file was generated by dexconf, the Debian X Configuration tool, using                                                  
# values from the debconf database.                                                                                           
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Device"
        Identifier      "Configured Video Device"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection

```
save and youve got a xorg.

---

