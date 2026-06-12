---
title: "flash 10 still missing in firefox"
date: 2009-02-03
forum: New to Ubuntu
---

### Post by Daverobb on 2009-02-03
Flash 9 (?) worked a bit buggy but worked.

I upgraded it to 10 after removing previous version (I believe) completely.

Now it won't work at all in firefox - firefox says it's missing but when I install it it says it's already installed?  

Any suggestions?

________________________
HArdy 8.04
2.6.24-23
GNOME 2.22.3

Athlon 32bit

---

### Post by Crafty Kisses on 2009-02-03
Go into Firefox, and type this in the navigation bar:
```
about:plguins
```
See if it's present.

---

### Post by Daverobb on 2009-02-03
not that i can see --

would it be listed as Adobe flash or something?

if it would be, it's not there

---

### Post by Crafty Kisses on 2009-02-03
I think it's labeled as "Shockwave Flash" I could be wrong though.

---

### Post by Daverobb on 2009-02-03
yeah - not there

---

### Post by Crafty Kisses on 2009-02-03
Alright, so try this:
```
sudo apt-get remove --purge flashplugin-nonfree
```
That's if you have that package installed, then try:
```
sudo apt-get install flashplugin-nonfree
```

---

### Post by Daverobb on 2009-02-03
This is what I get:

