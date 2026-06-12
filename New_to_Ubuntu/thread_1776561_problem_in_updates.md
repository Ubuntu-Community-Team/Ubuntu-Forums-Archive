---
title: "problem in updates"
date: 2011-06-06
forum: New to Ubuntu
---

### Post by Mr.ALDO on 2011-06-06
when I update the GNOME 3.0 it give me the following error

> The package system is broken

Check if you are using third party repositories. If so disable them, since they are a common source of problems.
Furthermore run the following command in a Terminal: apt-get install -f
The following packages have unmet dependencies:

gnome-shell: Depends: gir1.2-mutter-3.0 (>= 3.0.0) but it is not installed
             Depends: libcamel1.2-19 (< 2.33) but 2.32.2-0ubuntu2 is installed
             Depends: libffi5 (>= 3.0.4) but 3.0.9-3ubuntu1 is installed
             Depends: libnspr4 (>= 4.7.0~1.9b1) but 4.8.7-0ubuntu1 is installed
             Depends: libnss3 (>= 3.12.2~rc1) but 3.12.9+ckbi-1.82-0ubuntu2 is installed
             Depends: libsqlite3-0 (>= 3.7.3) but 3.7.4-2ubuntu5 is installed
             Depends: libxfixes3 (>= 1:4.0.1) but 1:4.0.5-1ubuntu1 is installed
             Depends: gnome-themes-standard (>= 2.91) but it is not installed
and when run the command in terminal it gives

> E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
so what to do....I am a really absolute beginner 
thanx,
sorry for my bad English :)

---

### Post by Peter09 on 2011-06-06
You need to obtain admin privileges using 'sudo'

The command you need is

```
sudo apt-get install -f
```

---

### Post by Mr.ALDO on 2011-06-08
> **Peter09 said:**
> You need to obtain admin privileges using 'sudo'

The command you need is

```
sudo apt-get install -f
```

when I do this command this what came on... and ubuntu asked for a problem report to be sent...is this right ??
> Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  gir1.2-polkit-1.0 mesa-utils mutter-common gnome-shell gir1.2-gkbd-3.0
  gir1.2-mutter-2.91 gnome-user-share libmutter0 xulrunner-2.0-mozjs gjs
  gir1.2-telepathylogger-0.2 gir1.2-upowerglib-1.0 gnome-icon-theme-symbolic
  gir1.2-telepathyglib-0.12 libgjs0b gir1.2-mutter-3.0 gnome-themes-standard
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  gir1.2-mutter-3.0 gnome-themes-standard
The following NEW packages will be installed:
  gir1.2-mutter-3.0 gnome-themes-standard
0 upgraded, 2 newly installed, 0 to remove and 110 not upgraded.
1 not fully installed or removed.
Need to get 0 B/1002 kB of archives.
After this operation, 6214 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  gnome-themes-standard
Install these packages without verification [y/N]? y
(Reading database ... 234722 files and directories currently installed.)
Unpacking gir1.2-mutter-3.0 (from .../gir1.2-mutter-3.0_3.0.0-0ubuntu1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/gir1.2-mutter-3.0_3.0.0-0ubuntu1_i386.deb (--unpack):
 trying to overwrite '/usr/lib/mutter/Meta-3.0.typelib', which is also in package gir1.2-mutter-2.91 3.0.0-0ubuntu1~build1
Unpacking gnome-themes-standard (from .../gnome-themes-standard_3.0.0-1~~build1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/gnome-themes-standard_3.0.0-1~~build1_i386.deb (--unpack):
 trying to overwrite '/usr/share/themes/HighContrastInverse/index.theme', which is also in package gnome-accessibility-themes 3.0.0-0ubuntu1~build1
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/gir1.2-mutter-3.0_3.0.0-0ubuntu1_i386.deb
 /var/cache/apt/archives/gnome-themes-standard_3.0.0-1~~build1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


---

### Post by Mr.ALDO on 2011-06-08
OH...and I remembered that I tried to install GNOME 3.0 in the previous theme that had the panel on the left but I stopped middle way and installed the official update and that problem came in.........an suggestions what to do ??

---

