---
title: "Help! Firefox is dead!"
date: 2010-07-27
forum: New to Ubuntu
---

### Post by RedStarYellowSun on 2010-07-27
Help!
After making a stupid mistake in updating Firefox, it doesn't seem to exist anymore!
The icon on the upper-bar is now a red circle with a red line through it. When pressed, a window appears reporting:
```
XML Parsing Error: undefined entity
Location: chrome://browser/content/browser.xul
Line Number 31, Column 1:

<window id="main-window"
^
```

How can I fix this? Even Update Manager cannot update it because (according to the window that appears after pressing the "Install Updates" button):
```
You have 2 broken packages on your system!
Use the "Broken" filter to locate them.
```

And another window says:
```
(-) An error occured
The following details are provided:
E: /var/cache/apt/archives/firefox_3.6.8+build1+nobinonly-0ubuntu0.10.04.1_i386.deb: trying to overwrite '/usr/bin/firefox', which is also in package firefox-mozilla-build 0
```

How do I fix this?

Thanks for your time.

Take care,
RedStarYellowSun

---

### Post by bsharp on 2010-07-27
Open Synaptic, click on the "Broken" filter, mark them to reinstall, and apply.

Should do it.

---

### Post by RedStarYellowSun on 2010-07-29
> **bsharp said:**
> Open Synaptic, click on the "Broken" filter, mark them to reinstall, and apply.

Should do it.

It gives me this window:
```
(-) An error occured
The following details are provided:
E: /var/cache/apt/archives/firefox_3.6.8+build1+nobinonly-0ubuntu0.10.04.1_i386.deb: trying to overwrite '/usr/bin/firefox', which is also in package firefox-mozilla-build 0
[Close]
```

I tried removing and then reinstalling. That seems to have done some good because, now, I have only 1 broken package: abrowser-branding.

How do I fix this stubborn one?

Thanks for your time.

Take care,
RedStarYellowSun

---

### Post by RedStarYellowSun on 2010-07-30
Anyone still there?

---

### Post by sandyd on 2010-07-30
> **RedStarYellowSun said:**
> Anyone still there?
```

sudo dpkg --purge --force all abrowser-branding abrowser-3.5-branding firefox-mozilla-build 
sudo apt-get install firefox-branding
```

---

### Post by RedStarYellowSun on 2010-08-01
> **carlee said:**
> ```

sudo dpkg --purge force all abrowser-branding
sudo apt-get install firefox-branding
```
Thanks for responding! :^D
Here are the results:
```
jutumang@jutumang-laptop:~$ sudo dpkg --purge force all abrowser-branding 
[sudo] password for jutumang:  
dpkg: warning: ignoring request to remove force which isn't installed. 
dpkg: warning: ignoring request to remove all which isn't installed. 
(Reading database ... 203676 files and directories currently installed.) 
Removing abrowser-branding ... 
Processing triggers for python-gmenu ... 
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache... 
Processing triggers for desktop-file-utils ... 
Processing triggers for python-support ... 
jutumang@jutumang-laptop:~$ sudo apt-get install firefox-branding 
Reading package lists... Done 
Building dependency tree        
Reading state information... Done 
You might want to run `apt-get -f install' to correct these: 
The following packages have unmet dependencies: 
  firefox-branding: Depends: firefox (= 3.6.8+build1+nobinonly-0ubuntu0.10.04.1) 
                    Conflicts: abrowser-3.5-branding 
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution). 
jutumang@jutumang-laptop:~$ sudo apt-get -f install 
Reading package lists... Done 
Building dependency tree        
Reading state information... Done 
Correcting dependencies... Done 
The following packages were automatically installed and are no longer required: 
  plasma-dataengines-workspace kdepim-runtime libprocessui4 libtaskmanager4 
  libqimageblitz4 libkscreensaver5 libsolidcontrolifaces4 
  linux-headers-2.6.32-21 plasma-widgets-workspace mysql-client-core-5.1 
  libplasma-geolocation-interface4 mysql-server-core-5.1 libksgrd4 
  linux-headers-2.6.32-21-generic kdebase-workspace-bin libkworkspace4 
  libplasmagenericshell4 libkfontinst4 libkephal4 kdebase-workspace-data 
  ksysguardd libplasmaclock4 libweather-ion4 kdebase-workspace-kgreet-plugins 
  libsolidcontrol4 akonadi-server libplasma-applet-system-monitor4 
  libprocesscore4 
Use 'apt-get autoremove' to remove them. 
The following extra packages will be installed: 
  abrowser-branding firefox 
Suggested packages: 
  firefox-gnome-support kmozillahelper latex-xft-fonts 
The following NEW packages will be installed: 
  abrowser-branding firefox 
