---
title: "Administrator with No Permission?"
date: 2010-06-28
forum: New to Ubuntu
---

### Post by RedStarYellowSun on 2010-06-28
I just wanted to update my Firefox with Ubuntuzilla, but it says that there is an update, but I have no permission to update it (or install any software at all). I have already set my user account (the ONLY user account in Ubuntu) to 'administrator', yet it still says that I have no permission. Why is this?

And why only now? I have been using Ubuntu with Ubuntuzilla for a year at least, but, even with 'Custom' user account, I never had this problem. Am I doing something wrong?

Thanks for your time.

Take care,
RedStarYellowSun

---

### Post by nanotube on 2010-06-28
> **RedStarYellowSun said:**
> I just wanted to update my Firefox with Ubuntuzilla, but it says that there is an update, but I have no permission to update it (or install any software at all). I have already set my user account (the ONLY user account in Ubuntu) to 'administrator', yet it still says that I have no permission. Why is this?

And why only now? I have been using Ubuntu with Ubuntuzilla for a year at least, but, even with 'Custom' user account, I never had this problem. Am I doing something wrong?

how exactly are you trying to install software, that it tells you you have no permission?

---

### Post by mikewhatever on 2010-06-28
Don't you get asked for the admin password?

---

### Post by RedStarYellowSun on 2010-06-28
> **nanotube said:**
> how exactly are you trying to install software, that it tells you you have no permission?

Because of Ubuntuzilla:
"Applications">"Internet">"Mozilla Build of Firefox">"Help">"Check for Updates"

Result:
"Software Update
Unable to Update
A recommended security and stability update is available, but you do not have the system permissions required to update it. Please contact your administrator, or try again from an account that has permission to install software on this computer.

