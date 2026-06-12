---
title: "Installation of openoffice 3.1.0"
date: 2009-06-13
forum: New to Ubuntu
---

### Post by atish.sihi on 2009-06-13
[FONT=Comic Sans MS][SIZE=2]Hi,

Currently I am using open office 3.0, I want to upgrade it with 3.1.0. I have tried a lot but not able to install it properly. I have tried with uninstalling 3.0 and then installing 3.1, but nothing worked out properly. Kindly let me know how to install 3.1.0. Is there any significant difference between 3.0.0 and 3.1.0. 

Regards,
Atish Sihi[/SIZE][/FONT]

---

### Post by howefield on 2009-06-13
Try this, 

[http://news.softpedia.com/news/How-to-Install-OpenOffice-org-3-1-on-Ubuntu-9-04-111105.shtml](http://news.softpedia.com/news/How-to-Install-OpenOffice-org-3-1-on-Ubuntu-9-04-111105.shtml)

New features in 3.1

[http://www.openoffice.org/dev_docs/features/3.1/index.html](http://www.openoffice.org/dev_docs/features/3.1/index.html)

---

### Post by gradinaruvasile on 2009-06-13
Getting rid of openoffice isnt that easy..

3.1.0 has more features and less bugs (at least this is on the ad...:) )

Remove the  

openofficeorg-desktop-integration
openofficeorg-debian-menus
openoffice.org-bundled

packages first

Then go to

[http://download.openoffice.org/other.html#en-US]("http://download.openoffice.org/other.html#en-US")


Grab the English (US) / Linux deb (or Linux 64 deb if u have ubuntu 64 bit version)

Unpack it in a folder , go in the DEBS folder in a terminal, execute

cd /path/to/DEBS

Where DEBS is the DEBS subfolder you unpacked (it has a truckload of .deb files in it)

sudo dpkg -i *

long list of things being done...

cd desktop-integration
sudo dpkg -i *
again

Open the Applications->Office 
you should have the openoffice 3.1 components there

good luck

---

### Post by atish.sihi on 2009-06-13
To : Howefield

I had tried the link (after searching in google we get hte link in top place, I had tried most of the links there) but was not able to install 3.1.0.

I already read the details about 3.1.0 in OOorg site. But I asking feedback who has used 3.1.0 already.

Regards,
Atish Sihi

---

### Post by gradinaruvasile on 2009-06-13
I did exactly i posted here and it worked (on every computer i did it (6-7)
It should work...

What doesn work exactly?

---

### Post by atish.sihi on 2009-06-13
To:gradinaruvasile

I had tried with uninstalling Openoffice 3.0.0
But I think full uninstallation has not been done properly.
Can you please provide me the commands which will help me full installation from terminal.
I am using ubuntu 8.04 32 Bit
Thanks in advance.

Atish Sihi

---

### Post by howefield on 2009-06-13
> **atish.sihi said:**
> I had tried the link (after searching in google we get hte link in top place, I had tried most of the links there) but was not able to install 3.1.0.

Sorry to hear that, :(

> But I asking feedback who has used 3.1.0 already.

Mind reading was never my strong point. But you have prompted me to upgrade and try.

---

### Post by gradinaruvasile on 2009-06-13
i dont think you have to uninstall anything except those 3 packages...

The OO version from the site has different package version/names so they can live happily together... You will lose only the menu links to the old openoffice (i think, but not sure).

If u really want to hunt down and remove the 3.0 open synaptic, search for "openoffice.org" and remove every package with openoffice.org in their name. But as i said this is not absolutely necessary.

---

### Post by fooman on 2009-06-13
you should not have to uninstall *anything*.....should only be an upgrade.

see here:

[http://ubuntuforums.org/showthread.php?t=987181](http://ubuntuforums.org/showthread.php?t=987181)

hope that helps.

---

### Post by gradinaruvasile on 2009-06-13
I tried that, but didnt like it for some reason... loaded and it seemed slower than the vanilla one.

---

### Post by atish.sihi on 2009-06-13
> **fooman said:**
> you should not have to uninstall *anything*.....should only be an upgrade.

see here:

[http://ubuntuforums.org/showthread.php?t=987181](http://ubuntuforums.org/showthread.php?t=987181)

hope that helps.

I had tried with steps in the link given by you. but at last in terminal it came "0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded." and I ban see under application->office its OO 3.0. :(

---

### Post by Mornedhel on 2009-06-13
To force upgrading of packages that require additional packages be installed, you can use sudo apt-get dist-upgrade instead of sudo apt-get upgrade.

---

### Post by atish.sihi on 2009-06-13
> **gradinaruvasile said:**
> i dont think you have to uninstall anything except those 3 packages...

The OO version from the site has different package version/names so they can live happily together... You will lose only the menu links to the old openoffice (i think, but not sure).

If u really want to hunt down and remove the 3.0 open synaptic, search for "openoffice.org" and remove every package with openoffice.org in their name. But as i said this is not absolutely necessary.


I in my synaptec package OO 2.0 is available. I am using ubuntu 8.04.So I can't uninstall it from there.

---

### Post by gradinaruvasile on 2009-06-13
Add this line to /etc/apt/sources.list

deb [http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu) hardy main

with:
sudo gedit /etc/apt/sources.list
then

sudo apt-get update && sudo apt-get dselect-upgrade

In a terminal.

Make sure u have the old openoffice installed.... cause this will upgrade your old packages to the new version, it is not the same method i suggested.

If u dont have it installed go to applications-add/remove, search for openoffice and tick the programs u need.

If not working, try the method i suggested first.

---

### Post by atish.sihi on 2009-06-13
> **Mornedhel said:**
> To force upgrading of packages that require additional packages be installed, you can use sudo apt-get dist-upgrade instead of sudo apt-get upgrade.


I tried with "sudo apt-get dist-upgrade" but still it's same.

---

### Post by atish.sihi on 2009-06-13
> **gradinaruvasile said:**
> Add this line to /etc/apt/sources.list

deb [http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu) hardy main

with:
sudo gedit /etc/apt/sources.list
then

sudo apt-get update && sudo apt-get dselect-upgrade

In a terminal.

Make sure u have the old openoffice installed.... cause this will upgrade your old packages to the new version, it is not the same method i suggested.

If u dont have it installed go to applications-add/remove, search for openoffice and tick the programs u need.

If not working, try the method i suggested first.


I have already tried with sorce file change and so on as you have  mentioned,but it's not working. Its not getting upgraded.

---

### Post by gradinaruvasile on 2009-06-13
Post the output of 

cat /etc/apt/sources.list

---

### Post by Johan-Steyn on 2009-06-13
Hi All,

To update Open Office from 3.0 to 3.1 check out this website (9.04 Jaunty) [http://news.softpedia.com/news/How-t...4-111105.shtml]("http://news.softpedia.com/news/How-to-Install-OpenOffice-org-3-1-on-Ubuntu-9-04-111105.shtml")

Just update the Software Sources with the PPA from the OpenOffice.org Scribblers.

Also add the save the key and import it to Software Sources Authentication tab.

Just run Update to update 3.0. to 3.1

Works like a charm.

PS> EVEN THOUGH IT IS UPDATE TO 3.1 THE LOADING SCREEN WILL STILL INDICATE 3.0. 

Check Help>About to confirm that the update to 3.1 was successful.

Regards,

JS

---

### Post by fooman on 2009-06-13
> **atish.sihi said:**
> I had tried with steps in the link given by you. but at last in terminal it came "0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded." and I ban see under application->office its OO 3.0. :(

if you have already uninstalled open office (or parts of it)...then just try installing the package "openoffice.org", to reinstall the entire open office suite.  if the repos have been added,  as in the thread i linked to earlier...then running the following command should do the trick:

```
sudo apt-get install openoffice.org
```

hope that helps.

---

### Post by atish.sihi on 2009-06-13
> **gradinaruvasile said:**
> Post the output of 

cat /etc/apt/sources.list
  The output is:

atish@atish-laptop:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/ hardy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
# deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-security main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-security main restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-security universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-security universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-security multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-security multiverse
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu) hardy main
##repo for open office3
deb [http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu) hardy main
deb-src [http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu) hardy main

---

### Post by atish.sihi on 2009-06-13
> **Johan-Steyn said:**
> Hi All,

To update Open Office from 3.0 to 3.1 check out this website (9.04 Jaunty) [http://news.softpedia.com/news/How-t...4-111105.shtml]("http://news.softpedia.com/news/How-to-Install-OpenOffice-org-3-1-on-Ubuntu-9-04-111105.shtml")

Just update the Software Sources with the PPA from the OpenOffice.org Scribblers.

Also add the save the key and import it to Software Sources Authentication tab.

Just run Update to update 3.0. to 3.1

Works like a charm.

PS> EVEN THOUGH IT IS UPDATE TO 3.1 THE LOADING SCREEN WILL STILL INDICATE 3.0. 

Check Help>About to confirm that the update to 3.1 was successful.

Regards,

JS


I have tried with the given link before but it didn't work for me. I have checked in help also,its still 3.0.0

---

### Post by atish.sihi on 2009-06-13
> **fooman said:**
> if you have already uninstalled open office (or parts of it)...then just try installing the package "openoffice.org", to reinstall the entire open office suite.  if the repos have been added,  as in the thread i linked to earlier...then running the following command should do the trick:

```
sudo apt-get install openoffice.org
```hope that helps.

Thanks Fooman!!! At last I am able to install OO 3.1.0. :D

Thanks to all for helping me. :D

Thia version much look like OO 2.0!!!=D>

---

