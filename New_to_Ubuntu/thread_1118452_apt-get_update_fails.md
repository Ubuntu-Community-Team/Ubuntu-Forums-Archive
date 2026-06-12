---
title: "apt-get update fails"
date: 2009-04-07
forum: New to Ubuntu
---

### Post by Miles_Prower on 2009-04-07
Running sudo apt-get update gets me this:
```
taels@tornado:~$ sudo apt-get update
Hit http://wine.budgetdedicated.com intrepid Release.gpg
Ign http://wine.budgetdedicated.com intrepid/main Translation-en_US
Hit http://mx.archive.ubuntu.com intrepid Release.gpg               
Ign http://mx.archive.ubuntu.com intrepid/main Translation-en_US                
Hit http://wine.budgetdedicated.com intrepid Release                            
Ign http://mx.archive.ubuntu.com intrepid/restricted Translation-en_US          
Ign http://mx.archive.ubuntu.com intrepid/universe Translation-en_US 
Ign http://mx.archive.ubuntu.com intrepid/multiverse Translation-en_US
Hit http://mx.archive.ubuntu.com intrepid-updates Release.gpg        
Ign http://mx.archive.ubuntu.com intrepid-updates/main Translation-en_US
Ign http://mx.archive.ubuntu.com intrepid-updates/restricted Translation-en_US
Ign http://mx.archive.ubuntu.com intrepid-updates/universe Translation-en_US
Ign http://mx.archive.ubuntu.com intrepid-updates/multiverse Translation-en_US
Hit http://mx.archive.ubuntu.com intrepid Release                    
Ign http://wine.budgetdedicated.com intrepid/main Packages                      
Hit http://mx.archive.ubuntu.com intrepid-updates Release                       
Hit http://wine.budgetdedicated.com intrepid/main Packages                      
Hit http://mx.archive.ubuntu.com intrepid/main Packages              
Hit http://mx.archive.ubuntu.com intrepid/restricted Packages        
Hit http://mx.archive.ubuntu.com intrepid/main Sources
Hit http://mx.archive.ubuntu.com intrepid/restricted Sources
Hit http://mx.archive.ubuntu.com intrepid/universe Packages
Ign http://ppa.launchpad.net intrepid Release.gpg
Ign http://ppa.launchpad.net intrepid/main Translation-en_US         
Get:1 http://ppa.launchpad.net intrepid Release.gpg [307B]           
Hit http://security.ubuntu.com intrepid-security Release.gpg         
Ign http://security.ubuntu.com intrepid-security/main Translation-en_US
Ign http://security.ubuntu.com intrepid-security/restricted Translation-en_US
Ign http://ppa.launchpad.net intrepid/main Translation-en_US
Ign http://ppa.launchpad.net intrepid Release  
Hit http://mx.archive.ubuntu.com intrepid/universe Sources
Hit http://mx.archive.ubuntu.com intrepid/multiverse Packages
Hit http://mx.archive.ubuntu.com intrepid/multiverse Sources
Hit http://mx.archive.ubuntu.com intrepid-updates/main Packages
Hit http://mx.archive.ubuntu.com intrepid-updates/restricted Packages
Hit http://mx.archive.ubuntu.com intrepid-updates/main Sources
Hit http://mx.archive.ubuntu.com intrepid-updates/restricted Sources 
Hit http://mx.archive.ubuntu.com intrepid-updates/universe Packages  
Get:2 http://ppa.launchpad.net intrepid Release [46.7kB]
Ign http://security.ubuntu.com intrepid-security/universe Translation-en_US 
Ign http://security.ubuntu.com intrepid-security/multiverse Translation-en_US
Hit http://security.ubuntu.com intrepid-security Release
Hit http://mx.archive.ubuntu.com intrepid-updates/universe Sources  
Hit http://mx.archive.ubuntu.com intrepid-updates/multiverse Packages
Hit http://mx.archive.ubuntu.com intrepid-updates/multiverse Sources
Ign http://ppa.launchpad.net intrepid/main Packages                 
Hit http://security.ubuntu.com intrepid-security/main Packages
Ign http://ppa.launchpad.net intrepid/main Packages
Ign http://ppa.launchpad.net intrepid/main Sources
Hit http://security.ubuntu.com intrepid-security/restricted Packages
Hit http://security.ubuntu.com intrepid-security/main Sources
Hit http://security.ubuntu.com intrepid-security/restricted Sources
Hit http://security.ubuntu.com intrepid-security/universe Packages
Err http://ppa.launchpad.net intrepid/main Packages
  404 Not Found
Hit http://security.ubuntu.com intrepid-security/universe Sources
Hit http://security.ubuntu.com intrepid-security/multiverse Packages
Hit http://security.ubuntu.com intrepid-security/multiverse Sources
Hit http://ppa.launchpad.net intrepid/main Packages
Hit http://ppa.launchpad.net intrepid/main Sources
Fetched 308B in 1s (171B/s)
W: Failed to fetch http://ppa.launchpad.net/tcarrez/ubuntu/dists/intrepid/main/binary-amd64/Packages.gz  404 Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.
taels@tornado:~$ 

```

