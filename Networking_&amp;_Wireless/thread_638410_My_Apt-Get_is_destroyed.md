---
title: "My Apt-Get is destroyed"
date: 2007-12-12
forum: Networking &amp; Wireless
---

### Post by CameronCalver on 2007-12-12
Hello well recently i noticed that apt or synaptic would not work on my server. when i do
```
sudo apt-get update
``` it just times out this is how the first command shows
```
server@ubuntu:~$ sudo apt-get update
Err http://security.ubuntu.com dapper-security Release.gpg
  Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
Err http://archive.ubuntu.com dapper-updates Release.gpg
  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err http://archive.ubuntu.com dapper-backports Release.gpg
  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
0% [Connecting to archive.ubuntu.com (1.0.0.0)]

```
The internet is working perfectly and so is the smb server which has never failed.
my source list is as follows.
```
deb http://security.ubuntu.com/ubuntu/ dapper-security main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu/ dapper-updates main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu/ dapper main restricted universe multiverse

```

yes very basic but i just want at least that to work at the start. I am running Ubuntu Dapper Drake which is getting old now and thats why i need apt to work so i can upgrade. Does anyone no what is goin on here?

---

### Post by anubhavrocks on 2007-12-12
If you give the following address on the browser
[http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/)

Does it reach it?

---

### Post by CameronCalver on 2007-12-12
sorry i will have to wait till tommorow to check that our sorry

---

### Post by CameronCalver on 2007-12-12
yeah that worked so what do i do now?

---

### Post by anubhavrocks on 2007-12-13
That was to make sure that your network is okay :)
give it one more try 
sudo apt-get update
if that does not work try changing your repos,you can do that by prefixing us. or some other country   to the addresses for example

 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates

---

### Post by CameronCalver on 2007-12-13
um ok i tryed that example of yours and this is what happened
```
server@ubuntu:~$ sudo apt-get update
E: Type 'http://us.archive.ubuntu.com' is not known on line 1 in source list /etc/apt/sources.list


```

---

### Post by anubhavrocks on 2007-12-15
can you please post your current
```
/etc/apt/sources.list
```

---

### Post by anubhavrocks on 2007-12-15
You also did not prefix 
deb
that caused the error

---

### Post by CameronCalver on 2007-12-15
i already posted my sources list
```
deb http://security.ubuntu.com/ubuntu/ dapper-security main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu/ dapper-updates main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu/ dapper main restricted universe multiverse
```

and i tryed to put deb infront and it did same thing ...

---

### Post by mellowd on 2007-12-15
Just out of interest, if you type aptitude update what do you get?

---

### Post by anubhavrocks on 2007-12-15
> **mellowd said:**
> Just out of interest, if you type aptitude update what do you get?

Aptitude is another front end to the package manager,it should give you similar results as apt-get update

---

### Post by mellowd on 2007-12-15
> **anubhavrocks said:**
> Aptitude is another front end to the package manager,it should give you similar results as apt-get update

Should, maybe. It would be good to test though.

---

### Post by anubhavrocks on 2007-12-15
> **CameronCalver said:**
> i already posted my sources list
```
deb http://security.ubuntu.com/ubuntu/ dapper-security main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu/ dapper-updates main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu/ dapper main restricted universe multiverse
```

and i tryed to put deb infront and it did same thing ...

Try this command and please copy paste  the actual output you get.  
sudo apt-get check

Do you by any chance use proxy to get to the internet?

---

### Post by anubhavrocks on 2007-12-15
> **mellowd said:**
> Should, maybe. It would be good to test though.

Its _equivalent_ to apt-get update.

---

### Post by mellowd on 2007-12-15
> **anubhavrocks said:**
> Its _equivalent_ to apt-get update.


No, they are not exactly the same thing

it will take 1 second to test it, why are you so against that?

---

### Post by anubhavrocks on 2007-12-15
I am talking from the developer point of view,You may consult the aptitude manual to further clarify.

---

### Post by CameronCalver on 2007-12-16
> **anubhavrocks said:**
> Try this command and please copy paste  the actual output you get.  
sudo apt-get check

Do you by any chance use proxy to get to the internet?

yes yes i USED to use a proxy but not anymore i and no longer using the proxy...at least i dont THINK i am ? and ill do that command on monday when im at the work 

p.s guys ill do the aptitude one when i get there but in the mean time stop the arguing kk its not a big deal if i use apt-get or apptitude

---

### Post by anubhavrocks on 2007-12-16
If you are using proxy,try using Synaptic.Its pretty straightforward to add proxy config.

---

### Post by CameronCalver on 2007-12-16
nooo i dont use the proxy any more yeah it died and in synaptic in network i clicked direct access not the proxy

---

### Post by CameronCalver on 2007-12-20
guys can someone give me a basic source.list so i can get this working??

---

### Post by mellowd on 2007-12-20
```
#
# deb cdrom:[Ubuntu-Server 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted

# deb cdrom:[Ubuntu-Server 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://gb.archive.ubuntu.com/ubuntu/ gutsy main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://gb.archive.ubuntu.com/ubuntu/ gutsy universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ gutsy universe
deb http://gb.archive.ubuntu.com/ubuntu/ gutsy-updates universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://gb.archive.ubuntu.com/ubuntu/ gutsy multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ gutsy multiverse
deb http://gb.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://gb.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
# deb-src http://gb.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu gutsy partner
# deb-src http://archive.canonical.com/ubuntu gutsy partner

deb http://security.ubuntu.com/ubuntu gutsy-security main restricted
deb-src http://security.ubuntu.com/ubuntu gutsy-security main restricted
deb http://security.ubuntu.com/ubuntu gutsy-security universe
deb-src http://security.ubuntu.com/ubuntu gutsy-security universe
deb http://security.ubuntu.com/ubuntu gutsy-security multiverse
deb-src http://security.ubuntu.com/ubuntu gutsy-security multiverse

```

---

### Post by mellowd on 2007-12-20
I've commented out the cd-rom but you can add it back if you like

---

