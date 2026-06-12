---
title: "Update Error : E: Sub-process /usr/bin/dpkg exited unexpectedly"
date: 2010-06-26
forum: New to Ubuntu
---

### Post by udayspatel on 2010-06-26
Hi,

[COLOR="Blue"]I have recently re-installed Linux as the main OS on my PC. I have been using it for the last 8-10 days. Here's an error that popped up all of  a sudden while trying to update packages through synaptics
[/COLOR]
**[COLOR="Red"]E: Sub-process /usr/bin/dpkg exited unexpectedly[/COLOR]**

[COLOR="Blue"]I checked various threads and tried commands suggested by them.. Here is a list of commands I tried. The sequence may not be accurate.

[COLOR="Black"][I]sudo apt-get install build-essential
sudo apt-get --purge remove aptitude
sudo aptitude update
sudo apt-get install aptitude
sudo apt-get -f upgrade
sudo dpkg -P humanity-icon-theme
sudo dpkg --reconfigure -a
sudo apt-get -f install
sudo dpkg --configure --force-configure-any -a
sudo dpkg --configure -a
apt-get upgrade
apt-get update
sudo dpkg -clean-avail[/I][/COLOR]

This is what I get as error no matter what I try. Both from command prompt and through synaptics

[SIZE="2"][FONT="Times New Roman"][COLOR="Black"]Writing extended state information... Done
(Reading database ... 126116 files and directories currently installed.)
Preparing to replace humanity-icon-theme 0.5.2 (using .../humanity-icon-theme_0.5.2_all.deb) ...
Unpacking replacement humanity-icon-theme ...
dpkg: ../../src/archives.c:763: tarobject: Assertion `r == stab.st_size' failed.
E: Sub-process /usr/bin/dpkg exited unexpectedly
A package failed to install.  Trying to recover:[/COLOR][/FONT][/SIZE]


Finally I learned from one of the threads that this file may be useful for person answering my issue "cat /etc/apt/sources.list"[/COLOR]

[SIZE="2"][FONT="Times New Roman"]yudi@yudi-desktop:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)]/ lucid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid-updates main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid universe
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid-updates universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid multiverse
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid-updates multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security multiverse
deb [http://archive.canonical.com/](http://archive.canonical.com/) lucid partner
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security multiverse[/FONT][/SIZE]

[COLOR="Blue"]Please help me with the issue. Thanks in advance.[/COLOR]

---

### Post by xtremesupremacy3 on 2010-06-26
Hey there, well I am willing to try and help with your problem, but it might take a few attempts.

Thanks for the sources list. That is a list of basically all the places that Ubuntu will get software from (when they dont have a # in front of it, otherwise it will be ignore). It looks like theres double entries for me, but I will ignore that for the moment being.

Sounds to me like the last install before this one went wrong, let's try and sort that out.

Click on System > Administration > Synaptic Package Manager.

Then click on Edit > Fix broken packages, after that, click Reload.

Then try installing it again, let me know how you get on

EDIT: Upon further examination, your sources list is just fine, no double entries

---

### Post by philinux on 2010-06-26
@udayspatel, Your apt cache has got corrupted.

Use gksu nautilus or mv to trash and remove the two bin files located here.


ls /var/cache/apt/*.bin
/var/cache/apt/pkgcache.bin  /var/cache/apt/srcpkgcache.bin

Then.

```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by udayspatel on 2010-06-27
> **xtremesupremacy3 said:**
> Hey there, well I am willing to try and help with your problem, but it might take a few attempts.

