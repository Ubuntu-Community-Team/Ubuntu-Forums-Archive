---
title: "Install Ubuntu desktop"
date: 2011-06-11
forum: New to Ubuntu
---

### Post by ssdt on 2011-06-11
I am trying to install ubuntu desktop with the command:

sudo apt-get -f install ubuntu-desktop

and I get this :


Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 ubuntu-desktop : Depends: gnome-applets but it is not going to be installed
                  Depends: language-selector-gnome but it is not going to be installed
                  Depends: software-center but it is not going to be installed
                  Depends: software-properties-gtk but it is not going to be installed
                  Recommends: apport-gtk but it is not going to be installed
                  Recommends: computer-janitor-gtk but it is not going to be installed
                  Recommends: jockey-gtk but it is not going to be installed
E: Broken packages


Any idea on how to fix this?

---

### Post by gandaran on 2011-06-11
what desktop do you installed? KDE? and what ubuntu version?

---

### Post by philinux on 2011-06-11
@ssdt,

just run this and post back.

```
sudo apt-get install -f
```

---

### Post by VOT Productions on 2011-06-11
Try sudo apt-get install ubuntu-desktop

---

### Post by ssdt on 2011-06-11
Here is the output: 

sudo apt-get install -f
[sudo] password for datta: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


Nothing seems to be wrong with this.

---

### Post by kroq-gar78 on 2011-06-11
maybe

```
sudo dpkg --configure -a
```? not sure what the difference between this and apt-get install -f, but try it. Never have had that command break any of my 4 systems, so should be safe (as in "nothing to lose")

Also, just do 
```
sudo apt-get update
```in case

---

### Post by jtarin on 2011-06-11
> **ssdt said:**
> Here is the output: 

sudo apt-get install -f
[sudo] password for datta: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


Nothing seems to be wrong with this.According to your profile you have 10.04 Lucid Lynx installed already. That is why it won't install.....if your profile is accurate.

---

