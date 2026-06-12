---
title: "Easy Ubuntu problem."
date: 2009-02-09
forum: New to Ubuntu
---

### Post by Awesom on 2009-02-09
Your sources.list does not match your system configuration.
Either you have changed your sources.list or an system
upgrade has failed. EasyUbuntu will not run unless these are fixed!

I do it all then get that error. I only installed ubuntu yesterday and am totally just beginning I don't know that much about codes and stuff but I can figure most simple stuff out. All I want atm is to have java so I can use frostwire and things. Iv tried doing the automatix and I get 404 not found. Any help much appreiciated.

---

### Post by Elfy on 2009-02-09
automatix is no longer

Post your sources list here please

```
cat /etc/apt/sources.list
```

---

### Post by clive littlewood on 2009-02-09
Hi

What forestpixie is asking you to do is open a terminal

Apps > Accessories > Terminal

enter cat /etc/apt/sources.list

You will be asked for your password which you type, but will not see.

Post the output to this thread.

For your Java open synaptic and search for ubuntu-restricted-extras and this will install java and many other restricted codecs you will need.

Hope this helps

Clive

---

### Post by Elfy on 2009-02-09
> For your Java open synaptic and search for ubuntu-restricted-extras and this will install java and many other restricted codecs you will need.Once you've sorted out the source list :)

---

### Post by Awesom on 2009-02-10
> Re: Easy Ubuntu problem.
automatix is no longer

Post your sources list here please

Code:

cat /etc/apt/sources.list

__________________
Please use descriptive thread titles.
Beginners Team Education Sessions
Beginners Team Resources

A computer is a means to an end. The person you're helping probably cares mostly about the end. This is reasonable.
By the time they ask you for help, they've probably tried several things. As a result, their computer might be in a strange state. This is natural.


```

# deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
# deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
# deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
# deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
# deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
# deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy-updates universe
# Line commented out by installer because it failed to verify:
# deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
# deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
# deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) intrepid main #WineHQ - Ubuntu 7.10 "Intrepid Ibex"
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy main
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy universe
# deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) dapper main

```

That is my sources list.

---