0 upgraded, 2 newly installed, 0 to remove and 112 not upgraded. 
3 not fully installed or removed. 
Need to get 0B/11.4MB of archives. 
After this operation, 30.7MB of additional disk space will be used. 
Do you want to continue [Y/n]? y 
Selecting previously deselected package abrowser-branding. 
(Reading database ... 203655 files and directories currently installed.) 
Unpacking abrowser-branding (from .../abrowser-branding_3.6.8+build1+nobinonly-0ubuntu0.10.04.1_i386.deb) ... 
Unpacking firefox (from .../firefox_3.6.8+build1+nobinonly-0ubuntu0.10.04.1_i386.deb) ... 
dpkg: error processing /var/cache/apt/archives/firefox_3.6.8+build1+nobinonly-0ubuntu0.10.04.1_i386.deb (--unpack): 
 trying to overwrite '/usr/bin/firefox', which is also in package firefox-mozilla-build 0:3.6.3-0ubuntu1 
Processing triggers for python-gmenu ... 
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache... 
Processing triggers for desktop-file-utils ... 
Processing triggers for python-support ... 
  Errors were encountered while processing: 
 /var/cache/apt/archives/firefox_3.6.8+build1+nobinonly-0ubuntu0.10.04.1_i386.deb 
E: Sub-process /usr/bin/dpkg returned an error code (1) 
jutumang@jutumang-laptop:~$
```

Aside from the requested 'apt-get autoremove', what course of action would your recommend?

Thanks for your time.

Take care,
RedStarYellowSun

---

### Post by viking350 on 2010-08-01
I am not a big fan of fire fox here is a suggestion (not in a attitude voice go into the software center and then install Google chromium;)

---

### Post by sandyd on 2010-08-01
> **RedStarYellowSun said:**
> Thanks for responding! :^D
Here are the results:
```
jutumang@jutumang-laptop:~$ sudo dpkg --purge force all abrowser-branding 
[sudo] password for jutumang:  
dpkg: warning: ignoring request to remove force which isn't installed. 
dpkg: warning: ignoring request to remove all which isn't installed. 
(Reading database ... 203676 files and directories currently installed.) 
Removing abrowser-branding ... 
Processing triggers for python-gmenu ... 
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache... 
Processing triggers for desktop-file-utils ... 
Processing triggers for python-support ... 
jutumang@jutumang-laptop:~$ sudo apt-get install firefox-branding 
Reading package lists... Done 
Building dependency tree        
Reading state information... Done 
You might want to run `apt-get -f install' to correct these: 
The following packages have unmet dependencies: 
  firefox-branding: Depends: firefox (= 3.6.8+build1+nobinonly-0ubuntu0.10.04.1) 
                    Conflicts: abrowser-3.5-branding 
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution). 
jutumang@jutumang-laptop:~$ sudo apt-get -f install 
Reading package lists... Done 
Building dependency tree        
Reading state information... Done 
Correcting dependencies... Done 
The following packages were automatically installed and are no longer required: 
  plasma-dataengines-workspace kdepim-runtime libprocessui4 libtaskmanager4 
  libqimageblitz4 libkscreensaver5 libsolidcontrolifaces4 
  linux-headers-2.6.32-21 plasma-widgets-workspace mysql-client-core-5.1 
  libplasma-geolocation-interface4 mysql-server-core-5.1 libksgrd4 
  linux-headers-2.6.32-21-generic kdebase-workspace-bin libkworkspace4 
  libplasmagenericshell4 libkfontinst4 libkephal4 kdebase-workspace-data 
  ksysguardd libplasmaclock4 libweather-ion4 kdebase-workspace-kgreet-plugins 
  libsolidcontrol4 akonadi-server libplasma-applet-system-monitor4 
  libprocesscore4 
Use 'apt-get autoremove' to remove them. 
The following extra packages will be installed: 
  abrowser-branding firefox 
Suggested packages: 
  firefox-gnome-support kmozillahelper latex-xft-fonts 
The following NEW packages will be installed: 
  abrowser-branding firefox 
0 upgraded, 2 newly installed, 0 to remove and 112 not upgraded. 
3 not fully installed or removed. 
Need to get 0B/11.4MB of archives. 
After this operation, 30.7MB of additional disk space will be used. 
Do you want to continue [Y/n]? y 
Selecting previously deselected package abrowser-branding. 
(Reading database ... 203655 files and directories currently installed.) 
Unpacking abrowser-branding (from .../abrowser-branding_3.6.8+build1+nobinonly-0ubuntu0.10.04.1_i386.deb) ... 
Unpacking firefox (from .../firefox_3.6.8+build1+nobinonly-0ubuntu0.10.04.1_i386.deb) ... 
dpkg: error processing /var/cache/apt/archives/firefox_3.6.8+build1+nobinonly-0ubuntu0.10.04.1_i386.deb (--unpack): 
 trying to overwrite '/usr/bin/firefox', which is also in package firefox-mozilla-build 0:3.6.3-0ubuntu1 
Processing triggers for python-gmenu ... 
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache... 
Processing triggers for desktop-file-utils ... 
Processing triggers for python-support ... 
  Errors were encountered while processing: 
 /var/cache/apt/archives/firefox_3.6.8+build1+nobinonly-0ubuntu0.10.04.1_i386.deb 
E: Sub-process /usr/bin/dpkg returned an error code (1) 
jutumang@jutumang-laptop:~$
```Aside from the requested 'apt-get autoremove', what course of action would your recommend?

