---
title: "How can I use my DWA-542 wireless card?"
date: 2008-04-06
forum: Networking &amp; Wireless
---

### Post by ajmetalhed on 2008-04-06
I recently bought a Compaq Presario SR5350F desktop, and now I am dual-booting Vista 32 bit and Ubuntu 7.10 32-bit.  In Vista, the wireless network works perfectly fine, but in Ubuntu, the card does not even seem to be recognized/installed.  I am a complete n00b when it comes to Ubuntu, so I had no idea what people were talking about in other posts pertaining to the same problem as me.  I have the impression that as of yet, there is no way to get this card to work.  Any help is appreciated.

---

### Post by greenstar on 2008-04-06
So that we will know what chipset you have, post the output of this:
```
lspci -nn
```If it's an AR5008, then see [this post]("http://ubuntuforums.org/showthread.php?p=4665969#post4665969").

If it's an AR5416, then see [this post]("http://ubuntuforums.org/showthread.php?p=4666204#post4666204").

HTH,

Greenstar

---

### Post by ajmetalhed on 2008-04-06
ali@ali-desktop:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub [8086:2770] (rev 02)
00:02.0 VGA compatible controller [0300]: Intel Corporation 82945G/GZ Integrated Graphics Controller [8086:2772] (rev 02)
00:1b.0 Audio device [0403]: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller [8086:27d8] (rev 01)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 [8086:27d0] (rev 01)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 [8086:27d2] (rev 01)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 [8086:27c8] (rev 01)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 [8086:27c9] (rev 01)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 [8086:27ca] (rev 01)
00:1d.3 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 [8086:27cb] (rev 01)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller [8086:27cc] (rev 01)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev e1)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge [8086:27b8] (rev 01)
00:1f.1 IDE interface [0101]: Intel Corporation 82801G (ICH7 Family) IDE Controller [8086:27df] (rev 01)
00:1f.2 IDE interface [0101]: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller [8086:27c0] (rev 01)
00:1f.3 SMBus [0c05]: Intel Corporation 82801G (ICH7 Family) SMBus Controller [8086:27da] (rev 01)
01:04.0 Communication controller [0780]: Conexant HSF 56k Data/Fax Modem [14f1:2f20]
01:05.0 Network controller [0280]: Atheros Communications, Inc. AR5416 802.11a/b/g/n Wireless PCI Adapter [168c:0023] (rev 01)
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller [10ec:8136] (rev 01)
ali@ali-desktop:~$ 

that was the complete output in the terminal.  I assume that the "Network controller" line contains the information I need.

---

### Post by ajmetalhed on 2008-04-06
Oh... I see.  It is an AR5146.  I'll take a look at the post.  Again, thanks for your help!

---

### Post by ajmetalhed on 2008-04-06
So from what i understand, I'll have to type this into the terminal:

```
 linux-restricted-modules-$(uname -r)
```

and madwifi will install?  I can only get online from Vista, so does Ubuntu need to download madwifi from the internet, or does it already contain the necessary files?

---

### Post by greenstar on 2008-04-07
It says that it should already be present in the restricted modules. However, if you did a manual installation of Ubuntu, you may need to install it by doing this:
```
sudo aptitude install linux-restricted-modules-$(uname -r)
```So what you'll probably need to do is install madwifi-tools:
```
sudo aptitude install madwifi-tools
```In synaptic, this is the description given for madwifi-tools:

> tools for the Multiband Atheros Driver for WiFi
This package provides userspace tools for the madwifi driver. The tools are
required to use and manipulate the madwifi interfaces present in a system.

