---
title: "Gcc problem"
date: 2010-07-04
forum: New to Ubuntu
---

### Post by vedi on 2010-07-04
I have computer installed ubuntu 10.04 installed.
It is not compiling c code.
gcc is installed.
After this problem I have installed so many libraries(although i don't know what they are for)
but it didn't work.
Plz help me
Thnx in Advance

---

### Post by lisati on 2010-07-04
Have you installed build-essential?
```
sudo apt-get install build-essential
```

---

### Post by partloer on 2010-07-04
Hi vedi,

If gcc is not compiling code but installed what type of error is it giving?

---

### Post by vedi on 2010-07-04
After I tried to install build-essential it gives following error

ved@ved-laptop:~$ sudo apt-get install build-essential
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
ved@ved-laptop:~$ sudo apt-get install build-essential
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  build-essential: Depends: libc6-dev but it is not going to be installed or
                            libc-dev
                   Depends: g++ (>= 4:4.3.1) but it is not going to be installed
E: Broken packages

---

### Post by vedi on 2010-07-04
Hi partloer
gcc givees following error when o tries to compile c code

/usr/bin/ld: cannot find -lc
collect2: ld returned 1 exit status

---

### Post by ibuclaw on 2010-07-04
What is the output of:
```
cat /etc/apt/sources.list
```
and
```
ls /etc/apt/sources.list.d/
```

Regards

---

### Post by vedi on 2010-07-04
"ls /etc/apt/sources.list.d/" dosn't give any output
and
After cat /etc/apt/sources.lst THis output comes



ved@ved-laptop:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)]/ lucid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.


## Major bug fix updates produced after the final release of the
## distribution.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.

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
# deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse
# deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner

# deb file:///home/ved/Desktop/a /
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid main universe restricted multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid universe main multiverse restricted #Added by software-properties
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security universe main multiverse restricted
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security universe main multiverse restricted
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid-updates universe main multiverse restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid-updates universe main multiverse restricted
# deb-src file:///home/ved/Desktop/a /

---

### Post by ibuclaw on 2010-07-04
And what did you try to install when you setup
> **vedi said:**
> 
# deb file:///home/ved/Desktop/a /
# deb-src file:///home/ved/Desktop/a /


?

---

### Post by vedi on 2010-07-04
I formatted ubuntu.
So i saved all previous packages and made aptoncd out of it before formatting previous ubuntu
Then I used it for upgrading and installing some packages.

And i generally mount all iso in this folder.

---

### Post by ibuclaw on 2010-07-04
OK... you could try - very important that you copy and paste this:
```

cat << EOF | sudo tee /etc/apt/preferences
Package: *
Pin: release a=lucid-updates
Pin-Priority: 1001

Package: *
Pin: release a=lucid-security
Pin-Priority: 1001

Package: *
Pin release a=lucid
Pin Priority: 1001
EOF


```
Then
```
sudo apt-get update && sudo apt-get install -f
```
Then
```
sudo apt-get install build-essential
```
Then
```
sudo unlink /etc/apt/preferences
```

And let us know how it goes.

If any part ends in errors, stop what you are doing, and report it immediately. :)

---

### Post by vedi on 2010-07-04
I have very slow connection it may take 40 to 50 minutes.
As soon as it happens i will let u know.

---

### Post by vedi on 2010-07-04
After "sudo apt-get install build-essential" all packages installed but some  didn't install and following error came-

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  build-essential: Depends: libc6-dev but it is not going to be installed or
                            libc-dev
                   Depends: g++ (>= 4:4.3.1) but it is not going to be installed
E: Broken packages

---

### Post by ibuclaw on 2010-07-04
Interesting ... when was the last time you upgraded then?

If you were to run:
```
sudo apt-get upgrade
```
How many updates does it show?

---