### Post by Elfy on 2009-02-10
You can create a source list with this - [http://repogen.simplylinux.ch/](http://repogen.simplylinux.ch/)

Open your sources list for editing

```
gksudo gedit /etc/apt/sources.list
```

Select and delete everything - replce it with thelist you get from the repogen site.

Save and close the file then from a terminal run

```
sudo apt-get update
```

---

### Post by halovivek on 2009-02-10
Why this problem occurs? some times i get this error. could not update.

---

### Post by Awesom on 2009-02-10
Hey thanks again for help I did all you said and it downloaded heaps but then this happened at the end ```

Reading package lists... Done
W: GPG error: http://download.virtualbox.org hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY DCF9F87B6DFBCBAE
W: GPG error: http://packages.medibuntu.org hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
W: GPG error: http://dl.google.com stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A040830F7FAC5991
W: GPG error: http://ppa.launchpad.net hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 60D11217247D1CFF
W: GPG error: http://ppa.launchpad.net hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 71346C8340130828
W: Duplicate sources.list entry http://ppa.launchpad.net hardy/main Packages (/var/lib/apt/lists/ppa.launchpad.net_abiword-stable_ppa_ubuntu_dists_hardy_main_binary-i386_Packages)
W: Duplicate sources.list entry http://ppa.launchpad.net intrepid/main Packages (/var/lib/apt/lists/ppa.launchpad.net_abiword-stable_ubuntu_dists_intrepid_main_binary-i386_Packages)
W: Duplicate sources.list entry http://ppa.launchpad.net hardy/main Packages (/var/lib/apt/lists/ppa.launchpad.net_do-core_ppa_ubuntu_dists_hardy_main_binary-i386_Packages)
W: Duplicate sources.list entry http://packages.medibuntu.org hardy/free Packages (/var/lib/apt/lists/packages.medibuntu.org_dists_hardy_free_binary-i386_Packages)
W: Duplicate sources.list entry http://packages.medibuntu.org hardy/non-free Packages (/var/lib/apt/lists/packages.medibuntu.org_dists_hardy_non-free_binary-i386_Packages)
W: Duplicate sources.list entry http://ppa.launchpad.net hardy/main Packages (/var/lib/apt/lists/ppa.launchpad.net_openoffice-pkgs_ubuntu_dists_hardy_main_binary-i386_Packages)
W: Duplicate sources.list entry http://ppa.launchpad.net hardy/main Packages (/var/lib/apt/lists/ppa.launchpad.net_tualatrix_ubuntu_dists_hardy_main_binary-i386_Packages)
W: Duplicate sources.list entry http://ppa.launchpad.net hardy/main Packages (/var/lib/apt/lists/ppa.launchpad.net_c-korn_ppa_ubuntu_dists_hardy_main_binary-i386_Packages)
W: Duplicate sources.list entry http://wine.budgetdedicated.com hardy/main Packages (/var/lib/apt/lists/wine.budgetdedicated.com_apt_dists_hardy_main_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems

```
I did the get update again and it still does it?

---

### Post by Elfy on 2009-02-10
Can you post it again then please - you have duplicates and some gpg errors which just need the key adding for.

---

### Post by Awesom on 2009-02-10
Um I assume you mean sources.list ? 

```

#############################################################
################### OFFICIAL UBUNTU REPOS ###################
#############################################################

###### Ubuntu Main Repos
deb http://au.archive.ubuntu.com/ubuntu/ hardy main restricted universe multiverse 
deb-src http://au.archive.ubuntu.com/ubuntu/ hardy main restricted universe multiverse 

###### Ubuntu Update Repos
deb http://au.archive.ubuntu.com/ubuntu/ hardy-security main restricted universe multiverse 
deb http://au.archive.ubuntu.com/ubuntu/ hardy-updates main restricted universe multiverse 
deb http://au.archive.ubuntu.com/ubuntu/ hardy-proposed main restricted universe multiverse 
deb http://au.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse 
deb-src http://au.archive.ubuntu.com/ubuntu/ hardy-security main restricted universe multiverse 
deb-src http://au.archive.ubuntu.com/ubuntu/ hardy-updates main restricted universe multiverse 
deb-src http://au.archive.ubuntu.com/ubuntu/ hardy-proposed main restricted universe multiverse 
deb-src http://au.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse 

###### Ubuntu Partner Repo
deb http://archive.canonical.com/ubuntu hardy partner
deb-src http://archive.canonical.com/ubuntu hardy partner

##############################################################
##################### UNOFFICIAL  REPOS ######################
##############################################################

###### 3rd Party Binary Repos

#### Abiword - http://www.abisource.com/
## Run this command: gpg --keyserver subkeys.pgp.net --recv 2382D57E && gpg --export --armor 2382D57E  | sudo apt-key add -
deb http://ppa.launchpad.net/abiword-stable/ppa/ubuntu hardy main 

#### Abiword - http://www.abisource.com/
## Run this command: gpg --keyserver subkeys.pgp.net --recv 2382D57E && gpg --export --armor 2382D57E  | sudo apt-key add -
deb http://ppa.launchpad.net/abiword-stable/ubuntu intrepid main

#### Amarok 2 - Project Neon - http://amarok.kde.org/wiki/User:Apachelogger/Project_Neon
deb http://ppa.launchpad.net/project-neon/ubuntu hardy main

#### Cairo Dock - http://www.cairo-dock.org/ww_page.php?p=Accueil&#9001;=en
## Run this command: wget -q http://repository.cairo-dock.org/ubuntu/cairo-dock.gpg -O- | sudo apt-key add -
deb http://repository.cairo-dock.org/ubuntu hardy cairo-dock

#### Gnome-Do - http://do.davebsd.com/
## Run this command: gpg --keyserver subkeys.pgp.net --recv 77558DD0 && gpg --export --armor 77558DD0  | sudo apt-key add -
deb http://ppa.launchpad.net/do-core/ppa/ubuntu hardy main

#### Google Linux Software Repositories - http://www.google.com/linuxrepositories/index.html
## Run this command: wget -q https://dl-ssl.google.com/linux/linux_signing_key.pub -O- | sudo apt-key add -
deb http://dl.google.com/linux/deb/ stable non-free

#### KDE 4.1.2 - http://www.kubuntu.org/news/kde-4.1.2
deb http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu hardy main

#### Medibuntu - http://www.medibuntu.org/
## Run this command: sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
deb http://packages.medibuntu.org/ hardy free non-free

#### OpenOffice.org 3.0 - https://launchpad.net/~openoffice-pkgs/+archive
deb http://ppa.launchpad.net/openoffice-pkgs/ubuntu hardy main 

#### Playdeb - http://www.playdeb.net/
## Run this command: wget http://www.playdeb.net/apturl_0.2.6-0~getdeb0_all.deb && sudo dpkg -i apturl_0.2.6-0~getdeb0_all.deb && sudo rm apturl_0.2.6-0~getdeb0_all.deb
deb mirror://www.getdeb.net/playdeb-mirror/hardy/// hardy/

#### Ubuntu Tweak - http://ubuntu-tweak.com/
deb http://ppa.launchpad.net/tualatrix/ubuntu hardy main

#### VirtualBox - http://www.virtualbox.org
## Run this command: wget -q http://download.virtualbox.org/virtualbox/debian/sun_vbox.asc -O- | sudo apt-key add -
deb http://download.virtualbox.org/virtualbox/debian hardy non-free

#### VLC media player  - http://www.videolan.org/vlc/
## Run this command: gpg --keyserver keyserver.ubuntu.com --recv-keys 40130828 && gpg --export -a 40130828 | sudo apt-key add -
deb http://ppa.launchpad.net/c-korn/ppa/ubuntu hardy main 

#### Wine - http://www.winehq.org/
## Run this command: wget -q http://wine.budgetdedicated.com/apt/387EE263.gpg -O- | sudo apt-key add -
deb http://wine.budgetdedicated.com/apt hardy main


####### 3rd Party Source Repos

#### Abiword (Source) - http://www.abisource.com/
## Run this command: gpg --keyserver subkeys.pgp.net --recv 2382D57E && gpg --export --armor 2382D57E  | sudo apt-key add -
deb http://ppa.launchpad.net/abiword-stable/ppa/ubuntu hardy main 

#### Abiword (Source) - http://www.abisource.com/
## Run this command: gpg --keyserver subkeys.pgp.net --recv 2382D57E && gpg --export --armor 2382D57E  | sudo apt-key add -
deb http://ppa.launchpad.net/abiword-stable/ubuntu intrepid main

#### Gnome-Do (Source) - http://do.davebsd.com/
## Run this command: gpg --keyserver subkeys.pgp.net --recv 77558DD0 && gpg --export --armor 77558DD0  | sudo apt-key add -
deb http://ppa.launchpad.net/do-core/ppa/ubuntu hardy main

#### Medibuntu (Source) - http://www.medibuntu.org/
## Run this command: sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
deb http://packages.medibuntu.org/ hardy free non-free

#### OpenOffice.org 3.0 (Source) - https://launchpad.net/~openoffice-pkgs/+archive
deb http://ppa.launchpad.net/openoffice-pkgs/ubuntu hardy main 

#### Ubuntu Tweak (Source) - http://ubuntu-tweak.com/
deb http://ppa.launchpad.net/tualatrix/ubuntu hardy main

#### VLC media player  (Source) - http://www.videolan.org/vlc/
## Run this command: gpg --keyserver keyserver.ubuntu.com --recv-keys 40130828 && gpg --export -a 40130828 | sudo apt-key add -
deb http://ppa.launchpad.net/c-korn/ppa/ubuntu hardy main 

#### Wine (Source) - http://www.winehq.org/
## Run this command: wget -q http://wine.budgetdedicated.com/apt/387EE263.gpg -O- | sudo apt-key add -
deb http://wine.budgetdedicated.com/apt hardy main

```

---

### Post by Elfy on 2009-02-10
Do you actually need all of those 3rd party repos ?

You need to run all the wget commands against each one in a terminal.

#### Wine (Source) - [http://www.winehq.org/](http://www.winehq.org/)
## Run this command: [COLOR="Red"]wget -q [http://wine.budgetdedicated.com/apt/387EE263.gpg](http://wine.budgetdedicated.com/apt/387EE263.gpg) -O- | sudo apt-key add -[/COLOR]
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) hardy main

