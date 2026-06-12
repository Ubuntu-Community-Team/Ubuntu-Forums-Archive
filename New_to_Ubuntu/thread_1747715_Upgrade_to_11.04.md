---
title: "Upgrade to 11.04"
date: 2011-05-02
forum: New to Ubuntu
---

### Post by bigal1932flying on 2011-05-02
Update Manager said I could upgrade to 11.04 so went ahead.
After downloading all files etc. went to restart and then did not boot.
Tried "Repair broken Packages" "Repair boot loader" "disk check"
but still just get black screen with "Ubuntu 11.04 afrancis-desktop tty1"
then "afrancis-desktop login:" "Password:" then last login details
then "afrancis@afrancis-desktop:~$"
What can I do to fix this?

---

### Post by jjordan12 on 2011-05-03
I have had this happen to me as well. I just reinstalled from a disc clean install and that cleared it mostly out. I just hope that Canonical can fix the upgrade wizard as more and more people upgrade their ubuntu to 11.04.

---

### Post by bigal1932flying on 2011-05-03
Tried running in safe graphics mode. When I try to run Package Manager I receive the message "E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/mirror.optus.net_ubuntu_dists_natty_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report."
Does this help at all?

---

### Post by plucky on 2011-05-03
> **bigal1932flying said:**
> Tried running in safe graphics mode. When I try to run Package Manager I receive the message "E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/mirror.optus.net_ubuntu_dists_natty_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report."
Does this help at all?

Can you try removing the index files with ```
sudo rm -i /var/lib/apt/lists/*
```

It will prompt you for every file to remove,or leave out the -i and it will just remove them all.

Then run ```
sudo apt-get update
``` to reload the index files.


See if that works

Good luck

---

### Post by bigal1932flying on 2011-05-03
Tried both those commands and received the same reply:
"rm: cannot remove `/var/lib/apt/lists/partial': Is a directory"

---

### Post by wilee-nilee on 2011-05-03
> **bigal1932flying said:**
> Tried both those commands and received the same reply:
"rm: cannot remove `/var/lib/apt/lists/partial': Is a directory"

Get to the recovery command line the network stanza you may need the net; plug-in the ethernet cord and see if this command doesn't free up the situation
```
sudo apt-get -f install 
```.

---

### Post by bigal1932flying on 2011-05-03
Think I have had a bit of a break through, tried removing and then installing Update Manager then reinstalled n-vidia driver.
Ubuntu then booted but when I opened Update Manager and tried to install updates I said "Failed to download package files - check your internet connection"
I can browse and download emails quite OK.
So what is the problem?

---

### Post by wilee-nilee on 2011-05-03
> **bigal1932flying said:**
> Think I have had a bit of a break through, tried removing and then installing Update Manager then reinstalled n-vidia driver.
Ubuntu then booted but when I opened Update Manager and tried to install updates I said "Failed to download package files - check your internet connection"
I can browse and download emails quite OK.
So what is the problem?

open software sources and see if things are clicked on.

check the apt sources list.
sudo gedit /etc/apt/sources.list