[HTML]$ sudo apt-get install flashplugin-nonfree
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  konqueror-nsplugins ttf-xfree86-nonfree xfs
The following NEW packages will be installed:
  flashplugin-nonfree
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/18.8kB of archives.
After this operation, 168kB of additional disk space will be used.
Preconfiguring packages ...
Selecting previously deselected package flashplugin-nonfree.
(Reading database ... 170392 files and directories currently installed.)
Unpacking flashplugin-nonfree (from .../flashplugin-nonfree_10.0.1.218+10.0.0.525ubuntu1~hardy1+really9.0.124.0ubuntu2_i386.deb) ...
Setting up flashplugin-nonfree (10.0.1.218+10.0.0.525ubuntu1~hardy1+really9.0.124.0ubuntu2) ...
Downloading...
--22:49:16--  http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz
           => `./install_flash_player_9_linux.tar.gz'
Resolving fpdownload.macromedia.com... 96.17.50.70
Connecting to fpdownload.macromedia.com|96.17.50.70|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
22:49:17 ERROR 404: Not Found.

download failed
The Flash plugin is NOT installed.
[/HTML]

---

### Post by Crafty Kisses on 2009-02-03
Hmmm, looks like the server you're trying to download it from is down.

---

### Post by Daverobb on 2009-02-03
guess i'll try tomorrow?

---

### Post by Crafty Kisses on 2009-02-03
You could technically download Flash from Adobe's website, right here: [http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/)

---

### Post by sandyd on 2009-02-03
correction:
if you noticed, hes downloading flash 9, not flash 10.
that could be why ;)

---

### Post by Crafty Kisses on 2009-02-03
That's weird, what version of Ubuntu are you running? From the looks of the Terminal log it looks like you maybe running Kubuntu, try and update your repos, because I could have sworn they put Flash 10 in the repos.

---

### Post by sandyd on 2009-02-03
download and installl the deb HERE :)
[http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/)

they got debs now 

happy day for all debian based distro users. :D:D:D:D:D:D:D

---

### Post by Daverobb on 2009-02-04
i purged and reinstalled using deb from the site (I've already done this tho a few times before) but to no avail -- doen't work in browser. 

I run ubuntu 8.04

---

### Post by Daverobb on 2009-02-04
if anyone can help me to work through this, that would be amazing

---

### Post by RomeReactor on 2009-02-04
Hi. Try finding where how many libflashplayer.so instances (if any) you have:
```
sudo updatedb
```
then:
```
locate libflashplayer.so
```
and post back the results. Are you running Ubuntu 32 bit, or 64? If you're unsure, run:
```
uname -m
```
if it reads **x86_64**, you have Ubuntu 64 bit.

---

### Post by Daverobb on 2009-02-04
locate is:

[HTML]/usr/lib/adobe-flashplugin/libflashplayer.so
[/HTML]

version is 32bit I assume from:

[HTML]uname -m
i686
[/HTML]

---

### Post by RomeReactor on 2009-02-04
Yes, that's 32-bit. Post the contents of these two folders:
```
ls ~/.mozilla/plugins
```
and
```
ls /usr/lib/mozilla/plugins
```

Also make sure you don't have Gnash installed (close Firefox first):
```
sudo aptitude purge gnash mozilla-plugin-gnash gnash-comon
```
Then re-open Firefox and see if there's any change.

---

### Post by Temposs on 2009-02-04
Note a typo. The last line of code should be:

```
sudo aptitude purge gnash mozilla-plugin-gnash gnash-common
```

---

### Post by Daverobb on 2009-02-04
[HTML]:~$ ls ~/.mozilla/plugins
ls: cannot access /home/dave/.mozilla/plugins: No such file or directory
dave@dave-desktop:~$ ls /usr/lib/mozilla/plugins
flashplugin-alternative.so  libjavaplugin.so
[/HTML]

also, gnash was installed; now purged

---

### Post by Daverobb on 2009-02-04
no change - firefox says 'missing plugin' for flash

---

### Post by Temposs on 2009-02-04
Now that gnash is uninstalled, try to install the flashplugin-nonfree package as was suggested in the earlier part of the thread.

---

### Post by RomeReactor on 2009-02-04
Check if nspluginwrapper is still installed (which it should be):
```
sudo aptitude install nspluginwrapper
```

Try deleting the **xpti** file in Firefox's folder (again, close Firefox first):
```
rm ~/.mozilla/firefox/*default/xpti.dat
```
Re-open Firefox.

---

### Post by Daverobb on 2009-02-04
ok -- reinstalled .deb flash ver 10 and restarted firefox 

-- no change - missing the plugin

then checked as follows:

[HTML]sudo aptitude install nspluginwrapper
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done             
Couldn't find any package whose name or description matched "nspluginwrapper"
Couldn't find any package whose name or description matched "nspluginwrapper"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done   [/HTML]

is it installed?

removed xpti file but no change to plugin status

---

### Post by Temposs on 2009-02-04
It's very strange that nspluginwrapper couldn't be found...it should definitely be in the repositories...If you open System->Administration->Software Sources, are all the checkboxes checked(except maybe "Source code")?

---

### Post by Daverobb on 2009-02-04
yes - all repos are checked

---

### Post by rajm11 on 2009-02-04
Okay I am facing the same problem,so followed the step

so i followed the posts and the instructions 
and after the last post this is what I came with. 

Command  used  sudo aptitude install nspluginwrapper

amol@Ubuntu-Server:~$ sudo aptitude install nspluginwrapper
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
Couldn't find any package whose name or description matched "nspluginwrapper"
Couldn't find any package whose name or description matched "nspluginwrapper"
The following packages have been kept back:.
....
0 packages upgraded, 0 newly installed, 0 to remove and 25 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done  

and here is use of rm command .

 rm ~/.mozilla/firefox/*default/xpti.dat
rm: cannot remove `/home/amol/.mozilla/firefox/*default/xpti.dat': No such file or directory

I still have no flash 9 or 10.

---

### Post by Daverobb on 2009-02-04
well it has something to do with the new version of flash because flash did work (altho not perfectly) before I 'updated\ through the adobe site

---

### Post by bwang on 2009-02-04
First, remove the old plugin:

```
sudo apt-get remove flashplugin-nonfree
```

Then restart your computer and try to install Flash 10.

---

### Post by Daverobb on 2009-02-04
this method of removing doesn't seem to remove the new install of flash (done through adobe site using deb installer)

I have done it previously using command ```
sudo apt-get remove adobe-flashplugin
```as well and it seemed to uninstall the new version but then reboot or new firefox window reinstall and --- still doesn't work!

---

### Post by shifty_powers on 2009-02-04
[http://fpdownload.macromedia.com/get/flashplayer/xpi/current/flashplayer-linux.xpi](http://fpdownload.macromedia.com/get/flashplayer/xpi/current/flashplayer-linux.xpi)

---

### Post by Daverobb on 2009-02-04
couldn't install because 'install script not found'

---

### Post by RomeReactor on 2009-02-04
According to this post from the second page:
> **Daverobb said:**
> [HTML]:~$ ls ~/.mozilla/plugins
ls: cannot access /home/dave/.mozilla/plugins: No such file or directory
dave@dave-desktop:~$ ls /usr/lib/mozilla/plugins
flashplugin-alternative.so  libjavaplugin.so
[/HTML]


You don't seem to have the **.mozilla/plugins** folder. Please verify this by pressing CTRL+H in Nautilus, in your home folder and checking whether the directory is there or not. What version of Firefox do you have? Is it the one from the repositories?

---

### Post by Daverobb on 2009-02-04
there is no plugins folder -- only /extensions and /firefox

firefox is Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.5) Gecko/2008121621 Ubuntu/8.04 (hardy) Firefox/3.0.5

don't know if it is originally from the repos

---

### Post by RomeReactor on 2009-02-04
Let's try this: 
```
gedit ~/Flash32
```
When it opens, paste the following there:
```
#!/bin/bash
aptitude -y purge flashplugin-nonfree nspluginwrapper
updatedb
for x in `locate libflashplayer.so`; do rm $x; done
wget http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_10_linux.tar.gz
tar -xvzf install_flash_player_10_linux.tar.gz
cp ~/install_flash_player_10_linux/libflashplayer.so /usr/lib/mozilla/plugins
rm ~/install_flash_player_10_linux.tar.gz
rm -R ~/install_flash_player_10_linux
```
then, make the script executable:
```
chmod +x Flash32
```
Now, we're going to backup the .mozilla directory so Firefox creates a new one when you start it up again, so backup your bookmarks first. Then close Firefox and run:
```
mv ~/.mozilla ~/mozilla_backup
```
And lastly, run the script:
```
sudo ./Flash32
```
When it finishes, open Firefox and check if Flash is detected.

---

### Post by Temposs on 2009-02-04
OK, something about this is screwy, so I'll give you a hackish way that I think will work...you should try to find a cleaner way to do this eventually, though.

Install the newest deb from adobe as you've done previously...then you'll have this file:

```
/usr/lib/adobe-flashplugin/libflashplayer.so
```

When you have that file, copy it like so:

```
sudo cp /usr/lib/adobe-flashplugin/libflashplayer.so /usr/lib/mozilla/plugins/
```

and

```
sudo cp /usr/lib/adobe-flashplugin/libflashplayer.so /usr/lib/firefox/plugins/
```

and

```
sudo cp /usr/lib/adobe-flashplugin/libflashplayer.so /usr/lib/firefox-addons/plugins/
```

Restart firefox and try flash.

EDIT: Try RomeReactor's way first, of course.

---

### Post by Daverobb on 2009-02-04
to RomeReactor --

didn't seem to work -- see script:

```
sudo ./Flash32
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done             
Couldn't find any package whose name or description matched "nspluginwrapper"
Couldn't find any package whose name or description matched "nspluginwrapper"
The following packages will be REMOVED:
  flashplugin-nonfree{p} 
0 packages upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
(Reading database ... 170468 files and directories currently installed.)
Removing flashplugin-nonfree ...
Purging configuration files for flashplugin-nonfree ...
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done             
--19:36:53--  http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_10_linux.tar.gz
           => `install_flash_player_10_linux.tar.gz'
Resolving fpdownload.macromedia.com... 96.17.34.70
Connecting to fpdownload.macromedia.com|96.17.34.70|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 3,962,157 (3.8M) [application/x-gzip]

100%[==========================>] 3,962,157     28.65K/s    ETA 00:00

19:39:03 (29.82 KB/s) - `install_flash_player_10_linux.tar.gz' saved [3962157/3962157]

install_flash_player_10_linux/
install_flash_player_10_linux/flashplayer-installer
install_flash_player_10_linux/libflashplayer.so
rm: cannot remove `/home/dave/libflashplayer-10.0.d21.1.linux-x86_64.so.tar.gz': No such file or directory

```

---

### Post by sandyd on 2009-02-04
suggestion:

type ```
 firefox
```in terminal.
that should give you some errors on missing libs. 
go and install them

(thats what happened when i first got mine)

dependencies need to be updated on that package....

---

### Post by RomeReactor on 2009-02-04
> **Daverobb said:**
> to RomeReactor --

didn't seem to work -- see script:

```
sudo ./Flash32
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done             
Couldn't find any package whose name or description matched "nspluginwrapper"
Couldn't find any package whose name or description matched "nspluginwrapper"
The following packages will be REMOVED:
  flashplugin-nonfree{p} 
0 packages upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
(Reading database ... 170468 files and directories currently installed.)
Removing flashplugin-nonfree ...
Purging configuration files for flashplugin-nonfree ...
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done             
--19:36:53--  http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_10_linux.tar.gz
           => `install_flash_player_10_linux.tar.gz'
Resolving fpdownload.macromedia.com... 96.17.34.70
Connecting to fpdownload.macromedia.com|96.17.34.70|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 3,962,157 (3.8M) [application/x-gzip]

100%[==========================>] 3,962,157     28.65K/s    ETA 00:00

19:39:03 (29.82 KB/s) - `install_flash_player_10_linux.tar.gz' saved [3962157/3962157]

install_flash_player_10_linux/
install_flash_player_10_linux/flashplayer-installer
install_flash_player_10_linux/libflashplayer.so
rm: cannot remove `/home/dave/libflashplayer-10.0.d21.1.linux-x86_64.so.tar.gz': No such file or directory

```

The error on the last line was due to wanting to remove the 64 bit version; it's corrected now in my previous post.

However, that should have been irrelevant. What do you get with:
```
sudo updatedb
```
and
```
locate libflashplayer.so
```
I must say, this seems strange. Temposs' suggestion should have worked too.

---

### Post by Daverobb on 2009-02-04
very strange

here is the result:

```
 sudo updatedb
[sudo] password for dave: 
dave@dave-desktop:~$ locate libflashplayer.so
/usr/lib/mozilla/plugins/libflashplayer.so
dave@dave-desktop:~$ 


```

---

### Post by Daverobb on 2009-02-04
i notice i  now how 2 folder in /usr/lib/

/mozilla and
/mozilla-firefox

both have plugin folders

---

### Post by RomeReactor on 2009-02-04
You could try copying the libflashplayer.so file to the mozilla-firefox/plugins folder:
```
sudo cp /usr/lib/mozilla/plugins/libflashplayer.so /mozilla-firefox/plugins
```

It's also possible that you don't have some firefox related packages installed, and therefore don't have the ubuntu-desktop metapackage; make sure you have the complete Ubuntu-desktop packages:
```
sudo aptitude install ubuntu-desktop
```
If you don't have it, perhaps installing it will restore the missing--if any--packages.

Regarding the missing nspluginwrapper package, it's only available in Ubuntu 64 bit, and not needed for your architecture; sorry about that.

---

### Post by Daverobb on 2009-02-04
first suggestion = says that folder doesn't exist

second = o files updated, etc 

no change 

this is a very strange situation - it would be interesting to know if this is a more widespread problem - how long has the new flash version been available

and why is there a discrepancy in the repos - the flashplugin-nonfree package does not exist -- ou must go through the adobe site directly.

that seems strange to me too altho there could be a simple answer,i'm sure

---

### Post by RomeReactor on 2009-02-04
> **Daverobb said:**
> and why is there a discrepancy in the repos - the flashplugin-nonfree package does not exist -- ou must go through the adobe site directly.

Make sure you have the Multiverse repository enabled in 'System->Administration->Software Sources'. The package *is* there.

---

### Post by Daverobb on 2009-02-04
it's there - it just doesn't work - it's a dead link -- 404 error - which i assume means adobe has taken the file off the server and replaced it with ver 10

weirdly tho, i think i fixed it -- i.e. flash now works in firefox

see this thread:  [http://ubuntuforums.org/showthread.php?t=1000713](http://ubuntuforums.org/showthread.php?t=1000713)

i had to uninstall ubuntu-restricted-extras in synaptic - reload the adobe deb file and then restart fireox a few times and now it seems to work

i'll post any further probs to this forum

---

### Post by Temposs on 2009-02-04
Could you output the contents of your sources.list? It's at:

```
/etc/apt/sources.list
```

This may tell us if anything is wrong with your repositories.

---

### Post by Daverobb on 2009-02-04
```
# deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://archive.ubuntu.com/ubuntu/ hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu/ hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu/ hardy universe
deb http://archive.ubuntu.com/ubuntu/ hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu/ hardy multiverse
deb http://archive.ubuntu.com/ubuntu/ hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://ca.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
# deb-src http://ca.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu gutsy partner
# deb-src http://archive.canonical.com/ubuntu gutsy partner

deb http://archive.ubuntu.com/ubuntu/ hardy-security main restricted
deb http://archive.ubuntu.com/ubuntu/ hardy-security universe
deb http://archive.ubuntu.com/ubuntu/ hardy-security multiverse
deb http://archive.ubuntu.com/ubuntu/ hardy-proposed restricted main multiverse universe
deb http://archive.ubuntu.com/ubuntu/ hardy-backports restricted main multiverse universe
deb http://archive.ubuntu.com/ubuntu/ gutsy multiverse
```

---

### Post by RomeReactor on 2009-02-04
According to your sources.list, you have two Gutsy repositories still enabled:
```
# deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://archive.ubuntu.com/ubuntu/ hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu/ hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu/ hardy universe
deb http://archive.ubuntu.com/ubuntu/ hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu/ hardy multiverse
deb http://archive.ubuntu.com/ubuntu/ hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
**deb http://ca.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse**
# deb-src http://ca.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu gutsy partner
# deb-src http://archive.canonical.com/ubuntu gutsy partner

deb http://archive.ubuntu.com/ubuntu/ hardy-security main restricted
deb http://archive.ubuntu.com/ubuntu/ hardy-security universe
deb http://archive.ubuntu.com/ubuntu/ hardy-security multiverse
deb http://archive.ubuntu.com/ubuntu/ hardy-proposed restricted main multiverse universe
deb http://archive.ubuntu.com/ubuntu/ hardy-backports restricted main multiverse universe
**deb http://archive.ubuntu.com/ubuntu/ gutsy multiverse**
```

Both are in bold. Disable them either by editing the sources.list file or in Software Sources. That may explain all these issues.

---

### Post by Temposs on 2009-02-04
Good call RomeReactor!

---

### Post by funky_uncle on 2009-02-05
> **Codename said:**
> Alright, so try this:
```
sudo apt-get remove --purge flashplugin-nonfree
```
That's if you have that package installed, then try:
```
sudo apt-get install flashplugin-nonfree
```I don't have any flash plugins installed. Typed the above in the terminal and got```
funky@funky-desktop:~$ sudo apt-get install flashplugin-nonfree
[sudo] password for funky: 
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
funky@funky-desktop:~$
```

Also, searching for "adobe-blashplugin" in Synaptic produces 0 results. But that's how I did it when I ran Mint.

---

### Post by funky_uncle on 2009-02-05
It turned out I had Synaptic running in the background so I closed it and typed ```
sudo apt-get adobe-flashplugin

```again. This gave me```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package flashplugin is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  flashplugin-nonfree
E: Package flashplugin has no installation candidate

```

---

### Post by carml on 2009-02-05
Did you try to download the file from Adobe.com?

---

### Post by funky_uncle on 2009-02-05
> **carml said:**
> Did you try to download the file from Adobe.com?Yes, but I get an "Error: Wrong architecture 'i386'"

Also, it seems like this plugin is only for Firefox, and I'm also using Opera from time to time.

---

### Post by RomeReactor on 2009-02-05
> **funky_uncle said:**
> It turned out I had Synaptic running in the background so I closed it and typed ```
sudo apt-get adobe-flashplugin

```again. This gave me```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package flashplugin is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  flashplugin-nonfree
E: Package flashplugin has no installation candidate

```

Hi. You need to enable the Multiverse repository in 'System-Administration->Software Sources'.

---

### Post by Temposs on 2009-02-05
funky_uncle,

The flash plugin will also work in Opera. You just need to point Opera to the right file. The adobe-flashplugin package is what you can get from the adobe website. If you want to use apt-get to install flash from the repositories, you need to get the flashplugin-nonfree package:

```
sudo apt-get install flashplugin-nonfree
```

---

### Post by LowSky on 2009-02-05
> **funky_uncle said:**
> Yes, but I get an "Error: Wrong architecture 'i386'"

Also, it seems like this plugin is only for Firefox, and I'm also using Opera from time to time.

Are you using 64Bit version of Ubuntu?

have you tried running 

```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by gandaran on 2009-02-05
> **funky_uncle said:**
> Yes, but I get an "Error: Wrong architecture 'i386'"

Also, it seems like this plugin is only for Firefox, and I'm also using Opera from time to time.
you have ubuntu 64-bits, right? 
then get adobe flash 64-bits [here]("http://labs.adobe.com/downloads/flashplayer10.html") 
to install, extract the package and move the libflashplayer.so file to /home/'user'/.mozilla/plugins (make the plugins folder) or /usr/lib/mozilla/plugins if you have more than one user account.
don't forget to remove any other flash package installed like flashplugin-nonfree (if you have any) or it will not work.
flash installed in /usr/lib/mozilla/plugins will also work in opera browser.

---

### Post by funky_uncle on 2009-02-05
> **RomeReactor said:**
> Hi. You need to enable the Multiverse repository in 'System-Administration->Software Sources'.They are enabled, doesn't work.

---

### Post by funky_uncle on 2009-02-05
> **LowSky said:**
> Are you using 64Bit version of Ubuntu?Yes.

> **LowSky said:**
> have you tried running 

```
sudo apt-get install ubuntu-restricted-extras
```Did that too, no difference :/

---

### Post by funky_uncle on 2009-02-05
> **gandaran said:**
> you have ubuntu 64-bits, right? 
then get adobe flash 64-bits [here]("http://labs.adobe.com/downloads/flashplayer10.html") 
to install, extract the package and move the libflashplayer.so file to /home/'user'/.mozilla/plugins (make the plugins folder) or /usr/lib/mozilla/plugins if you have more than one user account.
don't forget to remove any other flash package installed like flashplugin-nonfree (if you have any) or it will not work.
flash installed in /usr/lib/mozilla/plugins will also work in opera browser.Doesn't work.

:(

edit:
works in Firefox but not in Opera.

---

### Post by funky_uncle on 2009-02-05
.

---

### Post by gandaran on 2009-02-05
> **funky_uncle said:**
> Doesn't work.

:(

edit:
works in Firefox but not in Opera.

then just copy the libflashplayer.so to /usr/lib/opera/plugins too or maybe 64-bits opera doesn't work with 64-bits flash, this I don't really know.

---

### Post by funky_uncle on 2009-02-05
> **gandaran said:**
> then just copy the libflashplayer.so to /usr/lib/opera/pluginsThat worked! Thanks!

I had to run Nautilus in sudo mode to get access to that directory though.

Now if I could only get Java to work too...

---

### Post by steveneddy on 2009-02-05
I just got through downloading the .deb from adobe, copied it to a flash drive and installed it on three new installs in the house today.

I mean, Flash 10 from Adobe in a .deb - one click install?

I don't understand what is so hard.

What issues are you having?

---

### Post by gandaran on 2009-02-05
> **funky_uncle said:**
> That worked! Thanks!

I had to run Nautilus in sudo mode to get access to that directory though.

Now if I could only get Java to work too...

get the sun-java 64-bits .bin package from sun java site, search the forum for instructions on how to make firefox work with this package or then just install the icedtea plugin in synaptic (open java).

---

### Post by funky_uncle on 2009-02-05
> **gandaran said:**
> get the sun-java 64-bits .bin package from sun java site, search the forum for instructions on how to make firefox work with this package or then just install the icedtea plugin in synaptic (open java).I couldn't get icedtea to work, but I followed the instructions on [http://tldr.me/blog/2009/02/03/java-6-update-12-for-linux-amd64-howto/](http://tldr.me/blog/2009/02/03/java-6-update-12-for-linux-amd64-howto/) and it worked like a charm :)

(But only in Firefox, not Opera.)

---

