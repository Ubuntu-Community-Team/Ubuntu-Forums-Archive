---
title: "[SOLVED] Update problem"
date: 2008-12-06
forum: New to Ubuntu
---

### Post by hellomoto on 2008-12-06
Heya, im able to update but when ever I do I always I get an issue with one of the sources not downloading properly. 

```

W: GPG error: http://packages.medibuntu.org hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
W: GPG error: http://security.ubuntu.com hardy-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: http://archive.ubuntu.com hardy-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: Failed to fetch http://repository.salutis.sk/production/./Packages.gz  404 Not Found

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hardy-updates/Release  

W: Some index files failed to download, they have been ignored, or old ones used instead.

```

Does anyone know how I can stop this from happening as its really annoying!

---

### Post by drs305 on 2008-12-06
Go to the Medibuntu site and run the commands for your installation. The commands will install the medibuntu repository listing and add the key. The commands vary depending on which version of ubuntu you are using.
[https://help.ubuntu.com/community/Medibuntu]("https://help.ubuntu.com/community/Medibuntu")

For Hardy, running these two commands should fix things:
```

sudo wget http://www.medibuntu.org/sources.list.d/hardy.list --output-document=/etc/apt/sources.list.d/medibuntu.list
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update

```

Please mark the thread Solved if this resolves the issue.

---

### Post by hellomoto on 2008-12-06
i ran the above to commands and this is the terminal output:

```

]--16:22:29--  http://www.medibuntu.org/sources.list.d/hardy.list
           => `/etc/apt/sources.list.d/medibuntu.list'
Resolving www.medibuntu.org... 87.98.242.110
Connecting to www.medibuntu.org|87.98.242.110|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 226 [text/plain]

100%[====================================>] 226           --.--K/s             

16:22:32 (5.53 MB/s) - `/etc/apt/sources.list.d/medibuntu.list' saved [226/226]

```

Hoever when I run sudo apt-get update i still get:

```

W: GPG error: http://security.ubuntu.com hardy-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: http://packages.medibuntu.org hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: http://archive.ubuntu.com hardy-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: Failed to fetch http://repository.salutis.sk/production/./Packages.gz  404 Not Found

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hardy-updates/Release  

W: Some index files failed to download, they have been ignored, or old ones used instead.
W: You may want to run apt-get update to correct these problems

```

---

### Post by drs305 on 2008-12-06
If you manually added the medibuntu repository earlier, it is possible you still have an entry within sources.list. Medibuntu now attaches it's list externally in /etc/apt/sources.list.d

The reference to [http://repository.salutis.sk/production](http://repository.salutis.sk/production) is bad. The address has been removed, is temporarily out, or has been changed. It should be commented out or removed from your sources.list

If you post your sources.list we can take a look at it:
```
cat /etc/apt/sources.list
```

I didn't see any obvious error in the archive listing, but we can look at that one as well. You might try unticking it in Synaptic or Software Sources, Settings, Repositories, Updates, hitting Reload and then adding it back and hitting Reload again.

---

### Post by hellomoto on 2008-12-06
hey thanxs for your help so far.

here is my sources list:

```

mark@ubuntu:~$ cat /etc/apt/sources.list
#
# deb cdrom:[Xubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1)]/ hardy main restricted
# deb cdrom:[Xubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080701)]/ hardy main multiverse restricted universe

# deb cdrom:[Xubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080701)]/ hardy main multiverse restricted universe
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.


## Major bug fix updates produced after the final release of the
## distribution.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://gb.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
# deb-src http://gb.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu hardy partner
# deb-src http://archive.canonical.com/ubuntu hardy partner

# Line commented out by installer because it failed to verify:
# deb http://security.ubuntu.com/ubuntu hardy-security main restricted
# Line commented out by installer because it failed to verify:
# deb-src http://security.ubuntu.com/ubuntu hardy-security main restricted
# Line commented out by installer because it failed to verify:
# deb http://security.ubuntu.com/ubuntu hardy-security universe
# Line commented out by installer because it failed to verify:
# deb-src http://security.ubuntu.com/ubuntu hardy-security universe
# Line commented out by installer because it failed to verify:
# deb http://security.ubuntu.com/ubuntu hardy-security multiverse
# Line commented out by installer because it failed to verify:
# deb-src http://security.ubuntu.com/ubuntu hardy-security multiverse
deb http://archive.ubuntu.com/ubuntu/ hardy main universe restricted multiverse
deb http://security.ubuntu.com/ubuntu/ hardy-security universe main multiverse restricted
deb http://archive.ubuntu.com/ubuntu/ hardy-updates universe main multiverse restricted

deb http://repository.salutis.sk/production ./

```

---

### Post by mc4man on 2008-12-06
Your problem with medibuntu isn't that important, you are fetching the packages, they're just not being authenticated. (in other words you can install from medibuntu, you'll be prompted at some point to install without authentication.

What may fix that is to search medibuntu-keyring in synaptic and mark for re installation.

A bigger issue is the failed to fetch on the ubuntu sources.

3 things to try
```
sudo apt-get clean && sudo apt-get update && sudo apt-get upgrade
```

You could try going into System -> Admin.. -> software sources and in the 'download from' box pick some 'other' mirror.

If that doesn't work,wait awhile and try again to update or try this in the terminal
```

sudo apt-get update -o Acquire::http::No-Cache=True
```

---

### Post by drs305 on 2008-12-06
1. Comment the 'salutis' reference.
```
gksudo gedit /etc/apt/sources.list
```
Add a comment symbol:
```

[COLOR="Red"]# [/COLOR]deb http://repository.salutis.sk/production ./

```
Save the file and close it.

2. Next try changing your server: Synaptic or Software Sources, Settings, Repositories, Download From, and select another server. Reload. Then run 'sudo apt-get update' (which does essentially the same thing as 'Reload' but in terminal) and see if you get any errors.

---

### Post by zvacet on 2008-12-06
For Medibuntu you can type this in terminal

```
gpg --keyserver hkp://subkeys.pgp.net --recv-keys 2EBC26B60C5A2783
gpg --export --armor 2EBC26B60C5A2783 | sudo apt-key add -
```

---

### Post by hellomoto on 2009-01-07
ok i have done everything above and got it down to just the following error:

```


W: GPG error: http://archive.ubuntu.com hardy-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>


```

any ideas?

---

### Post by hellomoto on 2009-01-07
sorted: Changed the site to a better mirror by getting synaptic to search for the best one. 

Thank you everyone for your help!

---

### Post by chemtamer on 2009-07-04
> **drs305 said:**
> Go to the Medibuntu site and run the commands for your installation. The commands will install the medibuntu repository listing and add the key. The commands vary depending on which version of ubuntu you are using.
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

For Hardy, running these two commands should fix things:
```

sudo wget http://www.medibuntu.org/sources.list.d/hardy.list --output-document=/etc/apt/sources.list.d/medibuntu.list
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update

```Please mark the thread Solved if this resolves the issue.
et:4 [http://dl.google.com](http://dl.google.com) stable Release [1308B]                              
Get:5 [http://dl.google.com](http://dl.google.com) stable/main Packages [613B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/multiverse Packages
Fetched 2488B in 1s (1530B/s)
Reading package lists... Done
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/jaunty-security/Release](http://security.ubuntu.com/ubuntu/dists/jaunty-security/Release)  

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/jaunty-updates/Release](http://archive.ubuntu.com/ubuntu/dists/jaunty-updates/Release)  

W: Some index files failed to download, they have been ignored, or old ones used instead.
W: You may want to run apt-get update to correct these problems
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by drs305 on 2009-07-04
chemtamer, welcome to Ubuntu and the Ubuntu forums.

The reason you received the error messages is that you ran an outdated command. You are now using jaunty and the command was written back then for hardy. 

You have two options. You can run the same command again, but substitute *jaunty* for *hardy*, or use the new command. There is now a Medibuntu *release-independent* set of commands so inputing your release version is no longer necessary to get the proper results:

```

sudo wget http://www.medibuntu.org/sources.list.d/`lsb_release -cs`.list --output-document=/etc/apt/sources.list.d/medibuntu.list; sudo apt-get -q update; sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring; sudo apt-get -q update

```

For key *omissions*, you can run the following. Change the number code to whatever the error code is:
```

sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 40976EAF437D05B5

```

---

### Post by abandonedthe_mulletator on 2009-07-30
Hi,

I have a similar problem on Jaunty.  When I run sudp apt-get update I get this:
```
Hit http://ca.archive.ubuntu.com jaunty-updates/restricted Packages
Hit http://ca.archive.ubuntu.com jaunty-updates/multiverse Packages
Hit http://ca.archive.ubuntu.com jaunty-updates/main Sources
Hit http://ca.archive.ubuntu.com jaunty-updates/restricted Sources
Hit http://ca.archive.ubuntu.com jaunty-updates/universe Packages
Hit http://ca.archive.ubuntu.com jaunty-updates/universe Sources
W: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/jaunty-updates/Release  Unable to find expected entry  multiversesudo/binary-i386/Packages in Meta-index file (malformed Release file?)

E: Some index files failed to download, they have been ignored, or old ones used instead.

```

I've tried changing my software source and I ran this command:
```
sudo wget http://www.medibuntu.org/sources.list.d/jaunty.list --output-document=/etc/apt/sources.list.d/medibuntu.list

```

My internet runs fine with a direct connection.

Here is my sources.list:
```
# deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/ intrepid main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://ca.archive.ubuntu.com/ubuntu/ jaunty main restricted multiverse
deb-src http://ca.archive.ubuntu.com/ubuntu/ jaunty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://ca.archive.ubuntu.com/ubuntu/ jaunty-updates main restricted multiverse
deb-src http://ca.archive.ubuntu.com/ubuntu/ jaunty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://ca.archive.ubuntu.com/ubuntu/ jaunty universe
deb-src http://ca.archive.ubuntu.com/ubuntu/ jaunty universe
deb http://ca.archive.ubuntu.com/ubuntu/ jaunty-updates universe
deb-src http://ca.archive.ubuntu.com/ubuntu/ jaunty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://ca.archive.ubuntu.com/ubuntu/ jaunty-updates multiversesudo gedit /etc/apt/sources.list

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
deb http://archive.canonical.com/ubuntu jaunty partner
deb-src http://archive.canonical.com/ubuntu jaunty partner

deb http://security.ubuntu.com/ubuntu/ jaunty-security restricted main multiverse universe

```

What do I need to do?

---

### Post by drs305 on 2009-07-31
> **the_mulletator said:**
> 
> deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) jaunty-updates [COLOR="DarkRed"]**multiversesudo**[/COLOR] gedit /etc/apt/sources.list


What do I need to do?

the_mulletator,

Open sources.list for editing:
```
gksudo gedit /etc/apt/sources.list
```

Find this line quoted above (about 2/3 of the way down the contents), and change it to:
> deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) jaunty-updates [COLOR="DarkRed"]**multiverse**[/COLOR] 


Save the file, then run "sudo apt-get update".

---

### Post by abandonedthe_mulletator on 2009-07-31
Thanks,
It seems good.  There were no updates though.

---