"You can always get the latest version of Firefox at:
[http://www.firefox.com](http://www.firefox.com)

> **mikewhatever said:**
> Don't you get asked for the admin password?
No. In updating Firefox, I never did after installing Ubuntuzilla.

Thanks for your time.

Take care,
RedStarYellowSun
"[OK]"

---

### Post by da burger on 2010-06-28
You need to update using apt (ubuntu's built in updater) if I'm not mistaken. Either go to a terminal and type ```
sudo apt-get update && sudo apt-get upgrade
``` then enter your password or if you prefer a GUI go to System>Admin>Update Manager and click check then upgrade.

Hope that helps
Angus

---

### Post by RedStarYellowSun on 2010-06-28
> **da burger said:**
> You need to update using apt (ubuntu's built in updater) if I'm not mistaken. Either go to a terminal and type ```
sudo apt-get update && sudo apt-get upgrade
``` then enter your password or if you prefer a GUI go to System>Admin>Update Manager and click check then upgrade.

Hope that helps
Angus

The feedback:
```
jutumang@jutumang-laptop:~$ sudo apt-get update && sudo apt-get upgrade
Hit http://archive.canonical.com lucid Release.gpg
Ign http://archive.canonical.com/ubuntu/ lucid/partner Translation-en_US
Hit http://us.archive.ubuntu.com lucid Release.gpg                  
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/main Translation-en_US
Hit http://security.ubuntu.com lucid-security Release.gpg            
Ign http://security.ubuntu.com/ubuntu/ lucid-security/main Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ lucid-security/restricted Translation-en_US
Hit http://archive.canonical.com lucid Release                       
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/restricted Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/universe Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com lucid-updates Release.gpg
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/universe Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/multiverse Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ lucid-security/universe Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ lucid-security/multiverse Translation-en_US
Hit http://security.ubuntu.com lucid-security Release                
Hit http://us.archive.ubuntu.com lucid Release                       
Hit http://archive.canonical.com lucid/partner Packages                        
Hit http://us.archive.ubuntu.com lucid-updates Release               
Hit http://security.ubuntu.com lucid-security/main Packages                    
Hit http://archive.canonical.com lucid/partner Sources               
Hit http://us.archive.ubuntu.com lucid/main Packages
Hit http://us.archive.ubuntu.com lucid/restricted Packages
Hit http://us.archive.ubuntu.com lucid/main Sources
Hit http://us.archive.ubuntu.com lucid/restricted Sources
Hit http://us.archive.ubuntu.com lucid/universe Packages
Hit http://security.ubuntu.com lucid-security/restricted Packages
Hit http://security.ubuntu.com lucid-security/main Sources
Hit http://security.ubuntu.com lucid-security/restricted Sources
Hit http://security.ubuntu.com lucid-security/universe Packages
Hit http://us.archive.ubuntu.com lucid/universe Sources
Hit http://us.archive.ubuntu.com lucid/multiverse Packages
Hit http://us.archive.ubuntu.com lucid/multiverse Sources
Hit http://us.archive.ubuntu.com lucid-updates/main Packages
Hit http://us.archive.ubuntu.com lucid-updates/restricted Packages
Hit http://us.archive.ubuntu.com lucid-updates/main Sources
Hit http://security.ubuntu.com lucid-security/universe Sources
Hit http://security.ubuntu.com lucid-security/multiverse Packages
Hit http://security.ubuntu.com lucid-security/multiverse Sources
Hit http://us.archive.ubuntu.com lucid-updates/restricted Sources
Hit http://us.archive.ubuntu.com lucid-updates/universe Packages
Hit http://us.archive.ubuntu.com lucid-updates/universe Sources
Hit http://us.archive.ubuntu.com lucid-updates/multiverse Packages
Hit http://us.archive.ubuntu.com lucid-updates/multiverse Sources
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
jutumang@jutumang-laptop:~$
```

It doesn't seem to have installed anything and it seems to have had no effect. Is there something that can e don to make it install?

Take care,
RedStarYellowSun

---

### Post by da burger on 2010-06-28
I think you possibly need to just wait a while for it to update. Also could you just tell me what version number you get when you go to the about screen in firefox.

---

### Post by RedStarYellowSun on 2010-06-28
> **da burger said:**
> I think you possibly need to just wait a while for it to update. Also could you just tell me what version number you get when you go to the about screen in firefox.

As of now, I am using version 3.6.3, but they have already come up with 3.6.6.

Also, I was trying to create an executable editor file "/etc/cron.daily/ntpdate" to get ntpdate to update daily.
[https://help.ubuntu.com/9.04/serverguide/C/NTP.html](https://help.ubuntu.com/9.04/serverguide/C/NTP.html)

Unfortunately,  I cannot save the file because I "don't have the authorization". (How odd...)

Oh,well.

Thanks for trying anyway.

Take care,
RedStarYellowSun

---

### Post by mikewhatever on 2010-06-28
> **RedStarYellowSun said:**
> As of now, I am using version 3.6.3, but they have already come up with 3.6.6.

Also, I was trying to create an executable editor file "/etc/cron.daily/ntpdate" to get ntpdate to update daily.
[https://help.ubuntu.com/9.04/serverguide/C/NTP.html](https://help.ubuntu.com/9.04/serverguide/C/NTP.html)

Unfortunately,  I cannot save the file because I "don't have the authorization". (How odd...)

Oh,well.

Thanks for trying anyway.

Take care,
RedStarYellowSun

That's a different story altogether. You need to open the file with admin privileges like this:
```
gksudo gedit /etc/cron.daily/ntpdate
```
type or paste whatever you need, save and exit.

---

### Post by nanotube on 2010-06-28
> **RedStarYellowSun said:**
> <snip stuff>

you seem to have installed with the old script, or installed the .deb directly, instead of using the repository.

please follow the instructions for using the ubuntuzilla repository on the ubuntuzilla site:
[http://ubuntuzilla.sourceforge.net](http://ubuntuzilla.sourceforge.net)

---

### Post by RedStarYellowSun on 2010-06-28
> **mikewhatever said:**
> That's a different story altogether. You need to open the file with admin privileges like this:
```
gksudo gedit /etc/cron.daily/ntpdate
```
type or paste whatever you need, save and exit.

Thanks!

> **nanotube said:**
> you seem to have installed with the old script, or installed the .deb directly, instead of using the repository.

please follow the instructions for using the ubuntuzilla repository on the ubuntuzilla site:
[http://ubuntuzilla.sourceforge.net](http://ubuntuzilla.sourceforge.net)


I tried the things in the "Repository contents and package behavior" section, but this is the result:
```
jutumang@jutumang-laptop:~$ deb http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt all main
No command 'deb' found, did you mean:
 Command 'debc' from package 'devscripts' (main)
 Command 'derb' from package 'libicu-dev' (main)
 Command 'dab' from package 'bsdgames' (universe)
 Command 'debi' from package 'devscripts' (main)
deb: command not found
jutumang@jutumang-laptop:~$
```

One thing, though: After this, I tried to plow through the problem by removing and reinstalling the Firefox build. Now, due to the previous repository, I find the Firefox 3.6.6 in Update Manager. But, this is the result:

In 1 window:
"Changes applied
(-) Update is complete
Not all changes and updates succeeded. For further details of the failure, please expand the "Details panel bolow.
[-] Details
```
(Reading database ... 181952 files and directories currently installed.)
Preparing to replace firefox-mozilla-build 3.6.3-0ubuntu1 (using .../firefox-mozilla-build_3.6.6-0ubuntu1_i386.deb) ...
Unpacking replacement firefox-mozilla-build ...
dpkg: error processing /var/cache/apt/archives/firefox-mozilla-build_3.6.6-0ubuntu1_i386.deb (--unpack):
 trying to overwrite '/usr/bin/firefox', which is also in package firefox 0:3.6.3+nobinonly-0ubuntu4
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for desktop-file-utils ...
Processing triggers for python-support ...
Errors were encountered while provessing:
 /var/cache/apt/archives/firefox-mozilla-build_3.6.6-)ubuntu1_i386.deb
E: Subprocess /usr/bin/dpkg returned an error code (1)
A package failed to install. Trying to recover:
```
[Close]"
Note: I had to type this from the Update Manager window, so I may have made a mistake.

In another window:
"(-)An error occurred
The following details are provided
```
E: /var/cache/apt/archives/firefox-mozilla-build_3.6.6-0ubuntu1_i386.deb: trying to overwrite '/usr/bin/firefox', which is also in package firefox 0
```
[Close]"

Thanks for your time.

Take care,
RedStarYellowSun

---

### Post by nanotube on 2010-06-29
You have not read the instructions carefully enough.

> **RedStarYellowSun said:**
> 
I tried the things in the "Repository contents and package behavior" section, but this is the result:
```
jutumang@jutumang-laptop:~$ deb http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt all main
jutumang@jutumang-laptop:~$
```

this is not a command to run, but a repository to add to your sources.list.

> 
One thing, though: After this, I tried to plow through the problem by removing and reinstalling the Firefox build. Now, due to the previous repository, I find the Firefox 3.6.6 in Update Manager. But, this is the result:
<snip>
"(-)An error occurred
The following details are provided
```
E: /var/cache/apt/archives/firefox-mozilla-build_3.6.6-0ubuntu1_i386.deb: trying to overwrite '/usr/bin/firefox', which is also in package firefox 0
```

This is likely caused by you having installed earlier with the script. the instructions tell you to uninstall with the script before installing from the repo.

please post your output of ```
dpkg-divert --list
```

---

### Post by RedStarYellowSun on 2010-07-01
> **nanotube said:**
> You have not read the instructions carefully enough.


this is not a command to run, but a repository to add to your sources.list.


This is likely caused by you having installed earlier with the script. the instructions tell you to uninstall with the script before installing from the repo.

please post your output of ```
dpkg-divert --list
```

Sorry for the delay in response. We were out of the house.

Here is the response:
```
jutumang@jutumang-laptop:~$ dpkg-divert --list
diversion of /bin/sh to /bin/sh.distrib by dash
diversion of /usr/share/man/man1/sh.1.gz to /usr/share/man/man1/sh.distrib.1.gz by dash
diversion of /usr/share/dbus-1/services/org.freedesktop.Notifications.service to /usr/share/dbus-1/services/org.freedesktop.Notifications.service.notify-osd by notify-osd
diversion of /usr/bin/screen to /usr/bin/screen.real by screen-profiles
diversion of /usr/lib/gnupg/gpgkeys_curl to /usr/lib/gnupg/gpgkeys_curl.non_curl by gnupg-curl
diversion of /usr/lib/gnupg/gpgkeys_hkp to /usr/lib/gnupg/gpgkeys_hkp.non_curl by gnupg-curl
diversion of /usr/share/gnome-games/pixmaps/slot.svg to /usr/share/gnome-games/pixmaps/slot.svg.unbranded by branding-ubuntu
diversion of /usr/share/gnome-games/pixmaps/baize.png to /usr/share/gnome-games/pixmaps/baize.png.unbranded by branding-ubuntu
diversion of /usr/share/gnome-games/mahjongg/pixmaps/postmodern.svg to /usr/share/gnome-games/mahjongg/pixmaps/postmodern.svg.unbranded by branding-ubuntu
diversion of /usr/share/gnome-games/gnometris/pixmaps/gnometris.svg to /usr/share/gnome-games/gnometris/pixmaps/gnometris.svg.unbranded by branding-ubuntu
diversion of /usr/share/gnome-games-common/cards/gnomangelo_bitmap.svg to /usr/share/gnome-games-common/cards/gnomangelo_bitmap.svg.unbranded by branding-ubuntu
diversion of /usr/share/dict/words to /usr/share/dict/words.pre-dictionaries-common by dictionaries-common
jutumang@jutumang-laptop:~$
```

Unfortunately, when we got back, a family-member used the Update Manager, which attempted to update Firefox. The result is that whenever any Firefox (the "Firefox Web Browser" and the "Mozilla Build of Firefox") this appear in 2 windows;

The first:
[JavaScript Application]
! Exception in onLoad: TypeError: gBrowser is null
[OK]

The second:
XML Parsing Error: undefined entity
Location: chrome://browser/content/browser.xul
Line Number 31, Column 1:<window id="main-window"
^

_&#915;L* Sorry for the extra problem. Next time, I'll make a written notice.

Thanks for your time.

Take care,
RedStarYellowSun

---