This last command will allow to read and write it so be careful if unsure just post the list in wrapped code tags. Click on the (#) in the reply panel to generate code tags.

---

### Post by bigal1932flying on 2011-05-04
Tried ticking software sources. No change.
Tried to update in terminal and received:
Err [http://mirror.optus.net/ubuntu/](http://mirror.optus.net/ubuntu/) natty-proposed/universe openoffice.org-common all 1:3.3.0-7ubuntu2
  404  Not Found [IP: 211.29.132.93 80]
Err [http://mirror.optus.net/ubuntu/](http://mirror.optus.net/ubuntu/) natty-proposed/universe openoffice.org-draw all 1:3.3.0-7ubuntu2
  404  Not Found [IP: 211.29.132.93 80]
Err [http://mirror.optus.net/ubuntu/](http://mirror.optus.net/ubuntu/) natty-proposed/universe openoffice.org-gtk all 1:3.3.0-7ubuntu2
  404  Not Found [IP: 211.29.132.93 80]
Err [http://mirror.optus.net/ubuntu/](http://mirror.optus.net/ubuntu/) natty-proposed/universe openoffice.org-kde all 1:3.3.0-7ubuntu2
  404  Not Found [IP: 211.29.132.93 80]
Err [http://mirror.optus.net/ubuntu/](http://mirror.optus.net/ubuntu/) natty-proposed/universe openoffice.org-math all 1:3.3.0-7ubuntu2
  404  Not Found [IP: 211.29.132.93 80]
Failed to fetch [http://mirror.optus.net/ubuntu/pool/universe/o/openoffice.org/openoffice.org-common_3.3.0-7ubuntu2_all.deb](http://mirror.optus.net/ubuntu/pool/universe/o/openoffice.org/openoffice.org-common_3.3.0-7ubuntu2_all.deb) 404  Not Found [IP: 211.29.132.93 80]
Failed to fetch [http://mirror.optus.net/ubuntu/pool/universe/o/openoffice.org/openoffice.org-draw_3.3.0-7ubuntu2_all.deb](http://mirror.optus.net/ubuntu/pool/universe/o/openoffice.org/openoffice.org-draw_3.3.0-7ubuntu2_all.deb) 404  Not Found [IP: 211.29.132.93 80]
Failed to fetch [http://mirror.optus.net/ubuntu/pool/universe/o/openoffice.org/openoffice.org-gtk_3.3.0-7ubuntu2_all.deb](http://mirror.optus.net/ubuntu/pool/universe/o/openoffice.org/openoffice.org-gtk_3.3.0-7ubuntu2_all.deb) 404  Not Found [IP: 211.29.132.93 80]
Failed to fetch [http://mirror.optus.net/ubuntu/pool/universe/o/openoffice.org/openoffice.org-kde_3.3.0-7ubuntu2_all.deb](http://mirror.optus.net/ubuntu/pool/universe/o/openoffice.org/openoffice.org-kde_3.3.0-7ubuntu2_all.deb) 404  Not Found [IP: 211.29.132.93 80]
Failed to fetch [http://mirror.optus.net/ubuntu/pool/universe/o/openoffice.org/openoffice.org-math_3.3.0-7ubuntu2_all.deb](http://mirror.optus.net/ubuntu/pool/universe/o/openoffice.org/openoffice.org-math_3.3.0-7ubuntu2_all.deb) 404  Not Found [IP: 211.29.132.93 80]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
Not sure how to run with --fix-missing?

---

### Post by wilee-nilee on 2011-05-04
The apt sources list I suggested posting is what the computer reads in order to be able to call out to the repos for the update/upgrade. In the terminal run this command, come back to the thread, open a reply click on the [COLOR="Red"](#)[/COLOR] in the reply panel, and paste all the text from the command between the code tags.
```
cat /etc/apt/sources.list
```

I'm looking for something like this, here is my maverick list.
```
 cat /etc/apt/sources.list
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://us.archive.ubuntu.com/ubuntu/ maverick main restricted
# deb-src http://us.archive.ubuntu.com/ubuntu/ maverick main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ maverick-updates main restricted
# deb-src http://us.archive.ubuntu.com/ubuntu/ maverick-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ maverick universe
# deb-src http://us.archive.ubuntu.com/ubuntu/ maverick universe
deb http://us.archive.ubuntu.com/ubuntu/ maverick-updates universe
# deb-src http://us.archive.ubuntu.com/ubuntu/ maverick-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ maverick multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ maverick multiverse
deb http://us.archive.ubuntu.com/ubuntu/ maverick-updates multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ maverick-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ maverick-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ maverick-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu maverick-security main restricted
# deb-src http://security.ubuntu.com/ubuntu maverick-security main restricted
deb http://security.ubuntu.com/ubuntu maverick-security universe
# deb-src http://security.ubuntu.com/ubuntu maverick-security universe
deb http://security.ubuntu.com/ubuntu maverick-security multiverse
# deb-src http://security.ubuntu.com/ubuntu maverick-security multiverse

## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu maverick partner
# deb-src http://archive.canonical.com/ubuntu maverick partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu maverick main
deb http://us.archive.ubuntu.com/ubuntu/ maverick-proposed restricted main multiverse universe
# deb-src http://extras.ubuntu.com/ubuntu maverick main
## Depôt MultiSystem
deb http://liveusb.info/multisystem/depot all main
deb http://download.bitdefender.com/repos/deb/ bitdefender non-free
# deb-src http://download.bitdefender.com/repos/deb/ bitdefender non-free

```

---

### Post by bigal1932flying on 2011-05-04
Had another fiddle with Software Sources and now Update Manager seems to be working OK.
Thanks for your help.
Will just wait a while and give it a few tries before I say that my problems are solved.

---

### Post by wilee-nilee on 2011-05-04
> **bigal1932flying said:**
> Had another fiddle with Software Sources and now Update Manager seems to be working OK.
Thanks for your help.
Will just wait a while and give it a few tries before I say that my problems are solved.

Cool, you can open your source list and look to see if it is similar to mine if needed, the only real difference really is that you would have natty where mine says maverick, except for the few 3rd party repos you see at the bottom. 

If you need a new list check this out.
[http://repogen.simplylinux.ch/](http://repogen.simplylinux.ch/)

Just giving you general stuff, good job getting back from where you were.;)

---