I think that all of the ppas are causing the duplicate error as they all come from the same place.

---

### Post by Awesom on 2009-02-10
Thanks, umm the 1st two worked but the gpg ones didn't I did the update again and now I get this ```
Reading package lists... Done
W: GPG error: http://dl.google.com stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A040830F7FAC5991
W: GPG error: http://ppa.launchpad.net hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 60D11217247D1CFF
W: GPG error: http://ppa.launchpad.net hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 71346C8340130828
W: Duplicate sources.list entry http://ppa.launchpad.net hardy/main Packages (/var/lib/apt/lists/ppa.launchpad.net_abiword-stable_ppa_ubuntu_dists_hardy_main_binary-i386_Packages)
W: Duplicate sources.list entry http://ppa.launchpad.net intrepid/main Packages (/var/lib/apt/lists/ppa.launchpad.net_abiword-stable_ubuntu_dists_intrepid_main_binary-i386_Packages)
W: Duplicate sources.list entry http://ppa.launchpad.net hardy/main Packages (/var/lib/apt/lists/ppa.launchpad.net_do-core_ppa_ubuntu_dists_hardy_main_binary-i386_Packages)
W: Duplicate sources.list entry http://packages.medibuntu.org hardy/free Packages (/var/lib/apt/lists/packages.medibuntu.org_dists_hardy_free_binary-i386_Packages)
W: Duplicate sources.list entry http://packages.medibuntu.org hardy/non-free Packages (/var/lib/apt/lists/packages.medibuntu.org_dists_hardy_non-free_binary-i386_Packages)
W: Duplicate sources.list entry http://ppa.launchpad.net hardy/main Packages (/var/lib/apt/lists/ppa.launchpad.net_openoffice-pkgs_ubuntu_dists_hardy_main_binary-i386_Packages)
W: Duplicate sources.list entry http://ppa.launchpad.net hardy/main Packages (/var/lib/apt/lists/ppa.launchpad.net_tualatrix_ubuntu_dists_hardy_main_binary-i386_Packages)
W: Duplicate sources.list entry http://ppa.launchpad.net hardy/main Packages (/var/lib/apt/lists/ppa.launchpad.net_c-korn_ppa_ubuntu_dists_hardy_main_binary-i386_Packages)
W: Duplicate sources.list entry http://wine.budgetdedicated.com hardy/main Packages (/var/lib/apt/lists/wine.budgetdedicated.com_apt_dists_hardy_main_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems

