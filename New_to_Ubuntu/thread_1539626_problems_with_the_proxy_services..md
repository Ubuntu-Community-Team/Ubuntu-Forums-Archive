---
title: "problems with the proxy services."
date: 2010-07-26
forum: New to Ubuntu
---

### Post by plurga on 2010-07-26
well , I have ubuntu 9.04 installed on vmware workstation 6.0 ; the computer belongs to my company , so here everybody use guindous , so I installed vmware to keep working on ubuntu :)
well the point is that here in the company we surf over the internnet in a proxy service. On ubuntu I surf over the inter pretty good , but the problem is that when I try to update the system , install whatever program , change the software soucer I get this error :

gabriel@matrix:~$ sudo apt-get update
[sudo] password for gabriel:
Ign [http://ubuntu.patan.com.ar](http://ubuntu.patan.com.ar) jaunty Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty Release.gpg
Ign [http://ubuntu.patan.com.ar](http://ubuntu.patan.com.ar) jaunty/main Translation-en_US
Ign [http://ubuntu.patan.com.ar](http://ubuntu.patan.com.ar) jaunty/restricted Translation-en_US
Ign [http://ubuntu.patan.com.ar](http://ubuntu.patan.com.ar) jaunty/universe Translation-en_US
Ign [http://ubuntu.patan.com.ar](http://ubuntu.patan.com.ar) jaunty/multiverse Translation-en_US
Ign [http://ubuntu.patan.com.ar](http://ubuntu.patan.com.ar) jaunty-updates Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/main Translation-en_US
Ign [http://ubuntu.patan.com.ar](http://ubuntu.patan.com.ar) jaunty-security Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/main Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/restricted Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/main Sources
Ign [http://ubuntu.patan.com.ar](http://ubuntu.patan.com.ar) jaunty/main Packages
Ign [http://ubuntu.patan.com.ar](http://ubuntu.patan.com.ar) jaunty/restricted Packages
Ign [http://ubuntu.patan.com.ar](http://ubuntu.patan.com.ar) jaunty/main Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/restricted Sources
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/main Packages
  404 Not Found
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/restricted Packages
  404 Not Found
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/main Sources
  404 Not Found
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/restricted Sources
  404 Not Found
Ign [http://ubuntu.patan.com.ar](http://ubuntu.patan.com.ar) jaunty-updates/main Packages
Ign [http://ubuntu.patan.com.ar](http://ubuntu.patan.com.ar) jaunty-updates/restricted Packages
Ign [http://ubuntu.patan.com.ar](http://ubuntu.patan.com.ar) jaunty-updates/main Sources
Ign [http://ubuntu.patan.com.ar](http://ubuntu.patan.com.ar) jaunty-updates/restricted Sources
Ign [http://ubuntu.patan.com.ar](http://ubuntu.patan.com.ar) jaunty-updates/universe Packages
Ign [http://ubuntu.patan.com.ar](http://ubuntu.patan.com.ar) jaunty-updates/universe Sources
Ign [http://ubuntu.patan.com.ar](http://ubuntu.patan.com.ar) jaunty-updates/multiverse Packages
Ign [http://ubuntu.patan.com.ar](http://ubuntu.patan.com.ar) jaunty-updates/multiverse Sources
rces
Ign [http://ubuntu.patan.com.ar](http://ubuntu.patan.com.ar) jaunty-updates/universe Packages
Ign [http://ubuntu.patan.com.ar](http://ubuntu.patan.com.ar) jaunty-updates/universe Sources
Ign [http://ubuntu.patan.com.ar](http://ubuntu.patan.com.ar) jaunty-updates/multiverse Packages
Ign [http://ubuntu.patan.com.ar](http://ubuntu.patan.com.ar) jaunty-updates/multiverse Sources
Ign [http://ubuntu.patan.com.ar](http://ubuntu.patan.com.ar) jaunty-security/main Packages
Ign [http://ubuntu.patan.com.ar](http://ubuntu.patan.com.ar) jaunty-security/restricted Packages
Ign [http://ubuntu.patan.com.ar](http://ubuntu.patan.com.ar) jaunty-security/main Sources
Ign [http://ubuntu.patan.com.ar](http://ubuntu.patan.com.ar) jaunty-security/restricted Sources
Ign [http://ubuntu.patan.com.ar](http://ubuntu.patan.com.ar) jaunty-security/universe Packages
Ign [http://ubuntu.patan.com.ar](http://ubuntu.patan.com.ar) jaunty-security/universe Sources
Ign [http://ubuntu.patan.com.ar](http://ubuntu.patan.com.ar) jaunty-security/multiverse Packages
Ign [http://ubuntu.patan.com.ar](http://ubuntu.patan.com.ar) jaunty-security/multiverse Sources
Err [http://ubuntu.patan.com.ar](http://ubuntu.patan.com.ar) jaunty/main Packages
  404 Not Found
Err [http://ubuntu.patan.com.ar](http://ubuntu.patan.com.ar) jaunty/restricted Packages
  404 Not Found
Err [http://ubuntu.patan.com.ar](http://ubuntu.patan.com.ar) jaunty/main Sources
  404 Not Found
Err [http://ubuntu.patan.com.ar](http://ubuntu.patan.com.ar) jaunty/restricted Sources
  404 Not Found
Err [http://ubuntu.patan.com.ar](http://ubuntu.patan.com.ar) jaunty/universe Packages
  404 Not Found
Err [http://ubuntu.patan.com.ar](http://ubuntu.patan.com.ar) jaunty/universe Sources
  404 Not Found
Err [http://ubuntu.patan.com.ar](http://ubuntu.patan.com.ar) jaunty/multiverse Packages
  404 Not Found
Err [http://ubuntu.patan.com.ar](http://ubuntu.patan.com.ar) jaunty/multiverse Sources
  404 Not Found
Err [http://ubuntu.patan.com.ar](http://ubuntu.patan.com.ar) jaunty-updates/main Packages
  404 Not Found
  404 Not Found
Err [http://ubuntu.patan.com.ar](http://ubuntu.patan.com.ar) jaunty-security/restricted Sources
  404 Not Found
Err [http://ubuntu.patan.com.ar](http://ubuntu.patan.com.ar) jaunty-security/universe Packages
  404 Not Found
Err [http://ubuntu.patan.com.ar](http://ubuntu.patan.com.ar) jaunty-security/universe Sources
  404 Not Found
Err [http://ubuntu.patan.com.ar](http://ubuntu.patan.com.ar) jaunty-security/multiverse Packages
  404 Not Found
Err [http://ubuntu.patan.com.ar](http://ubuntu.patan.com.ar) jaunty-security/multiverse Sources
  404 Not Found
W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/jaunty/main/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/jaunty/main/binary-i386/Packages) 404 Not Found

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/jaunty/restricted/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/jaunty/restricted/binary-i386/Packages) 404 Not Found

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/jaunty/main/source/Sources](http://archive.ubuntu.com/ubuntu/dists/jaunty/main/source/Sources) 404 Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.
gabriel@matrix:~$ W: Failed to fetch [http://ubuntu.patan.com.ar/ubuntu/dists/jaunty/multiverse/binary-i386/Packages](http://ubuntu.patan.com.ar/ubuntu/dists/jaunty/multiverse/binary-i386/Packages) 404 Not Found
bash: W:: command not found
gabriel@matrix:~$

I have figured out around a bunch forums :

1.- I have configured the proxy in the web borwser , bcs I could not surf until I did that.
2.- in the synaptic also I configured the proxy and again the problem
3.- gabriel@matrix:/etc/apt$ cat sources.list
# deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)]/ jaunty main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://ubuntu.patan.com.ar/ubuntu/](http://ubuntu.patan.com.ar/ubuntu/) jaunty main restricted
deb-src [http://ubuntu.patan.com.ar/ubuntu/](http://ubuntu.patan.com.ar/ubuntu/) jaunty main restricted

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty main restricted # I add this lines bcs I saw in a forum
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty main restricted # I add this lines bcs I saw in a forum

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ubuntu.patan.com.ar/ubuntu/](http://ubuntu.patan.com.ar/ubuntu/) jaunty-updates main restricted
deb-src [http://ubuntu.patan.com.ar/ubuntu/](http://ubuntu.patan.com.ar/ubuntu/) jaunty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://ubuntu.patan.com.ar/ubuntu/](http://ubuntu.patan.com.ar/ubuntu/) jaunty universe
deb-src [http://ubuntu.patan.com.ar/ubuntu/](http://ubuntu.patan.com.ar/ubuntu/) jaunty universe
deb [http://ubuntu.patan.com.ar/ubuntu/](http://ubuntu.patan.com.ar/ubuntu/) jaunty-updates universe
deb-src [http://ubuntu.patan.com.ar/ubuntu/](http://ubuntu.patan.com.ar/ubuntu/) jaunty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://ubuntu.patan.com.ar/ubuntu/](http://ubuntu.patan.com.ar/ubuntu/) jaunty multiverse
deb-src [http://ubuntu.patan.com.ar/ubuntu/](http://ubuntu.patan.com.ar/ubuntu/) jaunty multiverse
deb [http://ubuntu.patan.com.ar/ubuntu/](http://ubuntu.patan.com.ar/ubuntu/) jaunty-updates multiverse
deb-src [http://ubuntu.patan.com.ar/ubuntu/](http://ubuntu.patan.com.ar/ubuntu/) jaunty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://mx.archive.ubuntu.com/ubuntu/](http://mx.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse
# deb-src [http://mx.archive.ubuntu.com/ubuntu/](http://mx.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner

deb [http://ubuntu.patan.com.ar/ubuntu/](http://ubuntu.patan.com.ar/ubuntu/) jaunty-security main restricted
deb-src [http://ubuntu.patan.com.ar/ubuntu/](http://ubuntu.patan.com.ar/ubuntu/) jaunty-security main restricted
deb [http://ubuntu.patan.com.ar/ubuntu/](http://ubuntu.patan.com.ar/ubuntu/) jaunty-security universe
deb-src [http://ubuntu.patan.com.ar/ubuntu/](http://ubuntu.patan.com.ar/ubuntu/) jaunty-security universe
deb [http://ubuntu.patan.com.ar/ubuntu/](http://ubuntu.patan.com.ar/ubuntu/) jaunty-security multiverse
deb-src [http://ubuntu.patan.com.ar/ubuntu/](http://ubuntu.patan.com.ar/ubuntu/) jaunty-security multiverse

 i have changed servers from , costa rica , mexico , argentina , usa , canada , and the result is the same.
well , there is something funny bcs when i change from 1 server , it starts downloading package information but i got the same error.

4.- I edit the file /etc/apt/apt.conf.d/proxy
[email]gabriel@matrix:/etc/apt/apt.conf[/email].d$ cat proxy
Acquire::http::Proxy "http://autocache.hp.com:8080";

when i issue the command :

[email]gabriel@matrix:/etc/apt/apt.conf[/email].d$ sudo apt-get update
2% [Connecting to autocache.hp.com (16.228.10.197)] [Connecting to autocache.hp.com (16.236.18.243)]

almost the command take off , but there is something a little bit that is not working good , the advice u told me was not bcs there is not error when i issue the update command from 2% not pass ,.

i installed NTLM Authorization Proxy Server and configured it .... note : install in on guindous. 

LISTEN_PORT:5865
PARENT_PROXY:[http://autocache.hp.com/](http://autocache.hp.com/)
PARENT_PROXY_PORT:8080
PARENT_PROXY_TIMEOUT:15
ALLOW_EXTERNAL_CLIENTS:0
FRIENDLY_IPS:
URL_LOG:0
MAX_CONNECTION_BACKLOG:5
Accept: image/gif, image/x-xbitmap, image/jpeg, image/pjpeg, application/vnd.ms-excel, application/msword, application/vnd.ms-powerpoint, */*
User-Agent: Mozilla/4.0 (compatible; MSIE 5.5; Windows 98)
NT_HOSTNAME:
NT_DOMAIN:AMERICAS
USER:username_to_use
PASSWORD:your_nt_password
LM_PART:1
NT_PART:0
NTLM_FLAGS: 06820000
NTLM_TO_BASIC:0
DEBUG:0
BIN_DEBUG:0
SCR_DEBUG:0
AUTH_DEBUG:0

and still the same problem 

in all the forums I have visited anybody has resolved the issue , bcs there are a ton of people that have the same problem like me ,,, I dont know what else do I have to do ??

help me pls.

Saludos.

---

### Post by sandyd on 2010-07-26
easy. your using ubuntu jaunty, which is not supported anymore. time for an upgrade or reinstall...

---

### Post by plurga on 2010-07-27
hi , hope u are ok 
well it's not easy as u say honey bcs i tried to upgrade my ubuntu but i get this : 

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty/main/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/jaunty/main/i18n/Translation-en_US.bz2)  Unable to connect to **autocache.hp.com 8080**:  :( , but ok , i'll keep searching abt the issue but if i did find anything , i will do the last one , reinstall 

saludos,.

---

### Post by overdrank on 2010-07-27
Hi and 9.04 Jaunty is supported until October 2010.

---

### Post by plurga on 2010-07-27
do u think that do i have to jump the proxy server from my company to get the updates or break the proxy server ?

---

### Post by sandyd on 2010-07-27
> **plurga said:**
> well , I have ubuntu 9.04 installed on vmware workstation 6.0 ; the computer belongs to my company , so here everybody use guindous , so I installed vmware to keep working on ubuntu :)
well the point is that here in the company we surf over the internnet in a proxy service. On ubuntu I surf over the inter pretty good , but the problem is that when I try to update the system , install whatever program , change the software soucer I get this error :

gabriel@matrix:~$ sudo apt-get update
[sudo] password for gabriel:
Ign [http://ubuntu.patan.com.ar](http://ubuntu.patan.com.ar) jaunty Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty Release.gpg
Ign [http://ubuntu.patan.com.ar](http://ubuntu.patan.com.ar) jaunty/main Translation-en_US
Ign [http://ubuntu.patan.com.ar](http://ubuntu.patan.com.ar) jaunty/restricted Translation-en_US
Ign [http://ubuntu.patan.com.ar](http://ubuntu.patan.com.ar) jaunty/universe Translation-en_US
Ign [http://ubuntu.patan.com.ar](http://ubuntu.patan.com.ar) jaunty/multiverse Translation-en_US
Ign [http://ubuntu.patan.com.ar](http://ubuntu.patan.com.ar) jaunty-updates Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/main Translation-en_US
Ign [http://ubuntu.patan.com.ar](http://ubuntu.patan.com.ar) jaunty-security Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/main Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/restricted Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/main Sources
Ign [http://ubuntu.patan.com.ar](http://ubuntu.patan.com.ar) jaunty/main Packages
Ign [http://ubuntu.patan.com.ar](http://ubuntu.patan.com.ar) jaunty/restricted Packages
Ign [http://ubuntu.patan.com.ar](http://ubuntu.patan.com.ar) jaunty/main Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/restricted Sources
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/main Packages
  404 Not Found
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/restricted Packages
  404 Not Found
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/main Sources
  404 Not Found
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/restricted Sources
  404 Not Found
Ign [http://ubuntu.patan.com.ar](http://ubuntu.patan.com.ar) jaunty-updates/main Packages
Ign [http://ubuntu.patan.com.ar](http://ubuntu.patan.com.ar) jaunty-updates/restricted Packages
Ign [http://ubuntu.patan.com.ar](http://ubuntu.patan.com.ar) jaunty-updates/main Sources
Ign [http://ubuntu.patan.com.ar](http://ubuntu.patan.com.ar) jaunty-updates/restricted Sources
Ign [http://ubuntu.patan.com.ar](http://ubuntu.patan.com.ar) jaunty-updates/universe Packages
Ign [http://ubuntu.patan.com.ar](http://ubuntu.patan.com.ar) jaunty-updates/universe Sources
Ign [http://ubuntu.patan.com.ar](http://ubuntu.patan.com.ar) jaunty-updates/multiverse Packages
Ign [http://ubuntu.patan.com.ar](http://ubuntu.patan.com.ar) jaunty-updates/multiverse Sources
rces
Ign [http://ubuntu.patan.com.ar](http://ubuntu.patan.com.ar) jaunty-updates/universe Packages
Ign [http://ubuntu.patan.com.ar](http://ubuntu.patan.com.ar) jaunty-updates/universe Sources
Ign [http://ubuntu.patan.com.ar](http://ubuntu.patan.com.ar) jaunty-updates/multiverse Packages
Ign [http://ubuntu.patan.com.ar](http://ubuntu.patan.com.ar) jaunty-updates/multiverse Sources
Ign [http://ubuntu.patan.com.ar](http://ubuntu.patan.com.ar) jaunty-security/main Packages
Ign [http://ubuntu.patan.com.ar](http://ubuntu.patan.com.ar) jaunty-security/restricted Packages
Ign [http://ubuntu.patan.com.ar](http://ubuntu.patan.com.ar) jaunty-security/main Sources
Ign [http://ubuntu.patan.com.ar](http://ubuntu.patan.com.ar) jaunty-security/restricted Sources
Ign [http://ubuntu.patan.com.ar](http://ubuntu.patan.com.ar) jaunty-security/universe Packages
Ign [http://ubuntu.patan.com.ar](http://ubuntu.patan.com.ar) jaunty-security/universe Sources
Ign [http://ubuntu.patan.com.ar](http://ubuntu.patan.com.ar) jaunty-security/multiverse Packages
Ign [http://ubuntu.patan.com.ar](http://ubuntu.patan.com.ar) jaunty-security/multiverse Sources
Err [http://ubuntu.patan.com.ar](http://ubuntu.patan.com.ar) jaunty/main Packages
  404 Not Found
Err [http://ubuntu.patan.com.ar](http://ubuntu.patan.com.ar) jaunty/restricted Packages
  404 Not Found
Err [http://ubuntu.patan.com.ar](http://ubuntu.patan.com.ar) jaunty/main Sources
  404 Not Found
Err [http://ubuntu.patan.com.ar](http://ubuntu.patan.com.ar) jaunty/restricted Sources
  404 Not Found
Err [http://ubuntu.patan.com.ar](http://ubuntu.patan.com.ar) jaunty/universe Packages
  404 Not Found
Err [http://ubuntu.patan.com.ar](http://ubuntu.patan.com.ar) jaunty/universe Sources
  404 Not Found
Err [http://ubuntu.patan.com.ar](http://ubuntu.patan.com.ar) jaunty/multiverse Packages
  404 Not Found
Err [http://ubuntu.patan.com.ar](http://ubuntu.patan.com.ar) jaunty/multiverse Sources
  404 Not Found
Err [http://ubuntu.patan.com.ar](http://ubuntu.patan.com.ar) jaunty-updates/main Packages
  404 Not Found
  404 Not Found
Err [http://ubuntu.patan.com.ar](http://ubuntu.patan.com.ar) jaunty-security/restricted Sources
  404 Not Found
Err [http://ubuntu.patan.com.ar](http://ubuntu.patan.com.ar) jaunty-security/universe Packages
  404 Not Found
Err [http://ubuntu.patan.com.ar](http://ubuntu.patan.com.ar) jaunty-security/universe Sources
  404 Not Found
Err [http://ubuntu.patan.com.ar](http://ubuntu.patan.com.ar) jaunty-security/multiverse Packages
  404 Not Found
Err [http://ubuntu.patan.com.ar](http://ubuntu.patan.com.ar) jaunty-security/multiverse Sources
  404 Not Found
W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/jaunty/main/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/jaunty/main/binary-i386/Packages) 404 Not Found

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/jaunty/restricted/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/jaunty/restricted/binary-i386/Packages) 404 Not Found

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/jaunty/main/source/Sources](http://archive.ubuntu.com/ubuntu/dists/jaunty/main/source/Sources) 404 Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.
gabriel@matrix:~$ W: Failed to fetch [http://ubuntu.patan.com.ar/ubuntu/dists/jaunty/multiverse/binary-i386/Packages](http://ubuntu.patan.com.ar/ubuntu/dists/jaunty/multiverse/binary-i386/Packages) 404 Not Found
bash: W:: command not found
gabriel@matrix:~$

I have figured out around a bunch forums :

1.- I have configured the proxy in the web borwser , bcs I could not surf until I did that.
2.- in the synaptic also I configured the proxy and again the problem
3.- gabriel@matrix:/etc/apt$ cat sources.list
# deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)]/ jaunty main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://ubuntu.patan.com.ar/ubuntu/](http://ubuntu.patan.com.ar/ubuntu/) jaunty main restricted
deb-src [http://ubuntu.patan.com.ar/ubuntu/](http://ubuntu.patan.com.ar/ubuntu/) jaunty main restricted

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty main restricted # I add this lines bcs I saw in a forum
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty main restricted # I add this lines bcs I saw in a forum

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ubuntu.patan.com.ar/ubuntu/](http://ubuntu.patan.com.ar/ubuntu/) jaunty-updates main restricted
deb-src [http://ubuntu.patan.com.ar/ubuntu/](http://ubuntu.patan.com.ar/ubuntu/) jaunty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://ubuntu.patan.com.ar/ubuntu/](http://ubuntu.patan.com.ar/ubuntu/) jaunty universe
deb-src [http://ubuntu.patan.com.ar/ubuntu/](http://ubuntu.patan.com.ar/ubuntu/) jaunty universe
deb [http://ubuntu.patan.com.ar/ubuntu/](http://ubuntu.patan.com.ar/ubuntu/) jaunty-updates universe
deb-src [http://ubuntu.patan.com.ar/ubuntu/](http://ubuntu.patan.com.ar/ubuntu/) jaunty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://ubuntu.patan.com.ar/ubuntu/](http://ubuntu.patan.com.ar/ubuntu/) jaunty multiverse
deb-src [http://ubuntu.patan.com.ar/ubuntu/](http://ubuntu.patan.com.ar/ubuntu/) jaunty multiverse
deb [http://ubuntu.patan.com.ar/ubuntu/](http://ubuntu.patan.com.ar/ubuntu/) jaunty-updates multiverse
deb-src [http://ubuntu.patan.com.ar/ubuntu/](http://ubuntu.patan.com.ar/ubuntu/) jaunty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://mx.archive.ubuntu.com/ubuntu/](http://mx.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse
# deb-src [http://mx.archive.ubuntu.com/ubuntu/](http://mx.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner

deb [http://ubuntu.patan.com.ar/ubuntu/](http://ubuntu.patan.com.ar/ubuntu/) jaunty-security main restricted
deb-src [http://ubuntu.patan.com.ar/ubuntu/](http://ubuntu.patan.com.ar/ubuntu/) jaunty-security main restricted
deb [http://ubuntu.patan.com.ar/ubuntu/](http://ubuntu.patan.com.ar/ubuntu/) jaunty-security universe
deb-src [http://ubuntu.patan.com.ar/ubuntu/](http://ubuntu.patan.com.ar/ubuntu/) jaunty-security universe
deb [http://ubuntu.patan.com.ar/ubuntu/](http://ubuntu.patan.com.ar/ubuntu/) jaunty-security multiverse
deb-src [http://ubuntu.patan.com.ar/ubuntu/](http://ubuntu.patan.com.ar/ubuntu/) jaunty-security multiverse

 i have changed servers from , costa rica , mexico , argentina , usa , canada , and the result is the same.
well , there is something funny bcs when i change from 1 server , it starts downloading package information but i got the same error.

4.- I edit the file /etc/apt/apt.conf.d/proxy
[EMAIL="gabriel@matrix:/etc/apt/apt.conf"]gabriel@matrix:/etc/apt/apt.conf[/EMAIL].d$ cat proxy
Acquire::http::Proxy "http://autocache.hp.com:8080";

when i issue the command :

[EMAIL="gabriel@matrix:/etc/apt/apt.conf"]gabriel@matrix:/etc/apt/apt.conf[/EMAIL].d$ sudo apt-get update
2% [Connecting to autocache.hp.com (16.228.10.197)] [Connecting to autocache.hp.com (16.236.18.243)]

almost the command take off , but there is something a little bit that is not working good , the advice u told me was not bcs there is not error when i issue the update command from 2% not pass ,.

i installed NTLM Authorization Proxy Server and configured it .... note : install in on guindous. 

LISTEN_PORT:5865
PARENT_PROXY:[http://autocache.hp.com/](http://autocache.hp.com/)
PARENT_PROXY_PORT:8080
PARENT_PROXY_TIMEOUT:15
ALLOW_EXTERNAL_CLIENTS:0
FRIENDLY_IPS:
URL_LOG:0
MAX_CONNECTION_BACKLOG:5
Accept: image/gif, image/x-xbitmap, image/jpeg, image/pjpeg, application/vnd.ms-excel, application/msword, application/vnd.ms-powerpoint, */*
User-Agent: Mozilla/4.0 (compatible; MSIE 5.5; Windows 98)
NT_HOSTNAME:
NT_DOMAIN:AMERICAS
USER:username_to_use
PASSWORD:your_nt_password
LM_PART:1
NT_PART:0
NTLM_FLAGS: 06820000
NTLM_TO_BASIC:0
DEBUG:0
BIN_DEBUG:0
SCR_DEBUG:0
AUTH_DEBUG:0

and still the same problem 

in all the forums I have visited anybody has resolved the issue , bcs there are a ton of people that have the same problem like me ,,, I dont know what else do I have to do ??

help me pls.

Saludos.

try running
```

gksudo gedit /etc/apt/sources.list
```
replace with
```

# deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)]/ jaunty main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://archives.ubuntu.com/ubuntu/ jaunty main restricted
deb-src http://archives.ubuntu.com/ubuntu/ jaunty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archives.ubuntu.com/ubuntu/ jaunty-updates main restricted
deb-src http://archives.ubuntu.com/ubuntu/ jaunty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://archives.ubuntu.com/ubuntu/ jaunty universe
deb-src http://archives.ubuntu.com/ubuntu/ jaunty universe
deb http://archives.ubuntu.com/ubuntu/ jaunty-updates universe
deb-src http://archives.ubuntu.com/ubuntu/ jaunty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archives.ubuntu.com/ubuntu/ jaunty multiverse
deb-src http://archives.ubuntu.com/ubuntu/ jaunty multiverse
deb http://archives.ubuntu.com/ubuntu/ jaunty-updates multiverse
deb-src http://archives.ubuntu.com/ubuntu/ jaunty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://mx.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse
deb-src http://mx.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu jaunty partner
deb-src http://archive.canonical.com/ubuntu jaunty partner

deb http://archives.ubuntu.com/ubuntu/ jaunty-security main restricted
deb-src http://archives.ubuntu.com/ubuntu/ jaunty-security main restricted
deb http://archives.ubuntu.com/ubuntu/ jaunty-security universe
deb-src http://archives.ubuntu.com/ubuntu/ jaunty-security universe
deb http://archives.ubuntu.com/ubuntu/ jaunty-security multiverse
deb-src http://archives.ubuntu.com/ubuntu/ jaunty-security multiverse

```

---

### Post by plurga on 2010-07-27
hola carlee 

i replaced the file like u said , but check it out : 

gabriel@matrix:~$ sudo apt-get update
0% [Connecting to autocache.hp.com (16.236.18.243)] [Connecting to autocache.hp.......................

i can wait until tomorrow to reach the update but anything wont happen. 

what do u think ????

---

### Post by sandyd on 2010-07-27
> **plurga said:**
> hola carlee 

i replaced the file like u said , but check it out : 

gabriel@matrix:~$ sudo apt-get update
0% [Connecting to autocache.hp.com (16.236.18.243)] [Connecting to autocache.hp.......................

i can wait until tomorrow to reach the update but anything wont happen. 

what do u think ????
seems to be a problem with the proxy.

---

### Post by plurga on 2010-07-29
i knew that since the begining sweet , but ok , i'll try to break the proxy or jump it hehehe ,
thanks for u time. 
hugs and kisses !!

---