### Post by 3rdalbum on 2011-06-11
Have you got any "held" or locked packages in Synaptic? Also, have you done a 'sudo apt-get update' recently? (you should try this if you haven't already).

---

### Post by ssdt on 2011-06-12
@kroq-gar78, this is the output:
```

update-rc.d: warning: /etc/init.d/acpi-support missing LSB information
update-rc.d: see <http://wiki.debian.org/LSBInitScripts>
acpid stop/waiting
acpid start/running, process 2898
No LSB modules are available.
^[
^CNo LSB modules are available.
Unknown media type in type 'virtual/bluedevil-input'
Unknown media type in type 'virtual/bluedevil-audio'
Unknown media type in type 'virtual/bluedevil-sendfile'
Unknown media type in type 'all/all'
Unknown media type in type 'all/allfiles'
Unknown media type in type 'uri/mms'
Unknown media type in type 'uri/mmst'
Unknown media type in type 'uri/mmsu'
Unknown media type in type 'uri/pnm'
Unknown media type in type 'uri/rtspt'
Unknown media type in type 'uri/rtspu'
Unknown media type in type 'interface/x-winamp-skin'
dpkg-maintscript-helper: warning: environment variable DPKG_MAINTSCRIPT_NAME missing
dpkg-maintscript-helper: warning: environment variable DPKG_MAINTSCRIPT_PACKAGE missing
 * Starting AppArmor profiles                                                   Skipping profile in /etc/apparmor.d/disable: usr.bin.firefox
                                                                         [ OK ]
 * Reloading AppArmor profiles                                                  Skipping profile in /etc/apparmor.d/disable: usr.bin.firefox
                                                                         [ OK ]
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service apport stop

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the stop(8) utility, e.g. stop apport
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service apport start

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the start(8) utility, e.g. start apport
start: Job failed to start
invoke-rc.d: initscript apport, action "start" failed.
Unknown media type in type 'virtual/bluedevil-input'
Unknown media type in type 'virtual/bluedevil-audio'
Unknown media type in type 'virtual/bluedevil-sendfile'
Unknown media type in type 'all/all'
Unknown media type in type 'all/allfiles'
Unknown media type in type 'uri/mms'
Unknown media type in type 'uri/mmst'
Unknown media type in type 'uri/mmsu'
Unknown media type in type 'uri/pnm'
Unknown media type in type 'uri/rtspt'
Unknown media type in type 'uri/rtspu'
Unknown media type in type 'interface/x-winamp-skin'
gpg: key 437D05B5: "Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>" not changed
gpg: key FBB75451: "Ubuntu CD Image Automatic Signing Key <cdimage@ubuntu.com>" not changed
gpg: Total number processed: 2
gpg:              unchanged: 2
atd stop/waiting
atd start/running, process 8470
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service avahi-daemon stop

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the stop(8) utility, e.g. stop avahi-daemon
avahi-daemon stop/waiting
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service dbus force-reload

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the reload(8) utility, e.g. reload dbus
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service avahi-daemon start

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the start(8) utility, e.g. start avahi-daemon
avahi-daemon start/running, process 8549
update-alternatives: warning: alternative /usr/bin/avidemux2_gtk (part of link group avidemux) doesn't exist. Removing from list of alternatives.
update-alternatives: warning: /etc/alternatives/avidemux is dangling, it will be updated with best choice.
update-alternatives: using /usr/bin/avidemux2_qt4 to provide /usr/bin/avidemux (avidemux) in auto mode.
update-alternatives: using /usr/share/man/man7/bash-builtins.7.gz to provide /usr/share/man/man7/builtins.7.gz (builtins.7.gz) in auto mode.
 * Disabling additional executable binary formats binfmt-support         [ OK ] 
 * Enabling additional executable binary formats binfmt-support          [ OK ] 
Unknown media type in type 'virtual/bluedevil-input'
Unknown media type in type 'virtual/bluedevil-audio'
Unknown media type in type 'virtual/bluedevil-sendfile'
Unknown media type in type 'all/all'
Unknown media type in type 'all/allfiles'
Unknown media type in type 'uri/mms'
Unknown media type in type 'uri/mmst'
Unknown media type in type 'uri/mmsu'
Unknown media type in type 'uri/pnm'
Unknown media type in type 'uri/rtspt'
Unknown media type in type 'uri/rtspu'
Unknown media type in type 'interface/x-winamp-skin'
 * Stopping bluetooth                                                    [ OK ] 
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service dbus force-reload

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the reload(8) utility, e.g. reload dbus
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service udev reload

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the reload(8) utility, e.g. reload udev
 * Starting bluetooth                                                    [ OK ] 
update-initramfs: Generating /boot/initrd.img-2.6.38-8-generic
Updating certificates in /etc/ssl/certs... 0 added, 0 removed; done.
Running hooks in /etc/ca-certificates/update.d....
updating keystore /etc/ssl/certs/java/cacerts...
done.
done.
Your console font configuration will be updated the next time your system
boots. If you want to update it now, run 'setupcon' from a virtual console.
update-initramfs: Generating /boot/initrd.img-2.6.38-8-generic
cron stop/waiting
dpkg-maintscript-helper: error: couldn't identify the package

```

And it still does not work.

And this is the output for sudo apt-get update:

```
W: Failed to fetch cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1)/dists/natty/main/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1)/dists/natty/restricted/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

E: Some index files failed to download. They have been ignored, or old ones used instead.
```

And yes, I forgot to change my profile. I am using 11.04

---

### Post by VOT Productions on 2011-06-12
What if you do **sudo apt-get install ubuntu-desktop**?

---

### Post by jtarin on 2011-06-12
Was this a progressive upgrade then....from 10.10-11.04 or a jump from 10.04-11.04?

---

### Post by ssdt on 2011-06-12
sudo apt-get install ubuntu-desktop's output:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 ubuntu-desktop : Depends: gnome-applets but it is not going to be installed
                  Depends: language-selector-gnome but it is not going to be installed
                  Depends: software-center but it is not going to be installed
                  Depends: software-properties-gtk but it is not going to be installed
                  Recommends: apport-gtk but it is not going to be installed
                  Recommends: computer-janitor-gtk but it is not going to be installed
                  Recommends: jockey-gtk but it is not going to be installed
E: Broken packages

```

@jtrain: it was a progressive update where after I got to ubuntu 11.04, I went to KDE. Now it looks like many of the programs that I need to run can't be run without Gnome.

---

### Post by VOT Productions on 2011-06-12
To help narrowing it down, try **sudo apt-get install gnome-applets**.

---

### Post by raja.genupula on 2011-06-12
> **ssdt said:**
> @kroq-gar78, this is the output:
```

update-rc.d: warning: /etc/init.d/acpi-support missing LSB information
update-rc.d: see <http://wiki.debian.org/LSBInitScripts>
acpid stop/waiting
acpid start/running, process 2898
No LSB modules are available.
^[
^CNo LSB modules are available.
Unknown media type in type 'virtual/bluedevil-input'
Unknown media type in type 'virtual/bluedevil-audio'
Unknown media type in type 'virtual/bluedevil-sendfile'
Unknown media type in type 'all/all'
Unknown media type in type 'all/allfiles'
Unknown media type in type 'uri/mms'
Unknown media type in type 'uri/mmst'
Unknown media type in type 'uri/mmsu'
Unknown media type in type 'uri/pnm'
Unknown media type in type 'uri/rtspt'
Unknown media type in type 'uri/rtspu'
Unknown media type in type 'interface/x-winamp-skin'
dpkg-maintscript-helper: warning: environment variable DPKG_MAINTSCRIPT_NAME missing
dpkg-maintscript-helper: warning: environment variable DPKG_MAINTSCRIPT_PACKAGE missing
 * Starting AppArmor profiles                                                   Skipping profile in /etc/apparmor.d/disable: usr.bin.firefox
                                                                         [ OK ]
 * Reloading AppArmor profiles                                                  Skipping profile in /etc/apparmor.d/disable: usr.bin.firefox
                                                                         [ OK ]
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service apport stop

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the stop(8) utility, e.g. stop apport
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service apport start

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the start(8) utility, e.g. start apport
start: Job failed to start
invoke-rc.d: initscript apport, action "start" failed.
Unknown media type in type 'virtual/bluedevil-input'
Unknown media type in type 'virtual/bluedevil-audio'
Unknown media type in type 'virtual/bluedevil-sendfile'
Unknown media type in type 'all/all'
Unknown media type in type 'all/allfiles'
Unknown media type in type 'uri/mms'
Unknown media type in type 'uri/mmst'
Unknown media type in type 'uri/mmsu'
Unknown media type in type 'uri/pnm'
Unknown media type in type 'uri/rtspt'
Unknown media type in type 'uri/rtspu'
Unknown media type in type 'interface/x-winamp-skin'
gpg: key 437D05B5: "Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>" not changed
gpg: key FBB75451: "Ubuntu CD Image Automatic Signing Key <cdimage@ubuntu.com>" not changed
gpg: Total number processed: 2
gpg:              unchanged: 2
atd stop/waiting
atd start/running, process 8470
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service avahi-daemon stop

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the stop(8) utility, e.g. stop avahi-daemon
avahi-daemon stop/waiting
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service dbus force-reload

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the reload(8) utility, e.g. reload dbus
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service avahi-daemon start

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the start(8) utility, e.g. start avahi-daemon
avahi-daemon start/running, process 8549
update-alternatives: warning: alternative /usr/bin/avidemux2_gtk (part of link group avidemux) doesn't exist. Removing from list of alternatives.
update-alternatives: warning: /etc/alternatives/avidemux is dangling, it will be updated with best choice.
update-alternatives: using /usr/bin/avidemux2_qt4 to provide /usr/bin/avidemux (avidemux) in auto mode.
update-alternatives: using /usr/share/man/man7/bash-builtins.7.gz to provide /usr/share/man/man7/builtins.7.gz (builtins.7.gz) in auto mode.
 * Disabling additional executable binary formats binfmt-support         [ OK ] 
 * Enabling additional executable binary formats binfmt-support          [ OK ] 
Unknown media type in type 'virtual/bluedevil-input'
Unknown media type in type 'virtual/bluedevil-audio'
Unknown media type in type 'virtual/bluedevil-sendfile'
Unknown media type in type 'all/all'
Unknown media type in type 'all/allfiles'
Unknown media type in type 'uri/mms'
Unknown media type in type 'uri/mmst'
Unknown media type in type 'uri/mmsu'
Unknown media type in type 'uri/pnm'
Unknown media type in type 'uri/rtspt'
Unknown media type in type 'uri/rtspu'
Unknown media type in type 'interface/x-winamp-skin'
 * Stopping bluetooth                                                    [ OK ] 
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service dbus force-reload

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the reload(8) utility, e.g. reload dbus
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service udev reload

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the reload(8) utility, e.g. reload udev
 * Starting bluetooth                                                    [ OK ] 
update-initramfs: Generating /boot/initrd.img-2.6.38-8-generic
Updating certificates in /etc/ssl/certs... 0 added, 0 removed; done.
Running hooks in /etc/ca-certificates/update.d....
updating keystore /etc/ssl/certs/java/cacerts...
done.
done.
Your console font configuration will be updated the next time your system
boots. If you want to update it now, run 'setupcon' from a virtual console.
update-initramfs: Generating /boot/initrd.img-2.6.38-8-generic
cron stop/waiting
dpkg-maintscript-helper: error: couldn't identify the package

```And it still does not work.

And this is the output for sudo apt-get update:

```
W: Failed to fetch cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1)/dists/natty/main/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1)/dists/natty/restricted/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