Thanks for the sources list. That is a list of basically all the places that Ubuntu will get software from (when they dont have a # in front of it, otherwise it will be ignore). It looks like theres double entries for me, but I will ignore that for the moment being.

Sounds to me like the last install before this one went wrong, let's try and sort that out.

Click on System > Administration > Synaptic Package Manager.

Then click on Edit > Fix broken packages, after that, click Reload.

Then try installing it again, let me know how you get on

EDIT: Upon further examination, your sources list is just fine, no double entries

[COLOR="Blue"]Thanks for your help mate,..
I tried the steps mentioned by you but it does not seem to have worked.

I get the following status update when I run fix.
By the way what should I do when you say try installing it again?[/COLOR]
[FONT="Times New Roman"][COLOR="Black"][SIZE="2"]30183 packages listed, 1298 installed, 0 broken, 0 to install/upgrade, 0 to remove[/SIZE][/COLOR][/FONT]

---

### Post by udayspatel on 2010-06-27
> **philinux said:**
> @udayspatel, Your apt cache has got corrupted.

Use gksu nautilus or mv to trash and remove the two bin files located here.


ls /var/cache/apt/*.bin
/var/cache/apt/pkgcache.bin  /var/cache/apt/srcpkgcache.bin

Then.

```
sudo apt-get update && sudo apt-get upgrade
```

[COLOR="Blue"]Thanks for pitching in for a help.

I get the following error when I try to delete the files. [/COLOR]

[SIZE="2"][FONT="Times New Roman"]
"**Cannot move items to the deleted items folder, do you want to delete them immediately?**
None of the 2 selected items can be moved to trash"[/FONT][/SIZE]

[COLOR="Blue"]I still get the same error after using the command suggested by you..
Here are the last few lines of the error.[/COLOR]

[SIZE="2"][FONT="Times New Roman"]80 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
1 not fully installed or removed.
Need to get 0B/92.3MB of archives.
After this operation, 492kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Extract templates from packages: 100%
Preconfiguring packages ...
(Reading database ... 126116 files and directories currently installed.)
Preparing to replace humanity-icon-theme 0.5.2 (using .../humanity-icon-theme_0.5.2.1_all.deb) ...
Unpacking replacement humanity-icon-theme ...
dpkg: ../../src/archives.c:763: tarobject: Assertion `r == stab.st_size' failed.
E: Sub-process /usr/bin/dpkg exited unexpectedly[/FONT][/SIZE]
[COLOR="Blue"]
I Look forward for your reply.[/COLOR]

---

### Post by udayspatel on 2010-06-27
[QUOTE=udayspatel;9516711][COLOR="Blue"]Thanks for pitching in for a help.

I get the following error when I try to delete the files. so I removed them through "sudo rm" command in terminal window.[/COLOR]

[SIZE="2"][FONT="Times New Roman"]
"**Cannot move items to the deleted items folder, do you want to delete them immediately?**
None of the 2 selected items can be moved to trash"[/FONT][/SIZE]

[COLOR="Blue"]After removing file through terminal window and using your command. I still get the same error after using the command suggested by you..
Here are the last few lines of the error.[/COLOR]

[SIZE="2"][FONT="Times New Roman"]80 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
1 not fully installed or removed.
Need to get 0B/92.3MB of archives.
After this operation, 492kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Extract templates from packages: 100%
Preconfiguring packages ...
(Reading database ... 126116 files and directories currently installed.)
Preparing to replace humanity-icon-theme 0.5.2 (using .../humanity-icon-theme_0.5.2.1_all.deb) ...
Unpacking replacement humanity-icon-theme ...
dpkg: ../../src/archives.c:763: tarobject: Assertion `r == stab.st_size' failed.
E: Sub-process /usr/bin/dpkg exited unexpectedly[/FONT][/SIZE]
[COLOR="Blue"]
I Look forward for your reply.[/COLOR]

---

### Post by philinux on 2010-06-27
Use this then.

```
gksu nautilus
``` To delete the two files.

This is the root file browser so be careful.

---

### Post by udayspatel on 2010-06-27
Hi Phil,

I did delete the files through command prompt(terminal Window) and tried the command provided by you, but still get the same error.

---

### Post by udayspatel on 2010-06-27
Hi Phil,

I did delete the files through command prompt(terminal Window) and tried the command provided by you, but still get the same error.

---

### Post by philinux on 2010-06-27
```
sudo apt-get update && sudo apt-get upgrade
```

Post back the full error list, and please stop double posting/bumping thanks.

---

### Post by udayspatel on 2010-06-27
HI Phil,

I tried the command after deleting files and gave me this error 
"E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem." 

So I ran the command " sudo dpkg --configure -a"

and then ran "sudo apt-get update && sudo apt-get upgrade"

But I still get the same error that I posted in my first reply to you.

---

### Post by udayspatel on 2010-06-27
[COLOR="Blue"]Here is the full error list.[/COLOR]

[COLOR="Black"][SIZE="2"][FONT="Times New Roman"]yudi@yudi-desktop:~$ sudo apt-get update && sudo apt-get upgrade
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid Release.gpg
Hit [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid/main Translation-en_GB          
Hit [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_GB    
Hit [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_GB      
Hit [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_GB    
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid-updates Release.gpg                     
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_GB  
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en_GB
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_GB
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-en_GB
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release.gpg                     
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main Translation-en_GB  
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid Release                       
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release.gpg                   
Ign [http://archive.canonical.com/](http://archive.canonical.com/) lucid/partner Translation-en_GB    
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_GB
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en_GB
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release                          
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid-updates Release               
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release                                 
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid/main Packages                           
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid/restricted Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid/main Sources                  
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid/restricted Sources            
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid/universe Packages             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Packages          
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Packages              
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid/universe Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid/multiverse Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid/multiverse Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid-updates/main Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid-updates/restricted Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid-updates/main Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid-updates/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid-updates/universe Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid-updates/universe Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid-updates/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid-updates/multiverse Sources
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  linux-headers-generic
The following packages will be upgraded:
  empathy empathy-common fglrx-modaliases gdm humanity-icon-theme
  indicator-applet indicator-applet-session indicator-sound jockey-common
  jockey-gtk language-selector language-selector-common libcairomm-1.0-1
  libgdata-common libgdata6 libgl1-mesa-dri libglib2.0-data libglibmm-2.4-1c2a
  libglu1-mesa libgtk2.0-bin libgtkmm-2.4-1c2a libido-0.1-0 liblircclient0
  libpam-gnome-keyring libpangomm-1.4-1 libparted0debian1 libsdl1.2debian
  libsdl1.2debian-pulseaudio libsnmp-base libsnmp15 linux-generic
  linux-image-generic nautilus nautilus-data nautilus-sendto-empathy
  nvidia-current-modaliases obexd-client openoffice.org-base-core
  openoffice.org-calc openoffice.org-common openoffice.org-core
  openoffice.org-draw openoffice.org-gnome openoffice.org-gtk
  openoffice.org-impress openoffice.org-math openoffice.org-style-human
  openoffice.org-writer parted pm-utils pm-utils-powersave-policy
  python-cupshelpers python-papyon python-ubuntuone-client python-uno
  rhythmbox rhythmbox-plugin-cdrecorder rhythmbox-plugins simple-scan
  software-center ssh-askpass-gnome system-config-printer-common
  system-config-printer-gnome system-config-printer-udev telepathy-butterfly
  tomboy totem totem-common totem-mozilla totem-plugins transmission-common
  transmission-gtk ttf-opensymbol ubuntuone-client ubuntuone-client-gnome
  udisks unattended-upgrades vinagre xserver-common xserver-xorg-core
80 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
1 not fully installed or removed.
Need to get 0B/92.3MB of archives.
After this operation, 492kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Extract templates from packages: 100%
Preconfiguring packages ...
(Reading database ... 126116 files and directories currently installed.)
Preparing to replace humanity-icon-theme 0.5.2 (using .../humanity-icon-theme_0.5.2.1_all.deb) ...
Unpacking replacement humanity-icon-theme ...
dpkg: ../../src/archives.c:763: tarobject: Assertion `r == stab.st_size' failed.
E: Sub-process /usr/bin/dpkg exited unexpectedly[/FONT][/SIZE][/COLOR]

---

### Post by philinux on 2010-06-27
> Preparing to replace humanity-icon-theme 0.5.2 (using .../humanity-icon-theme_0.5.2.1_all.deb) ...
Unpacking replacement **[COLOR="Red"]humanity-icon-theme[/COLOR]** ...
dpkg: ../../src/archives.c:763: tarobject: Assertion `r == stab.st_size' failed.
E: Sub-process /usr/bin/dpkg exited unexpectedly

This package is the problem.

What does

```
sudo dpkg --configure -a
```

Spit out.

---

### Post by udayspatel on 2010-06-27
I ran the command " sudo dpkg --configure -a"

and then ran "sudo apt-get update && sudo apt-get upgrade"

But I still get the same error that I posted in my first reply to you

---

### Post by udayspatel on 2010-06-27
sudo dpkg --configure -a
does not give any output. I think it runs in the background to correct some issue. Only after I run sudo dpkg --configure -a can i run the command provided by you else the system asks me to run sudo dpkg --configure -a if I run any other update command

---

### Post by philinux on 2010-06-27
```
sudo apt-get purge humanity-icon-theme

then

sudo apt-get install humanity-icon-theme
```

---

### Post by udayspatel on 2010-06-27
Hi Phil,
[COLOR="Blue"]
I tried the command suggested.
Here's what I get with the first command[/COLOR]

[COLOR="Black"][SIZE="2"][FONT="Times New Roman"]Building dependency tree       
Reading state information... Done
The following packages will be REMOVED
  gnome-themes-ubuntu* humanity-icon-theme light-themes* ubuntu-artwork*
  ubuntu-desktop* ubuntu-mono*
0 upgraded, 0 newly installed, 6 to remove and 80 not upgraded.
1 not fully installed or removed.
After this operation, 34.0MB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 126115 files and directories currently installed.)
Removing ubuntu-desktop ...
Removing ubuntu-artwork ...
Purging configuration files for ubuntu-artwork ...
Removing light-themes ...
Purging configuration files for light-themes ...
Removing ubuntu-mono ...
Purging configuration files for ubuntu-mono ...
Removing gnome-themes-ubuntu ...
Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_GB.utf8.cache...
Processing triggers for hicolor-icon-theme ...
Processing triggers for python-support ...
dpkg: error processing humanity-icon-theme (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 humanity-icon-theme
E: Sub-process /usr/bin/dpkg returned an error code (1)[/FONT][/SIZE][/COLOR]


[COLOR="Blue"]So then I gave the second command and mentioned below is output for the same.
[/COLOR]
[COLOR="Black"][FONT="Times New Roman"][SIZE="2"]yudi@yudi-desktop:~$ sudo apt-get install humanity-icon-theme
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  humanity-icon-theme
1 upgraded, 0 newly installed, 0 to remove and 80 not upgraded.
1 not fully installed or removed.
Need to get 0B/3,689kB of archives.
After this operation, 106kB of additional disk space will be used.
Selecting previously deselected package humanity-icon-theme.
(Reading database ... 123954 files and directories currently installed.)
Preparing to replace humanity-icon-theme 0.5.2 (using .../humanity-icon-theme_0.5.2.1_all.deb) ...
Unpacking replacement humanity-icon-theme ...
dpkg: ../../src/archives.c:763: tarobject: Assertion `r == stab.st_size' failed.
E: Sub-process /usr/bin/dpkg exited unexpectedly[/SIZE][/FONT][/COLOR]

---

### Post by philinux on 2010-06-27
[http://ubuntuforums.org/showpost.php?p=2728028&postcount=4](http://ubuntuforums.org/showpost.php?p=2728028&postcount=4)

Be sure to use gksu gedit though.

Substitute for your errant package [COLOR="Blue"]humanity-icon-theme[/COLOR]

---

### Post by drs305 on 2010-06-27
It may be time to just get rid of the installation files manually. Open a file browser as root and go to /var/lib/dpkg/info:
```
gksu nautilus /var/lib/dpkg/info
```
Find the humanity-icon-theme files (there should be 4). Move them, rename or delete them. The first two will allow you to restore them if necessary.

You can see if that fixes things. If not, open /var/lib/dpkg/status. Make a backup of the file, find "Package: humanity-icon-theme" and delete the entire section.
```
sudo cp /var/lib/dpgk/status /var/lib/dpkg/status.bak
gksu gedit /var/lib/dpkg/status
```

This is not an 'elegant' solution but may finally rid you of the error messages, at which time you should reinstall the theme. If this doesn't fix the problem I would restore all the files to their original status so you are back to known values.

---

### Post by udayspatel on 2010-06-27
Hi Phil/DRS

I have removed the file from "gksu nautilus /var/lib/dpkg/info" and also deleted the section in file gksu gedit /var/lib/dpkg/status for Humanity-icon-theme.

What should be the next step from here?
Should I try to update + upgrade my packages?

---

### Post by udayspatel on 2010-06-27
[COLOR="Sienna"]Problem solved!!!
You guys rock man!
This is the best forum I've ever come across[/COLOR]

[COLOR="Blue"]Phil/DRS
The humanity-icon-theme issue is now resolved after removing all files from the folder and deleting entries in status file.[/COLOR]
[COLOR="Blue"]
After that I ran the command for upgrade[/COLOR]
"*sudo apt-get update && sudo apt-get upgrade*"


[COLOR="Blue"]It ran successfully for all items except a couple of them which are mentioned below.
Should I follow similar steps for them as I did for humanity icon theme?[/COLOR]
"[COLOR="Black"][SIZE="2"][FONT="Times New Roman"]E: /var/cache/apt/archives/openoffice.org-draw_1%3a3.2.0-7ubuntu4.1_i386.deb: short read in buffer_copy (backend dpkg-deb during `./usr/lib/openoffice/basis3.2/program/libsdli.so')
E: /var/cache/apt/archives/openoffice.org-core_1%3a3.2.0-7ubuntu4.1_i386.deb: conflicting packages - not installing openoffice.org-core[/FONT][/SIZE][/COLOR]"

---

### Post by udayspatel on 2010-06-27
Hurray!!!
THe problem is now resolved

I ran the following set of commands and it successfully updated openoffice

$ sudo apt-get clean
$ sudo apt-get update
$ sudo apt-get upgrade
$ sudo apt-get -f install

Thanks for your help througout this thread..

---

### Post by drs305 on 2010-06-27
udayspatel,

Glad you solved your problem. APT problems can really be stubborn ones to correct.

Would you please mark the thread 'Solved'. You do this via the "Thread Tools" link at the top right of the first post. It lets helpers concentrate on unresolved issues and also provides users looking for solutions a hint that an answer may be contained in the thread.

---

### Post by udayspatel on 2010-07-10
Hello DRS
You are right. I should have come back to mark this as solved so that experts can focus on unsolved threads. 
Please accept my apologies. I'll take care in the future.

---

### Post by Vege 4wd on 2010-07-10
Hi I am jumping on the thread because I have a similar problem but cannot find a error. 
My error report as in post #12 is:

Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid Release.gpg                             
Hit [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) lucid/main Translation-en_AU          
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release.gpg                             
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) lucid/partner Translation-en_AU       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                                 
Ign [http://ppa.launchpad.net/dtl131/ppa/ubuntu/](http://ppa.launchpad.net/dtl131/ppa/ubuntu/) lucid/main Translation-en_AU   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release.gpg                      
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main Translation-en_AU   
Hit [http://download.virtualbox.org](http://download.virtualbox.org) lucid Release.gpg                           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid Release.gpg                                
Hit [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_AU    
Ign [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_AU      
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release                                 
Ign [http://download.virtualbox.org/virtualbox/debian/](http://download.virtualbox.org/virtualbox/debian/) lucid/non-free Translation-en_AU
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                     
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_AU
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_AU
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en_AU
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release                          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid Release                                    
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Packages                        
Hit [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_AU    
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid-updates Release.gpg                     
Hit [http://download.virtualbox.org](http://download.virtualbox.org) lucid Release                               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Packages                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/main Sources                               
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Sources                         
Ign [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_AU  
Hit [http://download.virtualbox.org](http://download.virtualbox.org) lucid/non-free Packages           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/restricted Sources                         
Ign [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en_AU
Ign [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_AU
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Packages              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Sources               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Sources                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Sources               
Ign [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-en_AU
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Sources                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid Release 
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid-updates Release
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid/main Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid/restricted Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid/restricted Sources
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid/main Sources
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid/multiverse Sources
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid/universe Sources
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid/universe Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid/multiverse Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid-updates/main Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid-updates/restricted Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid-updates/restricted Sources
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid-updates/main Sources
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid-updates/multiverse Sources
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid-updates/universe Sources
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid-updates/universe Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid-updates/multiverse Packages
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
aaron@aaron-laptop:~$ 

I am fairly new with ubuntu and I cannot see a error. Any help would be greatly apprieciated.

---

### Post by philinux on 2010-07-10
vege 4wd,

Start a new thread with a title that **explains your problem**. As you say there are no errors reported in the above post.

---

### Post by linuxrev on 2011-11-05
Thanks for your unelegant trick, Drs305 (post #19). It solved a similar problem on my system!

-- 
linuxrev

---

