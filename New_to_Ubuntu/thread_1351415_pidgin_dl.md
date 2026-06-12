---
title: "pidgin d/l"
date: 2009-12-10
forum: New to Ubuntu
---

### Post by nal13 on 2009-12-10
I recently upgraded from 9.04 to 9.10. I tried Empathy for my IMing need, but really don't like it as much as pidgin. I went to d/l pidgin from synaptic, that didn't work, also from Ubuntu Software Center and got this prompt after it failed to d/l:

> This error could be caused by required additional software packages which are missing or not installable. Futhermore there could be a conflict between software packages which are not allowed to be installed at the same time.

So am I missing some repositories?

---

### Post by t0p on 2009-12-10
> **nal13 said:**
> 
So am I missing some repositories?

I don't *think* so.  Pidgin is (supposed to be) available through the main repository.

But there's a PPA (repository) for the latest pidgin [here]("http://www.pidgin.im/download/ubuntu/").

---

### Post by Locke_99GS on 2009-12-10
```

sudo apt-get update && sudo apt-get install -f
sudo aptitude install pidgin

```

---

### Post by nal13 on 2009-12-10
Neither of those worked.

---

### Post by nal13 on 2009-12-14
bump.

I also had the same problem while trying to d/l Transmission. :(

---

### Post by synapsys on 2009-12-14
Try:

```
sudo dpkg --configure -a
```

See if that produces any error messages.

Also could you post the contents of /etc/apt/sources.list ?

---

### Post by AlphaWhelp on 2009-12-14
if you go to pidgin's website, there are two commands you should run first, then download the libpurple libraries through your update manager, then the sudo apt-get install pidgin work.

```
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com \     67265eb522bdd6b1c69e66ed7fb8bee0a1f196a8

echo deb [http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu](http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu) \     `lsb_release --short --codename` main | \
    sudo tee /etc/apt/sources.list.d/pidgin-ppa.list
```

Then go to update manager, download the libraries, then go back to terminal and type

```
sudo apt-get install pidgin
```

Here is the website for reference.  [http://www.pidgin.im/download/ubuntu/](http://www.pidgin.im/download/ubuntu/)

---

### Post by nal13 on 2009-12-14
> **synapsys said:**
> Try:

```
sudo dpkg --configure -a
```

 
Nothing appears

> **synapsys said:**
> Try:

Also could you post the contents of /etc/apt/sources.list ?

What do I put before that command line?

---

### Post by nal13 on 2009-12-14
> **AlphaWhelp said:**
> if you go to pidgin's website, there are two commands you should run first, then download the libpurple libraries through your update manager, then the sudo apt-get install pidgin work.

```
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com \     67265eb522bdd6b1c69e66ed7fb8bee0a1f196a8

echo deb [http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu](http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu) \     `lsb_release --short --codename` main | \
    sudo tee /etc/apt/sources.list.d/pidgin-ppa.list
```

Then go to update manager, download the libraries, then go back to terminal and type

```
sudo apt-get install pidgin
```

Here is the website for reference.  [http://www.pidgin.im/download/ubuntu/](http://www.pidgin.im/download/ubuntu/)

I tried that before, but tried again and still didn't work. This comes up:

```
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --recv-keys --keyserver keyserver.ubuntu.com   67265eb522bdd6b1c69e66ed7fb8bee0a1f196a8
gpg: requesting key A1F196A8 from hkp server keyserver.ubuntu.com
gpg: key A1F196A8: "Launchpad PPA for Pidgin Developers" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1
nick@nick-netbook:~$ sudo apt-get install pidgin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  pidgin: Depends: pidgin-data (< 1:2.6.2-z) but 1:2.6.4-1~getdeb1 is to be installed
E: Broken packages

```

---

### Post by synapsys on 2009-12-14
```
sudo apt-get build-dep pidgin
```then try installing

> **nal13 said:**
> Nothing appears



What do I put before that command line?

```
cat /etc/apt/sources.list
```

or System >> Administration >> Software Sources

---

### Post by nal13 on 2009-12-14
> **synapsys said:**
> 

```
cat /etc/apt/sources.list
```

or System >> Administration >> Software Sources

```

# deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)]/ jaunty main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ karmic main restricted multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ karmic-updates main restricted multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ karmic universe
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic universe
deb http://us.archive.ubuntu.com/ubuntu/ karmic-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic-updates universe

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
# deb http://us.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu jaunty partner
deb-src http://archive.canonical.com/ubuntu jaunty partner

deb http://security.ubuntu.com/ubuntu karmic-security main restricted multiverse
deb-src http://security.ubuntu.com/ubuntu karmic-security main restricted
deb http://security.ubuntu.com/ubuntu karmic-security universe
deb-src http://security.ubuntu.com/ubuntu karmic-security universe
# deb http://archive.getdeb.net/ubuntu karmic-getdeb apps # disabled on upgrade to karmic
deb http://archive.canonical.com/ubuntu karmic partner

```

---

### Post by synapsys on 2009-12-14
Pidgin is in the universe repository, which you have enabled. 

Have you installed the package pidgin-data yet?

---

### Post by nal13 on 2009-12-14
> **synapsys said:**
> Pidgin is in the universe repository, which you have enabled. 

Have you installed the package pidgin-data yet?


Ya, just did. That didn't help either. :(

---

### Post by nal13 on 2009-12-15
Should I maybe have updated repositories since I upgraded from 9.04 to 9.10?

---

### Post by synapsys on 2009-12-15
Maybe this is the problem:

> deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) **jaunty** partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) **jaunty** partner


---