E: Some index files failed to download. They have been ignored, or old ones used instead.
```And yes, I forgot to change my profile. I am using 11.04



do you select the Update Manager -->  settings -->  ubuntu software , do you select the cd-rom also ? 
if so then only you're going to get the output as above .

---

### Post by raja.genupula on 2011-06-12
execute this also , for the last line problem its going to helpful to you 

```

sudo rm -rf /var/lib/apt/lists/*


```
```
sudo apt-get update
```

---

### Post by VOT Productions on 2011-06-12
[B]sudo apt-get install gnome-applets
sudo apt-get install software-center
sudo apt-get install jockey-gtk
[/B][B]sudo apt-get install software-properties-gtk
[/B][B]sudo apt-get install language-selector-gnome
[/B][B]sudo apt-get install apport-gtk
[/B]**sudo apt-get install computer-janitor**

Please run the commands.

---

### Post by ssdt on 2011-06-12
Output of sudo apt-get install gnome-applets:

```
datta@datta-OM:~$ sudo apt-get install gnome-applets
[sudo] password for datta: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 gnome-applets : Depends: gir1.2-gtk-2.0 but it is not going to be installed
                 Depends: gir1.2-panelapplet-3.0 but it is not going to be installed
E: Broken packages

```

@raja.genupula, I see that the problem was from selecting the cd-rom. I deselected it but same problem.

sudo apt-get install gnome-applets output:

The following packages have unmet dependencies:
 gnome-applets : Depends: gir1.2-gtk-2.0 but it is not going to be installed
                 Depends: gir1.2-panelapplet-3.0 but it is not going to be installed
E: Broken packages

---

### Post by ssdt on 2011-06-12
> **VOT Productions said:**
> [B]sudo apt-get install gnome-applets
sudo apt-get install software-center
sudo apt-get install jockey-gtk
[/B][B]sudo apt-get install software-properties-gtk
[/B][B]sudo apt-get install language-selector-gnome
[/B][B]sudo apt-get install apport-gtk
[/B]**sudo apt-get install computer-janitor**

Please run the commands.

Output of all these. Only computer-janitor was installed:
```

datta@datta-OM:~$ sudo apt-get install gnome-applets
[sudo] password for datta: 
Sorry, try again.
[sudo] password for datta: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 gnome-applets : Depends: gir1.2-gtk-2.0 but it is not going to be installed
                 Depends: gir1.2-panelapplet-3.0 but it is not going to be installed
E: Broken packages
datta@datta-OM:~$ sudo apt-get install software-center
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 software-center : Depends: python-aptdaemon-gtk but it is not going to be installed
                   Recommends: software-properties-gtk but it is not going to be installed
                   Recommends: sessioninstaller but it is not going to be installed
E: Broken packages
datta@datta-OM:~$ sudo apt-get install jockey-gtk
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 jockey-gtk : Depends: gir1.2-gtk-2.0 (>= 2.23.90-0ubuntu2) but it is not going to be installed
              Depends: gir1.2-appindicator-0.1 but it is not going to be installed
E: Broken packages
datta@datta-OM:~$ 
datta@datta-OM:~$ sudo apt-get install software-properties-gtk
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 software-properties-gtk : Depends: gir1.2-gtk-2.0 (>= 2.23.90-0ubuntu3) but it is not going to be installed
E: Broken packages
datta@datta-OM:~$ 
datta@datta-OM:~$ sudo apt-get install language-selector-gnome
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 language-selector-gnome : Depends: gir1.2-gtk-2.0 (>= 2.23.90-0ubuntu3) but it is not going to be installed
                           Depends: gir1.2-vte-0.0 but it is not going to be installed
                           Depends: python-aptdaemon.gtk3widgets but it is not going to be installed
E: Broken packages
datta@datta-OM:~$ 
datta@datta-OM:~$ sudo apt-get install apport-gtk
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 apport-gtk : Depends: gir1.2-gtk-2.0 (>= 2.23.90-0ubuntu3) but it is not going to be installed
E: Broken packages
datta@datta-OM:~$ 
datta@datta-OM:~$ sudo apt-get install computer-janitor
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  python-argparse
Suggested packages:
  python-argparse-doc
The following NEW packages will be installed:
  computer-janitor python-argparse
0 upgraded, 2 newly installed, 0 to remove and 7 not upgraded.
Need to get 78.2 kB of archives.
After this operation, 643 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://us.archive.ubuntu.com/ubuntu/ natty/main python-argparse all 1.1-1 [43.4 kB]
Get:2 http://us.archive.ubuntu.com/ubuntu/ natty/main computer-janitor all 2.1.0-0ubuntu4 [34.9 kB]
Fetched 78.2 kB in 6s (12.7 kB/s)                                              
Selecting previously deselected package python-argparse.
(Reading database ... 88166 files and directories currently installed.)
Unpacking python-argparse (from .../python-argparse_1.1-1_all.deb) ...
Selecting previously deselected package computer-janitor.
Unpacking computer-janitor (from .../computer-janitor_2.1.0-0ubuntu4_all.deb) ...
Processing triggers for python-central ...
Processing triggers for man-db ...
Setting up python-argparse (1.1-1) ...
Setting up computer-janitor (2.1.0-0ubuntu4) ...
Processing triggers for python-support ...



```

---

### Post by VOT Productions on 2011-06-12
> **ssdt said:**
> Output of sudo apt-get install gnome-applets:

```
datta@datta-OM:~$ sudo apt-get install gnome-applets
[sudo] password for datta: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 gnome-applets : Depends: gir1.2-gtk-2.0 but it is not going to be installed
                 Depends: gir1.2-panelapplet-3.0 but it is not going to be installed
E: Broken packages

```

@raja.genupula, I see that the problem was from selecting the cd-rom. I deselected it but same problem.

sudo apt-get install gnome-applets output:

The following packages have unmet dependencies:
 gnome-applets : Depends: gir1.2-gtk-2.0 but it is not going to be installed
                 Depends: gir1.2-panelapplet-3.0 but it is not going to be installed
E: Broken packages

Try sudo apt-get install gir1.2-gtk-2.0. Also try the other commands too!

---

### Post by ssdt on 2011-06-12
Output of sudo apt-get install gir1.2-gtk-2.0:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 gir1.2-gtk-2.0 : Depends: gir1.2-freedesktop but it is not going to be installed
                  Depends: gir1.2-pango-1.0 but it is not going to be installed
E: Broken packages
```

Another output:

```

datta@datta-OM:~$ sudo apt-get install gir1.2-panelapplet-3.0
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 gir1.2-panelapplet-3.0 : Depends: gir1.2-freedesktop but it is not going to be installed
                          Depends: gir1.2-gtk-2.0 but it is not going to be installed
                          Depends: gir1.2-pango-1.0 but it is not going to be installed
E: Broken packages
```

---

### Post by ssdt on 2011-06-14
One alternative was to install gnome 3 and then I was able to install Ubuntu desktop.

I followed this tutorial: [http://news.softpedia.com/news/How-to-Install-GNOME-3-on-Ubuntu-11-04-194085.shtml](http://news.softpedia.com/news/How-to-Install-GNOME-3-on-Ubuntu-11-04-194085.shtml)

---

### Post by kroq-gar78 on 2011-06-14
Oh, also, sorry. I meant to say 'sudo dpkg --configure -a'. SORRY! I just realized it today. Good thing you found a solution though. Anyway...

I seemed to have a similar problem with my laptop. I think I fixed it SOMEHOW (abt 2months ago and I already forgot) and it was the same-ish thing, just not with ubuntu-desktop (I think it was some audio program I was trying to install).

Also, since you apparently found a solution, mark this thread as "solved" by going to "thread tools" at the top left of the 1st post on the page and click "Mark this thread as solved", or something similar to that.

Sincerely,
kroq-gar78

---

### Post by ssdt on 2011-06-15
Well, I did not find a solution to it but a workaround.
Now I ran your code and yeah, perfect match. It worked and now I can install ubuntu desktop.
So for later, anyone asking for the solution should do this:
```

sudo dpkg --configure -a

```
Works great and fine. And yeah, no problem with the mistake cause it's fixed.

---

### Post by collisionystm on 2011-06-15
> **ssdt said:**
> I am trying to install ubuntu desktop with the command:

sudo apt-get -f install ubuntu-desktop

and I get this :


Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 ubuntu-desktop : Depends: gnome-applets but it is not going to be installed
                  Depends: language-selector-gnome but it is not going to be installed
                  Depends: software-center but it is not going to be installed
                  Depends: software-properties-gtk but it is not going to be installed
                  Recommends: apport-gtk but it is not going to be installed
                  Recommends: computer-janitor-gtk but it is not going to be installed
                  Recommends: jockey-gtk but it is not going to be installed
E: Broken packages


Any idea on how to fix this?

```
sudo apt-get install tasksel
```

```
tasksel
```

---