``` Not sure if anything has changed..

---

### Post by Elfy on 2009-02-10
What exactly is easyubuntu - where did you get it from - the website says it is no longer maintained.

What os are you actually running - is it a standard one?

What country are you in as well please.

---

### Post by Awesom on 2009-02-10
I don't need anything really lol I just ticked most of the boxes I wasn't sure all I want is java mainly so I can run frostwire.. I am from Australia and I had an old live cd with 7.10 I think but I did an upgrade which took like 6hrs to download and now I am pretty sure I am using 8.04 maybe there is a way to check the exact version ?

---

### Post by Elfy on 2009-02-10
Run 

```
lsb_release -a
```

I would redo your repos from the generator again :)

Get medibuntu installed from here

[https://help.ubuntu.com/community/Medibuntu#Adding](https://help.ubuntu.com/community/Medibuntu#Adding) the Repositories

Get virtualbox if you want to from here, bottom of the page is the repo information

[http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)

For most things the universe, multiverse, main and restricted will be ok - do the Ubuntu partner repos

Don't do proposed and backports, nor any of the 3rd party ones 

You can add them as you need them

Java is available in the normal repos :)

---

### Post by Awesom on 2009-02-10
Its allllll gooood :D thanks for your time man with your help pretty sure I've got it all now I went back to the site and only did the updates and stuff none of the 3rd party stuff and it updated now I am download the restricted-extras which is doin sun java so yeh seems to be workin fine so thanks again :D

---

### Post by Elfy on 2009-02-10
Good and your welcome :)

---