It used to give me this error about a missing key:
```
W: GPG error: http://ppa.launchpad.net intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 43C0AFF0D7FAE680
W: Failed to fetch http://ppa.launchpad.net/tcarrez/ubuntu/dists/intrepid/main/binary-amd64/Packages.gz  404 Not Found

```
, but it does not since (I think) I added the key it was complaining about:
```
taels@tornado:~$ gpg --keyserver subkeys.pgp.net --recv 43C0AFF0D7FAE680
gpg: requesting key D7FAE680 from hkp server subkeys.pgp.net
gpg: key D7FAE680: public key "Launchpad PPA for Team XBMC Intrepid" imported
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
taels@tornado:~$ gpg --export --armor 43C0AFF0D7FAE680 | sudo apt-key add -
OK

```


... what's it missing now? is it a dead link or something? I tried to look for info on the url that it's getting the 404 error on, but I couldn't come up with anything more than that it's got something to do with samba. Anyone know what's going on? I'm in a bit over my head.

---

### Post by twistedvision24 on 2009-04-07
Have you updated your sources.list file with the correct sources?

---

### Post by sahabcse on 2009-04-07
Paste 

/etc/apt/sources.list

---

### Post by Miles_Prower on 2009-04-07
My sources.list :
```
# deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release amd64 (20081029.2)]/ intrepid main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://mx.archive.ubuntu.com/ubuntu/ intrepid main restricted
deb-src http://mx.archive.ubuntu.com/ubuntu/ intrepid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://mx.archive.ubuntu.com/ubuntu/ intrepid-updates main restricted
deb-src http://mx.archive.ubuntu.com/ubuntu/ intrepid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://mx.archive.ubuntu.com/ubuntu/ intrepid universe
deb-src http://mx.archive.ubuntu.com/ubuntu/ intrepid universe
deb http://mx.archive.ubuntu.com/ubuntu/ intrepid-updates universe
deb-src http://mx.archive.ubuntu.com/ubuntu/ intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://mx.archive.ubuntu.com/ubuntu/ intrepid multiverse
deb-src http://mx.archive.ubuntu.com/ubuntu/ intrepid multiverse
deb http://mx.archive.ubuntu.com/ubuntu/ intrepid-updates multiverse
deb-src http://mx.archive.ubuntu.com/ubuntu/ intrepid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://mx.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse
# deb-src http://mx.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu intrepid partner
# deb-src http://archive.canonical.com/ubuntu intrepid partner

deb http://security.ubuntu.com/ubuntu intrepid-security main restricted
deb-src http://security.ubuntu.com/ubuntu intrepid-security main restricted
deb http://security.ubuntu.com/ubuntu intrepid-security universe
deb-src http://security.ubuntu.com/ubuntu intrepid-security universe
deb http://security.ubuntu.com/ubuntu intrepid-security multiverse
deb-src http://security.ubuntu.com/ubuntu intrepid-security multiverse
deb http://ppa.launchpad.net/tcarrez/ubuntu intrepid main
deb http://ppa.launchpad.net/team-xbmc-intrepid/ubuntu intrepid main
deb-src http://ppa.launchpad.net/team-xbmc-intrepid/ubuntu intrepid main
```

---

### Post by duanedesign on 2009-04-07
I do not see tcarrez on index of ppas at [http://ppa.launchpad.net/](http://ppa.launchpad.net/)


EDIT: here is Thierry's wiki and Launchpad page (looks like he changed it to ttx):

[https://wiki.ubuntu.com/ThierryCarrez](https://wiki.ubuntu.com/ThierryCarrez)

[https://launchpad.net/~ttx](https://launchpad.net/~ttx)

---

### Post by Miles_Prower on 2009-04-07
Hmm.. seems like this is related to xbmc, which I've installed, but never used. Will uninstalling it remove the associated sources.list entry(s)? If not, how would I do this manually?

edit: pwned noobs by uninstalling xbmc via apt, then commented out the xbmc-related entries in sources.list. The new sources.list file is the same as the old one except for these changes:
```
#i've commented these out because I no longer use xbmc
#deb http://ppa.launchpad.net/tcarrez/ubuntu intrepid main
#deb http://ppa.launchpad.net/team-xbmc-intrepid/ubuntu intrepid main
#deb-src http://ppa.launchpad.net/team-xbmc-intrepid/ubuntu intrepid main

```

now... how do I mark this thread as solved?

---