[http://madwifi.org/](http://madwifi.org/)Then configure the wireless card with madwifi-tools.

HTH,
Greenstar

---

### Post by ajmetalhed on 2008-04-08
I didn't do a manual install-- i chose the guided install to largest continuos free space.

In the Synaptic Package Manager, i've enabled packages from all four repositories (official, restricted, universe, and multiverse) but I still don't see Madwifi.

I tried all three of these codes afterwards:

```
linux-restricted-modules-$(uname -r)
```

```
sudo aptitude install linux-restricted-modules-$(uname -r)
```

```
sudo aptitude install madwifi-tools

```

and nothing installed.  Will I have to use my Ubuntu 7.10 installation cd as a repository, or should I download madwifi from Vista and attempt to manually install it in Ubuntu?

---

### Post by greenstar on 2008-04-08
Did you remember to:
```
sudo aptitude update
```after enabling additional repositories?

If so, please post your sources.list so I'll be on the same page.
No need for sudo here, since were just copying the contents of the file:
```
gedit /etc/apt/sources.list
```

Greenstar

---

### Post by ajmetalhed on 2008-04-08
alright i'll post the results of those in just a minute; i have to boot into Ubuntu now.

---

### Post by ajmetalhed on 2008-04-08
first, i made sure restricted, universe, and multiverse were enabled

and then, for ```
sudo aptitude update
```

it gave me

```

Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Translation-en_US
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Translation-en_US
Err http://archive.canonical.com gutsy Release.gpg                          
  Could not resolve 'archive.canonical.com'
Err http://archive.canonical.com gutsy/partner Translation-en_US            
  Could not resolve 'archive.canonical.com'
Ign http://archive.canonical.com gutsy Release                              
Err http://archive.ubuntu.com gutsy Release.gpg
  Could not resolve 'archive.ubuntu.com'
Err http://archive.ubuntu.com gutsy/main Translation-en_US
  Could not resolve 'archive.ubuntu.com'
Err http://archive.ubuntu.com gutsy/universe Translation-en_US
  Could not resolve 'archive.ubuntu.com'
Ign http://archive.canonical.com gutsy/partner Packages
Err http://archive.ubuntu.com gutsy/restricted Translation-en_US
  Could not resolve 'archive.ubuntu.com'
Err http://archive.ubuntu.com gutsy/multiverse Translation-en_US
  Could not resolve 'archive.ubuntu.com'
Ign http://archive.canonical.com gutsy/partner Sources
Err http://archive.canonical.com gutsy/partner Packages
  Could not resolve 'archive.canonical.com'
Ign http://archive.ubuntu.com gutsy Release
Err http://archive.canonical.com gutsy/partner Sources
  Could not resolve 'archive.canonical.com'
Ign http://archive.ubuntu.com gutsy/main Packages
Ign http://archive.ubuntu.com gutsy/universe Packages
Ign http://archive.ubuntu.com gutsy/restricted Packages
Ign http://archive.ubuntu.com gutsy/multiverse Packages
Err http://archive.ubuntu.com gutsy/main Packages
  Could not resolve 'archive.ubuntu.com'
Err http://archive.ubuntu.com gutsy/universe Packages
  Could not resolve 'archive.ubuntu.com'
Err http://archive.ubuntu.com gutsy/restricted Packages
  Could not resolve 'archive.ubuntu.com'
Err http://archive.ubuntu.com gutsy/multiverse Packages
  Could not resolve 'archive.ubuntu.com'
Reading package lists... Done
```


and for

```

gedit /etc/apt/sources.list

```
it gave me

```

deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
# deb http://us.archive.ubuntu.com/ubuntu/ gutsy main restricted
# Line commented out by installer because it failed to verify:
# deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
# deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
# deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
# deb http://us.archive.ubuntu.com/ubuntu/ gutsy universe
# Line commented out by installer because it failed to verify:
# deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy universe
# Line commented out by installer because it failed to verify:
# deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates universe
# Line commented out by installer because it failed to verify:
# deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
# deb http://us.archive.ubuntu.com/ubuntu/ gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
# deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu gutsy partner
deb-src http://archive.canonical.com/ubuntu gutsy partner

# Line commented out by installer because it failed to verify:
# deb http://security.ubuntu.com/ubuntu gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb-src http://security.ubuntu.com/ubuntu gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb http://security.ubuntu.com/ubuntu gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb-src http://security.ubuntu.com/ubuntu gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb http://security.ubuntu.com/ubuntu gutsy-security multiverse
# Line commented out by installer because it failed to verify:
deb http://archive.ubuntu.com/ubuntu/ gutsy main universe restricted multiverse
# deb-src http://security.ubuntu.com/ubuntu gutsy-security multiverse

```

---

### Post by ajmetalhed on 2008-04-08
i think i may need to use a cd?

---

### Post by greenstar on 2008-04-08
Look at your sources.list.:( Everything but the CD-ROM is commented out (disabled with a # at the beginning of the line). Also note all the lines that say:
```
# Line commented out by installer because it failed to verify:
```Here's my sources.list. I've commented out all of he extras I have, but I've left them there in case you want/need to use them. All you need to do to enable them is remove the # from the beginning of the line, or check the box for the repository line in System->Administration->Software Sources

1. To fix those errors, do:
```
sudo gedit /etc/apt/sources.list
```2. <Ctrl>+<A> to select all

3. Delete to clear all lines

4. Copy & paste into your blank file everything you see between the lines below.
---------------------------------------------------------------
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how 
# to upgrade to newer versions of the distribution.
#
# If you don't know what to do with this file, read
# [https://help.ubuntu.com/community/Repositories/CommandLine](https://help.ubuntu.com/community/Repositories/CommandLine)
#
# If you get errors about missing keys, lookup the key in this file
# and run these commands (replace KEY with the key number):
#
# gpg –keyserver subkeys.pgp.net –recv KEY
# gpg –export –armor KEY | sudo apt-key add -
#
# If you have a gpg key URL use (replace URL with the key address):
#
# wget URL –quiet -O - | sudo apt-key add -
#
# If you have a gpg key file use (replace FILE with the key file):
#
# sudo apt-key add FILE
#
# In the repository list page there’s also a script that can do this
# work automatically, this is suggested only if you know what you’re doing
#
# Add comments (##) in front of any line to remove it from being checked.   
# Use the following sources.list at your own risk.  
#
# Uncomment deb-src if you wish to download the source packages

# Ubuntu supported packages (GPG key: 437D05B5)
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy restricted main multiverse universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates restricted main multiverse universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-security main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-security restricted main multiverse universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-proposed main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-proposed restricted main multiverse universe

# Ubuntu community supported packages (GPG key: 437D05B5)
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-security universe multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-proposed universe multiverse

# Ubuntu backports project (GPG key: 437D05B5)
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

# Medibuntu (Multimedia, Entertainment & Distraction In Ubuntu)
# GPG key-file: wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add -
# deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) gutsy free non-free
# deb-src [http://packages.medibuntu.org/](http://packages.medibuntu.org/) gutsy free non-free

# Canonical's 'partner' repository. This software is not part of Ubuntu, but is
# offered by Canonical and the respective vendors as a service to Ubuntu
# users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

# Wine
# GPG key-file: wget -q [http://wine.budgetdedicated.com/apt/387EE263.gpg](http://wine.budgetdedicated.com/apt/387EE263.gpg) -O- | sudo apt-key add -
# deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) gutsy main #WineHQ - Ubuntu 7.10 "Gutsy Gibbon"
# deb-src [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) gutsy main #WineHQ - Ubuntu 7.10 "Gutsy Gibbon"
------------------------------------------------

5. <Ctrl>+<S> to save

6. <Ctrl>+<Q> to quit the text editor. 

7. Update aptitude
```
sudo aptitude update
```8. Let aptitude try to sort out any package installation or dependency problems
```
sudo aptitude -f install
```9. Upgrade the individual packages
```
sudo aptitude safe-upgrade
```10. Upgrade the whole distro
```
sudo aptitude dist-upgrade
```11. Go back to [this step]("http://ubuntuforums.org/showpost.php?p=4668417&postcount=6") and try again.

HTH,

Greenstar

---

### Post by ajmetalhed on 2008-04-08
well i'm gonna give that a shot now.

Thanks for all of your help!

---

### Post by ajmetalhed on 2008-04-09
:confused: Now I have no idea what I am doing wrong.  I made sure all repositories are enabled, I copied your source list exactly as it is and followed all of your steps, but I still got errors.  It doesn't appear that madwifi came with my install.   In Ubuntu, I do not have a working internet connection, and it seems as though it is trying to access the internet for the updates.  So is there a way I can download the madwifi files from windows and then install them in Ubuntu?

---

### Post by greenstar on 2008-04-09
> **ajmetalhed said:**
> followed all of your steps, but I still got errors.
You *have* to tell me what the errors are or I can't help.

> **ajmetalhed said:**
> It doesn't appear that madwifi came with my install.
It comes with everyone's Ubuntu install unless you install manually as in starting with the server install cd and adding packages piecemeal.

> **ajmetalhed said:**
> In Ubuntu, I do not have a working internet connection, and it seems as though it is trying to access the internet for the updates.
It is trying to access the internet for updates. Be patient and we'll get there.

> **ajmetalhed said:**
> So is there a way I can download the madwifi files from windows and then install them in Ubuntu?
Yes, but that's not the problem we have to deal with first, and it won't, by itself, solve the problem that you're experiencing. We've got to handle the problems in order. Let's not get ahead of ourselves worrying about madwifi just yet. You've got a bigger problem that must be solved first.
 

So how about providing more info on the 'new' error(s) you get when you do:
```
sudo aptitude update
```Also, post your current sources.list:

```
gedit /etc/apt/sources.list
```I think you may have made a mistake somewhere in that process if you're still getting update errors.

Greenstar

---

### Post by ajmetalhed on 2008-04-09
when I type:

```

sudo aptitude update

```

i get
```

Err http://us.archive.ubuntu.com gutsy Release.gpg
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com gutsy/main Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com gutsy/restricted Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com gutsy/universe Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com gutsy/multiverse Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com gutsy-updates Release.gpg
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com gutsy-updates/main Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com gutsy-updates/restricted Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com gutsy-updates/universe Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com gutsy-updates/multiverse Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com gutsy-security Release.gpg
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com gutsy-security/main Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com gutsy-security/restricted Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com gutsy-security/universe Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com gutsy-security/multiverse Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com gutsy-proposed Release.gpg
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com gutsy-proposed/main Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com gutsy-proposed/restricted Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com gutsy-proposed/universe Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com gutsy-proposed/multiverse Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Ign http://us.archive.ubuntu.com gutsy Release
Ign http://us.archive.ubuntu.com gutsy-updates Release
Ign http://us.archive.ubuntu.com gutsy-security Release
Ign http://us.archive.ubuntu.com gutsy-proposed Release
Ign http://us.archive.ubuntu.com gutsy/main Packages
Ign http://us.archive.ubuntu.com gutsy/restricted Packages
Ign http://us.archive.ubuntu.com gutsy/restricted Sources
Ign http://us.archive.ubuntu.com gutsy/main Sources
Ign http://us.archive.ubuntu.com gutsy/multiverse Sources
Ign http://us.archive.ubuntu.com gutsy/universe Sources
Ign http://us.archive.ubuntu.com gutsy/universe Packages
Ign http://us.archive.ubuntu.com gutsy/multiverse Packages
Ign http://us.archive.ubuntu.com gutsy-updates/main Packages
Ign http://us.archive.ubuntu.com gutsy-updates/restricted Packages
Ign http://us.archive.ubuntu.com gutsy-updates/restricted Sources
Ign http://us.archive.ubuntu.com gutsy-updates/main Sources
Ign http://us.archive.ubuntu.com gutsy-updates/multiverse Sources
Ign http://us.archive.ubuntu.com gutsy-updates/universe Sources
Ign http://us.archive.ubuntu.com gutsy-updates/universe Packages
Ign http://us.archive.ubuntu.com gutsy-updates/multiverse Packages
Ign http://us.archive.ubuntu.com gutsy-security/main Packages
Ign http://us.archive.ubuntu.com gutsy-security/restricted Packages
Ign http://us.archive.ubuntu.com gutsy-security/restricted Sources
Ign http://us.archive.ubuntu.com gutsy-security/main Sources
Ign http://us.archive.ubuntu.com gutsy-security/multiverse Sources
Ign http://us.archive.ubuntu.com gutsy-security/universe Sources
Ign http://us.archive.ubuntu.com gutsy-security/universe Packages
Ign http://us.archive.ubuntu.com gutsy-security/multiverse Packages
Ign http://us.archive.ubuntu.com gutsy-proposed/main Packages
Ign http://us.archive.ubuntu.com gutsy-proposed/restricted Packages
Ign http://us.archive.ubuntu.com gutsy-proposed/restricted Sources
Ign http://us.archive.ubuntu.com gutsy-proposed/main Sources
Ign http://us.archive.ubuntu.com gutsy-proposed/multiverse Sources
Ign http://us.archive.ubuntu.com gutsy-proposed/universe Sources
Ign http://us.archive.ubuntu.com gutsy-proposed/universe Packages
Ign http://us.archive.ubuntu.com gutsy-proposed/multiverse Packages
Err http://us.archive.ubuntu.com gutsy/main Packages
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com gutsy/restricted Packages
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com gutsy/restricted Sources
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com gutsy/main Sources
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com gutsy/multiverse Sources
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com gutsy/universe Sources
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com gutsy/universe Packages
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com gutsy/multiverse Packages
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com gutsy-updates/main Packages
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com gutsy-updates/restricted Packages
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com gutsy-updates/restricted Sources
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com gutsy-updates/main Sources
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com gutsy-updates/multiverse Sources
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com gutsy-updates/universe Sources
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com gutsy-updates/universe Packages
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com gutsy-updates/multiverse Packages
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com gutsy-security/main Packages
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com gutsy-security/restricted Packages
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com gutsy-security/restricted Sources
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com gutsy-security/main Sources
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com gutsy-security/multiverse Sources
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com gutsy-security/universe Sources
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com gutsy-security/universe Packages
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com gutsy-security/multiverse Packages
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com gutsy-proposed/main Packages
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com gutsy-proposed/restricted Packages
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com gutsy-proposed/restricted Sources
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com gutsy-proposed/main Sources
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com gutsy-proposed/multiverse Sources
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com gutsy-proposed/universe Sources
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com gutsy-proposed/universe Packages
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com gutsy-proposed/multiverse Packages
  Could not resolve 'us.archive.ubuntu.com'
Reading package lists... Done

```

I do not know if there is another configuration file I have to edit to fix these problems...

When I type

```

gedit /etc/apt/sources.list

```

I get

```

# See http://help.ubuntu.com/community/UpgradeNotes for how
# to upgrade to newer versions of the distribution.
#
# If you don't know what to do with this file, read
# https://help.ubuntu.com/community/Re...es/CommandLine
#
# If you get errors about missing keys, lookup the key in this file
# and run these commands (replace KEY with the key number):
#
# gpg -keyserver subkeys.pgp.net -recv KEY
# gpg -export -armor KEY | sudo apt-key add -
#
# If you have a gpg key URL use (replace URL with the key address):
#
# wget URL -quiet -O - | sudo apt-key add -
#
# If you have a gpg key file use (replace FILE with the key file):
#
# sudo apt-key add FILE
#
# In the repository list page there's also a script that can do this
# work automatically, this is suggested only if you know what you're doing
#
# Add comments (##) in front of any line to remove it from being checked.
# Use the following sources.list at your own risk.
#
# Uncomment deb-src if you wish to download the source packages

# Ubuntu supported packages (GPG key: 437D05B5)
deb http://us.archive.ubuntu.com/ubuntu/ gutsy main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy restricted main multiverse universe
deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates restricted main multiverse universe
deb http://us.archive.ubuntu.com/ubuntu/ gutsy-security main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-security restricted main multiverse universe
deb http://us.archive.ubuntu.com/ubuntu/ gutsy-proposed main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-proposed restricted main multiverse universe

# Ubuntu community supported packages (GPG key: 437D05B5)
deb http://us.archive.ubuntu.com/ubuntu/ gutsy universe multiverse
deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates universe multiverse
deb http://us.archive.ubuntu.com/ubuntu/ gutsy-security universe multiverse
deb http://us.archive.ubuntu.com/ubuntu/ gutsy-proposed universe multiverse

# Ubuntu backports project (GPG key: 437D05B5)
# deb http://us.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

# Medibuntu (Multimedia, Entertainment & Distraction In Ubuntu)
# GPG key-file: wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add -
# deb http://packages.medibuntu.org/ gutsy free non-free
# deb-src http://packages.medibuntu.org/ gutsy free non-free

# Canonical's 'partner' repository. This software is not part of Ubuntu, but is
# offered by Canonical and the respective vendors as a service to Ubuntu
# users.
# deb http://archive.canonical.com/ubuntu gutsy partner
# deb-src http://archive.canonical.com/ubuntu gutsy partner

# Wine
# GPG key-file: wget -q http://wine.budgetdedicated.com/apt/387EE263.gpg -O- | sudo apt-key add -
# deb http://wine.budgetdedicated.com/apt gutsy main #WineHQ - Ubuntu 7.10 "Gutsy Gibbon"
# deb-src http://wine.budgetdedicated.com/apt gutsy main #WineHQ - Ubuntu 7.10 "Gutsy Gibbon"

``` 

which is almost the same thing-- The apostrophes and hyphens were shown as a strange square-box character, so i re-typed the apostrophes and put little dashes in the hyphen's spaces.  Either way, that was only in this section:

```

# See http://help.ubuntu.com/community/UpgradeNotes for how
# to upgrade to newer versions of the distribution.
#
# If you don't know what to do with this file, read
# https://help.ubuntu.com/community/Re...es/CommandLine
#
# If you get errors about missing keys, lookup the key in this file
# and run these commands (replace KEY with the key number):
#
# gpg -keyserver subkeys.pgp.net -recv KEY
# gpg -export -armor KEY | sudo apt-key add -
#
# If you have a gpg key URL use (replace URL with the key address):
#
# wget URL -quiet -O - | sudo apt-key add -
#
# If you have a gpg key file use (replace FILE with the key file):
#
# sudo apt-key add FILE
#
# In the repository list page there's also a script that can do this
# work automatically, this is suggested only if you know what you're doing
#
# Add comments (##) in front of any line to remove it from being checked.
# Use the following sources.list at your own risk.
#
# Uncomment deb-src if you wish to download the source packages

```

so i don't think that makes a difference.  

As for the next step, do you want me to go back to the post with the eleven steps and put the resulting messages, or is there a different course of action I will need to take?

---

### Post by greenstar on 2008-04-10
> **ajmetalhed said:**
> As for the next step, do you want me to go back to the post with the eleven steps and put the resulting messages, or is there a different course of action I will need to take?

No, you don't need to re-do the whole 11-step plan. Your sources.list is perfectly fine now. That means we were successful with steps 1-6. Progress!

At this point, it's looking like an internet connection problem. Gotta be connected to do the rest of this.

1. Get connected via ethernet.

2. Do steps 7 - 11 once connected.

Greenstar

---

### Post by ajmetalhed on 2008-04-10
You mean a wired connection?  Thats a problem because the modem is in the parents' room, and my computer is in my room, and I don't really have a way to get an ethernet connection into my room.  Are there any other possibilities?

---

### Post by greenstar on 2008-04-10
Get a longer ethernet cable or go somewhere else and plug in. AFAIK, you're going to have to connect to the internet to finish this.

Edit: On second thought, you can probably work around your obstacle.

You don't have to necessarily run a cable to your pc's location, just take it to the other room, plug it up, let it update and then install madwifi-tools. After that you should be able to configure & use wireless without need of ethernet.

-or-

You might be able to get 'er done by downloading madwifi-tools and then installing the .deb. Use these links from us.archive.ubuntu.com:
[For a 32-bit install]("http://us.archive.ubuntu.com/ubuntu/pool/universe/m/madwifi-tools/madwifi-tools_0.9.3+dfsg-1_i386.deb")
[For a 64-bit install]("http://us.archive.ubuntu.com/ubuntu/pool/universe/m/madwifi-tools/madwifi-tools_0.9.3+dfsg-1_amd64.deb")
After that you should be able to configure & use wireless without need of ethernet.

HTH,

Greenstar

---

### Post by ajmetalhed on 2008-04-13
i downloaded the 32-bit .deb from the archive and successfully installed it, but now I'm not sure what the command line is to configure the card with madwifi-tools.  I'm going to spend some time on the madwifi website and figure this out.

Thank you for your help!

---

