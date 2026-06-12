---
title: "AVI to Mpeg converter"
date: 2009-06-22
forum: New to Ubuntu
---

### Post by Narcoleptic_Insomniac on 2009-06-22
Hello. I know this topic has been made, I searched, and I couldn't figure out how to install any of the programs specified in said topics. This is really annoying, because I'm getting tired of having to download and compile every program I want to install. I really wish there was an easier way. Does anyone know how I can easily get a program to quickly convert 2 avi files to mpeg? It would be greatly appreciated. Thanks.

---

### Post by fugaki on 2009-06-22
try winff

sudo apt-get install winff

---

### Post by Narcoleptic_Insomniac on 2009-06-22
> **fugaki said:**
> try winff

sudo apt-get install winff

Thanks, I'll try that and let you know how it works.

---

### Post by Narcoleptic_Insomniac on 2009-06-22
Says it could not find the package "winff". I ran and update and got the same results.

---

### Post by Arup on 2009-06-22
> **Narcoleptic_Insomniac said:**
> Says it could not find the package "winff". I ran and update and got the same results.

Enable medibuntu repos from [www.medibuntu.org](www.medibuntu.org)

---

### Post by Narcoleptic_Insomniac on 2009-06-22
> **Arup said:**
> Enable medibuntu repos from [www.medibuntu.org](www.medibuntu.org)

How? In my sources list?

---

### Post by jenkinbr on 2009-06-22
> **Narcoleptic_Insomniac said:**
> How? In my sources list?
Yes.

Have a look [here]("https://help.ubuntu.com/community/Medibuntu") for more info.

---

### Post by dmizer on 2009-06-22
> **Narcoleptic_Insomniac said:**
> How? In my sources list?

Instructions are included in the link provided by Arup.

---

### Post by Narcoleptic_Insomniac on 2009-06-22
> **jenkinbr said:**
> Yes.

Have a look [here]("https://help.ubuntu.com/community/Medibuntu") for more info.

I ended up finding that and followed the instructions for Intrepid, only now realizing that I upgraded my distro yesterday, but I got this error when in terminal. 

```

W: GPG error: http://packages.medibuntu.org intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783

```

I'll go start over again with the proper steps and tell you what happens.

---

### Post by jenkinbr on 2009-06-22
You're fine - just run ```
sudo apt-get install medibuntu-keyring
```

---

### Post by Narcoleptic_Insomniac on 2009-06-22
Ok, I re-did the steps to ad the repo for jaunty, ran an apt-get update and this is what happened.
```

Get:4 http://packages.medibuntu.org jaunty/non-free Packages [7943B]
Fetched 23.1kB in 1s (15.5kB/s)
Reading package lists... Done
W: GPG error: http://packages.medibuntu.org jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783

```

It tells me "You may want to run apt-get update to fix this". What good is running apt-get update going to do if I received this error from the command its telling me to run?

---

### Post by jenkinbr on 2009-06-22
It is only a warning.

run the command I posted erlier to solve that.

---

### Post by Narcoleptic_Insomniac on 2009-06-22
> **jenkinbr said:**
> You're fine - just run sudo apt-get install mediubuntu-keyring

Ok, I am doing this now. Sorry my posts are not very orderly, I'm trying my best to follow your guys instructions. I really appreciate the help.

---

### Post by jenkinbr on 2009-06-22
I spelled that wrong.

```
sudo apt-get install medibuntu-keyring
```

---

### Post by Narcoleptic_Insomniac on 2009-06-22
> **jenkinbr said:**
> It is only a warning.

run the command I posted erlier to solve that.

Ok I did that. I ran an update and everything went through fine, so I finally tryed sudo apt-get install winff and...

```

Hit http://packages.medibuntu.org jaunty/non-free Packages
Hit http://ca.archive.ubuntu.com intrepid-updates/multiverse Sources
Fetched 198B in 1s (148B/s)
Reading package lists... Done
anon@anonymous:~$ sudo apt-get install winff
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package winff

```
I noticed however that all my other repos are still intrepid and the only one that is jaunty is the medibuntu one which I just did, could that be the problem?

---

### Post by jenkinbr on 2009-06-22
yes.

```
sudo gedit /etc/apt/sources.list
```

Find and replace all instances of jaunty with intrepid.

save and try again.

---

### Post by Narcoleptic_Insomniac on 2009-06-22
> **jenkinbr said:**
> yes.

```
sudo gedit /etc/apt/sources.list
```

Find and replace all instances of jaunty with intrepid.

save and try again.

```

#deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/ intrepid main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://ca.archive.ubuntu.com/ubuntu/ intrepid main restricted
deb-src http://ca.archive.ubuntu.com/ubuntu/ intrepid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://ca.archive.ubuntu.com/ubuntu/ intrepid-updates main restricted
deb-src http://ca.archive.ubuntu.com/ubuntu/ intrepid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://ca.archive.ubuntu.com/ubuntu/ intrepid universe
deb-src http://ca.archive.ubuntu.com/ubuntu/ intrepid universe
deb http://ca.archive.ubuntu.com/ubuntu/ intrepid-updates universe
deb-src http://ca.archive.ubuntu.com/ubuntu/ intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://ca.archive.ubuntu.com/ubuntu/ intrepid multiverse
deb-src http://ca.archive.ubuntu.com/ubuntu/ intrepid multiverse
deb http://ca.archive.ubuntu.com/ubuntu/ intrepid-updates multiverse
deb-src http://ca.archive.ubuntu.com/ubuntu/ intrepid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://ca.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse
# deb-src http://ca.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse

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

```
This is my sources list. I don't see anything with jaunty, something tells me theres something real ****ed up about my sources list. Do you see anything wrong?

---

### Post by jenkinbr on 2009-06-22
That is strange.

actually, the file you need to edit is at /etc/apt/sources.list.d/medibuntu.list

---

### Post by Narcoleptic_Insomniac on 2009-06-22
> **jenkinbr said:**
> That is strange.

actually, the file you need to edit is at /etc/apt/sources.list.d/medibuntu.list

```

## Please report any bug on https://bugs.launchpad.net/medibuntu/
deb http://packages.medibuntu.org/ intrepid free non-free #Medibuntu - Ubuntu 8.10 "intrepid ibex"
#deb-src http://packages.medibuntu.org/ intrepid free non-free #Medibuntu (source) - Ubuntu 8.10 "intrepid ibex"

```
They are both already intrepid... Do I have to remove the # from the second one?

---

### Post by Narcoleptic_Insomniac on 2009-06-22
I followed this instructions found here on the winff website... it got me past the repo problem I think but now I'm running into this when I try to apt-get install...

```

anon@anonymous:~$ sudo apt-get install winff
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help resolve the situation:

The following packages have unmet dependencies:
  winff: Depends: libgtk2.0-0 (>= 2.16.0) but 2.14.4-0ubuntu1 is to be installed
E: Broken packages
anon@anonymous:~$ 

```

---

### Post by jenkinbr on 2009-06-22
Have you upgraded your packages recently?

Run sudo apt-get upgrade first to do an upgrade, then try installing winff.

---

### Post by jose158 on 2009-06-22
Have you tried this: 
[http://code.google.com/p/winff/wiki/UbuntuInstallation](http://code.google.com/p/winff/wiki/UbuntuInstallation)

---

### Post by Narcoleptic_Insomniac on 2009-06-22
I ran an upgrade the other day I'm almost positive, but I'll do it again. I'm also going to try that code.google thing.

---

### Post by Narcoleptic_Insomniac on 2009-06-22
I've actually been following those instructions at code.google.com along side your instructions. I'm running into errors with it aswell.

---

