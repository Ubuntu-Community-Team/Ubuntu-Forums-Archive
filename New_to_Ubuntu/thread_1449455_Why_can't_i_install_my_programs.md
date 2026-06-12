---
title: "Why can't i install my programs"
date: 2010-04-07
forum: New to Ubuntu
---

### Post by theweasel2345 on 2010-04-07
michael@TheCloud:~$ sudo apt-get install hddtemp
Reading package lists... Done
Building dependency tree       
Reading state information... Done
hddtemp is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
5 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up firefox-3.6 (3.6.3+nobinonly-1jolicloud2) ...
Please restart all running instances of firefox-3.6, or you will experience problems.
dpkg: error processing firefox-3.6 (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of firefox:
 firefox depends on firefox-3.6 (= 3.6.3+nobinonly-1jolicloud2); however:
  Package firefox-3.6 is not configured yet.
dpkg: error processing firefox (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of firefox-3.5:
 firefox-3.5 depends on firefox-3.6; however:
  Package firefox-3.6 is not configured yet.
dpkg: error processing firefox-3.5 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of firefox-3.6-gnome-support:
 firefox-3.6-gnome-support depends on firefox-3.6 (= 3.6.3+nobinonly-1jolicloud2); however:
  Package firefox-3.6 is not configured yet.
dpkg: error processing firefox-3.6-gnome-support (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration ofNo apport report written because the error message indicates its a followup error from a previous failure.
             No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                                       No apport report written because MaxReports is reached already
                                      No apport report written because MaxReports is reached already
                                                                                                     firefox-gnome-support:
 firefox-gnome-support depends on firefox-3.6-gnome-support; however:
  Package firefox-3.6-gnome-support is not configured yet.
dpkg: error processing firefox-gnome-support (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 firefox-3.6
 firefox
 firefox-3.5
 firefox-3.6-gnome-support
 firefox-gnome-support
E: Sub-process /usr/bin/dpkg returned an error code (1)
michael@TheCloud:~$

---

### Post by tom.swartz07 on 2010-04-07
> **theweasel2345 said:**
> ```
michael@TheCloud:~$ sudo apt-get install hddtemp
Reading package lists... Done
Building dependency tree       
Reading state information... Done
hddtemp is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
5 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up firefox-3.6 (3.6.3+nobinonly-1jolicloud2) ...
Please restart all running instances of firefox-3.6, or you will experience problems.
dpkg: error processing firefox-3.6 (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of firefox:
 firefox depends on firefox-3.6 (= 3.6.3+nobinonly-1jolicloud2); however:
  Package firefox-3.6 is not configured yet.
dpkg: error processing firefox (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of firefox-3.5:
 firefox-3.5 depends on firefox-3.6; however:
  Package firefox-3.6 is not configured yet.
dpkg: error processing firefox-3.5 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of firefox-3.6-gnome-support:
 firefox-3.6-gnome-support depends on firefox-3.6 (= 3.6.3+nobinonly-1jolicloud2); however:
  Package firefox-3.6 is not configured yet.
dpkg: error processing firefox-3.6-gnome-support (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration ofNo apport report written because the error message indicates its a followup error from a previous failure.
             No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                                       No apport report written because MaxReports is reached already
                                      No apport report written because MaxReports is reached already
                                                                                                     firefox-gnome-support:
 firefox-gnome-support depends on firefox-3.6-gnome-support; however:
  Package firefox-3.6-gnome-support is not configured yet.
dpkg: error processing firefox-gnome-support (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 firefox-3.6
 firefox
 firefox-3.5
 firefox-3.6-gnome-support
 firefox-gnome-support
E: Sub-process /usr/bin/dpkg returned an error code (1)
michael@TheCloud:~$
```

hddtemp is already installed. > michael@TheCloud:~$ sudo apt-get install hddtemp
Reading package lists... Done
Building dependency tree       
Reading state information... Done
**[COLOR="Red"]hddtemp is already the newest version.[/COLOR]**

From what it looks like, you have broken packages, and/or un-met dependencies. 

The best route is to open Synaptic Package Manager (System>administration>Synaptic) and select Edit> Fix Broken Packages. Apply. 

You should be good to go after that!

Post back and let us know if that fixed it!

---

### Post by 3rdalbum on 2010-04-07
You've got Jolicloud repositories enabled?

HDDtemp is already installed. It's a command-line program, you won't see it in your Applications menu.

Your other problem won't prevent the installation of software, but it is something you should try and get fixed. If you're running Ubuntu, then try removing the Jolicloud repository. If you're running Jolicloud, then try:

```
sudo dpkg --configure -a
```

or

```
sudo apt-get install -f
```

---

### Post by theweasel2345 on 2010-04-07
nothing worked
I dont have sympatics installed
dpkg didnt work
sudo apt-get install -f didnt work
any other suggestions

---

### Post by lisati on 2010-04-07
> **theweasel2345 said:**
> nothing worked
I dont have sympatics installed

It's Synaptic Package Manager, not sympatics... :)
Have a look on the System menu for Administration, and on the Administration menu for Synaptic Package Manager.

---

### Post by 3rdalbum on 2010-04-07
You should probably seek help from Jolicloud, rather than Ubuntu, because it's the Jolicloud packages that are causing your problem.

---

### Post by theweasel2345 on 2010-04-08
Well, I tried to remove firefox and all the programs that caused me trouble, but when i tried to reinstall them, same problem

---

### Post by lidex on 2010-04-08
Try uninstalling them all again and this time only re-install the firefox package.

```
sudo apt-get remove firefox-3.6 firefox firefox-3.5 firefox-3.6-gnome-support firefox-gnome-support
sudo apt-get install firefox
```

---

### Post by maniqui on 2010-04-08
I'm having the exact same issue, on a Jolicloud installation. I've trying uninstalling and re-installng firefox and firefox-* packages, both using Synaptic and aptitude, but after re-installing, I keep getting the same error:

```
Setting up firefox-3.6 (3.6.3+nobinonly-1jolicloud2) ...
Please restart all running instances of firefox-3.6, or you will experience problems.
dpkg: error processing firefox-3.6 (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of firefox:
 firefox depends on firefox-3.6 (= 3.6.3+nobinonly-1jolicloud2); however:
  Package firefox-3.6 is not configured yet.
dpkg: error processing firefox (--configure):
 dependency problems - leaving unconfigured
Setting up htop (0.8.1-4ubuntu1) ...
No apport report written because the error message indicates its a followup error from a previous failure.

Errors were encountered while processing:
 firefox-3.6
 firefox
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up firefox-3.6 (3.6.3+nobinonly-1jolicloud2) ...
Please restart all running instances of firefox-3.6, or you will experience problems.
dpkg: error processing firefox-3.6 (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of firefox:
 firefox depends on firefox-3.6 (= 3.6.3+nobinonly-1jolicloud2); however:
  Package firefox-3.6 is not configured yet.
dpkg: error processing firefox (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 firefox-3.6
 firefox

```

---