Thanks for your time.

Take care,
RedStarYellowSunfixed. I wrote the commands to remove the metapackage, but not the package itself.... oops.:oops:

---

### Post by RedStarYellowSun on 2010-08-03
> **carlee said:**
> fixed. I wrote the commands to remove the metapackage, but not the package itself.... oops.:oops:

Thanks for the fix. It seems, though that 'mozilla-firefox-build' just refuses to be removed. After saying that 'force' and 'all' aren't installed and, after reading the database, here is what it says:
```
Removing abrowser-branding ...
Removing abrowser-3.5-branding ...
dpkg: dependency problems prevent removal of firefox-mozilla-build:
  firefox-3.0 depends on firefox; however:
   Package firefox is not installed
   Package firefox-mozilla-build which provides firefox is to be removed.
  firefox-3.5 depends on firefox; however:
   Package firefox is not installed
   Package firefox-mozilla-build which provides firefox is to be removed.
dpgk: Error processing firefox-mozilla-build (--purge):
 dependency problems - not removing
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for desktop-file-utils ...
Processing triggers for python-support ...
Errors were encountered while processing:
 firefox-mozilla-build
jutumang@jutumang-laptop:~$ sudo apt-get install firefox-branding
E: Could not get lock /var/lib/dpkg/lock - open (ll: Resource 
temporarily unavailale)
E: Unable to lock the administration directory (/var/lib/dpkg), is another process using it?
jutumang@jutumang-laptop:~$
```

How stubborn... It refuses to remove it because it will be removed if it does. How can we bypass this?

Thanks again!

Take care,
RedStarYellowSun

---

### Post by sandyd on 2010-08-03
> **RedStarYellowSun said:**
> Thanks for the fix. It seems, though that 'mozilla-firefox-build' just refuses to be removed. After saying that 'force' and 'all' aren't installed and, after reading the database, here is what it says:
```
Removing abrowser-branding ...
Removing abrowser-3.5-branding ...
dpkg: dependency problems prevent removal of firefox-mozilla-build:
  firefox-3.0 depends on firefox; however:
   Package firefox is not installed
   Package firefox-mozilla-build which provides firefox is to be removed.
  firefox-3.5 depends on firefox; however:
   Package firefox is not installed
   Package firefox-mozilla-build which provides firefox is to be removed.
dpgk: Error processing firefox-mozilla-build (--purge):
 dependency problems - not removing
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for desktop-file-utils ...
Processing triggers for python-support ...
Errors were encountered while processing:
 firefox-mozilla-build
jutumang@jutumang-laptop:~$ sudo apt-get install firefox-branding
E: Could not get lock /var/lib/dpkg/lock - open (ll: Resource 
temporarily unavailale)
E: Unable to lock the administration directory (/var/lib/dpkg), is another process using it?
jutumang@jutumang-laptop:~$
```How stubborn... It refuses to remove it because it will be removed if it does. How can we bypass this?

Thanks again!

Take care,
RedStarYellowSun
omg. I forgot two dashes in front of the --force.
I really need to stop making typos....

---

### Post by todak on 2010-08-03
Close all package manager programs and then open a terminal and enter this ```
sudo apt-get install firefox
``` and see if that works.

---

### Post by jtarin on 2010-08-03
> **carlee said:**
> omg. I forgot two dashes in front of the --force.
I really need to stop making typos....
Naw! Just be more creative.:p

---

### Post by finsyourfriend on 2010-08-03
Had an similar issue. See if this helps you out:

[http://ubuntuforums.org/showthread.php?t=1521025](http://ubuntuforums.org/showthread.php?t=1521025)

---

### Post by RedStarYellowSun on 2010-08-04
> **carlee said:**
> omg. I forgot two dashes in front of the --force.
I really need to stop making typos....

IT WORKED!!!! ***_THANK YOU SO MUCH!!!!!!_***

You rock!

Take care,
RedStarYellowSun

---

