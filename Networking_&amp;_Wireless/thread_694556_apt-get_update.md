---
title: "apt-get update"
date: 2008-02-12
forum: Networking &amp; Wireless
---

### Post by ubmatu on 2008-02-12
I  think I have a network issue, but it first became illustrated whilst using  apt-get update.
when installing gutsy I got some error message about etc/apt/services.list.
I found that I was unable to browse the internet.
I managed to get the internet working by removing ipv6

I changed the line is /etc/modprobe.d/aliases from:

alias net-pf-10 ipv6

to

alias net-pf-10 off

as advised by [http://ubuntu-tutorials.com/2007/11/18/how-to-disable-ipv6-on-ubuntu-710-gutsy-gibbon/](http://ubuntu-tutorials.com/2007/11/18/how-to-disable-ipv6-on-ubuntu-710-gutsy-gibbon/) and I can browse again.

however, I still can't ping an outside url or use traceroute etc. 
the DNS seems to be working but something is not right.
~$ host [www.ubuntu.com](www.ubuntu.com)

[www.ubuntu.com](www.ubuntu.com) has address 91.189.94.158

;; Warning: Message parser reports malformed message packet.

;; connection timed out; no servers could be reached


~$ ping -c 5  [www.ubuntu.com](www.ubuntu.com)

PING [www.ubuntu.com](www.ubuntu.com) (91.189.94.158) 56(84) bytes of data.



--- [www.ubuntu.com](www.ubuntu.com) ping statistics ---

5 packets transmitted, 0 received, 100% packet loss, time 4010ms


when I first looked at etc/apt/services.list it had all deb and deb-src lines commented out 
# Line commented out by installer because it failed to verify:


I tried to remove the #'s but that didn't seem to resolve anything.
do I need to re-initailise the list before running apt-get again?

source.list = 
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to

# newer versions of the distribution.



deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy main restricted

deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy main restricted



## Major bug fix updates produced after the final release of the

## distribution.

deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted



## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu

## team, and may not be under a free licence. Please satisfy yourself as to

## your rights to use the software. Also, please note that software in

## universe WILL NOT receive any review or updates from the Ubuntu security

## team.

deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy universe

deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy universe

deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy-updates universe

deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy-updates universe



## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 

## team, and may not be under a free licence. Please satisfy yourself as to 

## your rights to use the software. Also, please note that software in 

## multiverse WILL NOT receive any review or updates from the Ubuntu

## security team.

deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy multiverse

deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy multiverse

deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse



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



deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted

deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe

deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse

deb [http://mirror.internode.on.net/pub/ubuntu/ubuntu/](http://mirror.internode.on.net/pub/ubuntu/ubuntu/) gutsy main universe restricted multiverse

deb-src [http://mirror.internode.on.net/pub/ubuntu/ubuntu/](http://mirror.internode.on.net/pub/ubuntu/ubuntu/) gutsy universe main multiverse restricted #Added by software-properties

deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) gutsy-security universe main multiverse restricted

deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) gutsy-security universe main multiverse restricted

deb [http://mirror.internode.on.net/pub/ubuntu/ubuntu/](http://mirror.internode.on.net/pub/ubuntu/ubuntu/) gutsy-updates universe main multiverse restricted

deb-src [http://mirror.internode.on.net/pub/ubuntu/ubuntu/](http://mirror.internode.on.net/pub/ubuntu/ubuntu/) gutsy-updates universe main multiverse restricted

# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse

output from  apt-get update=
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Translation-en_AU

Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Translation-en_AU                  

Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) gutsy Release.gpg                                                                                                 

  Could not connect to au.archive.ubuntu.com:80 (1.0.0.0), connection timed out

Err [http://mirror.internode.on.net](http://mirror.internode.on.net) gutsy Release.gpg                                                                                               

  Could not connect to mirror.internode.on.net:80 (1.0.0.0), connection timed out

Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release.gpg                                          

  Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out

etc...

The thing is, if I browse to the urls in source.list I can save the files. why cant I do it with apt-get?
any idea on whats going on with my network? Thanks for you help.

---

### Post by banewman on 2008-02-12
Comment out this line - 
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
and try again.
:)

---

### Post by ubmatu on 2008-02-12
I updated sources.list to narrate out the cd line.

the results for finding the repositories is still failing :(

Err [http://mirror.internode.on.net](http://mirror.internode.on.net) gutsy Release.gpg                                                                                              
  Could not connect to mirror.internode.on.net:80 (1.0.0.0), connection timed out
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release.gpg                                                                                         
  Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) gutsy Release.gpg                                                  
  Could not connect to au.archive.ubuntu.com:80 (1.0.0.0), connection timed out

etc....

---

