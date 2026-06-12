---
title: "Failed to download repository information"
date: 2011-05-06
forum: New to Ubuntu
---

### Post by linuxsyst on 2011-05-06
Failed to download repository information

Check your Internet connection.

W:Failed to fetch [http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/dists/natty/main/source/Sources](http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/dists/natty/main/source/Sources)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/dists/natty/main/binary-i386/Packages](http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/dists/natty/main/binary-i386/Packages)  404  Not Found
, E:Some index files failed to download. They have been ignored, or old ones used instead.

Could you help me please.

---

### Post by matt_symes on 2011-05-06
Hi

Press ctrl + F2 keys at the same type. Type **gedit** into the run dialog.

This will open gedit. Navigate to and open the file

```
/etc/apt/sources.list
```

Copy and paste the results back into you next post. 

Wrap the output between code tags. This will make it more readable.

There are a couple of ways to do this. Highlight the text and hit the # button above where you are typing or before and after the output type code tags like this

[noparse] ```
 text from file 
``` [/noparse]

Kind regards

---

### Post by mikewhatever on 2011-05-06
You seem to have added the Mozilla-Stable ppa to your Natty installation. Why? Natty has the latest stable Firefox version in its repositories.

---

### Post by ivanovnegro on 2011-05-06
> **mikewhatever said:**
> You seem to have added the Mozilla-Stable ppa to your Natty installation. Why? Natty has the latest stable Firefox version in its repositories.

Yup, he has to remove them and that should solve the problem.

---

### Post by linuxsyst on 2011-05-06
# deb cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)]/ maverick main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://cz.archive.ubuntu.com/ubuntu/](http://cz.archive.ubuntu.com/ubuntu/) natty main restricted
deb-src [http://cz.archive.ubuntu.com/ubuntu/](http://cz.archive.ubuntu.com/ubuntu/) natty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://cz.archive.ubuntu.com/ubuntu/](http://cz.archive.ubuntu.com/ubuntu/) natty-updates main restricted
deb-src [http://cz.archive.ubuntu.com/ubuntu/](http://cz.archive.ubuntu.com/ubuntu/) natty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://cz.archive.ubuntu.com/ubuntu/](http://cz.archive.ubuntu.com/ubuntu/) natty universe
deb-src [http://cz.archive.ubuntu.com/ubuntu/](http://cz.archive.ubuntu.com/ubuntu/) natty universe
deb [http://cz.archive.ubuntu.com/ubuntu/](http://cz.archive.ubuntu.com/ubuntu/) natty-updates universe
deb-src [http://cz.archive.ubuntu.com/ubuntu/](http://cz.archive.ubuntu.com/ubuntu/) natty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://cz.archive.ubuntu.com/ubuntu/](http://cz.archive.ubuntu.com/ubuntu/) natty multiverse
deb-src [http://cz.archive.ubuntu.com/ubuntu/](http://cz.archive.ubuntu.com/ubuntu/) natty multiverse
deb [http://cz.archive.ubuntu.com/ubuntu/](http://cz.archive.ubuntu.com/ubuntu/) natty-updates multiverse
deb-src [http://cz.archive.ubuntu.com/ubuntu/](http://cz.archive.ubuntu.com/ubuntu/) natty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://cz.archive.ubuntu.com/ubuntu/](http://cz.archive.ubuntu.com/ubuntu/) maverick-backports main restricted universe multiverse
# deb-src [http://cz.archive.ubuntu.com/ubuntu/](http://cz.archive.ubuntu.com/ubuntu/) maverick-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) natty partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) natty main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) natty main

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security multiverse

It thinks that I have 10.10?

---

### Post by matt_symes on 2011-05-06
Hi

As the other posters have said have a look at this link

[http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/dists/](http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/dists/)

There is no natty distribution there. Follow my first post and i will help you remove them from your sources.list file.

Kind regards

---

### Post by matt_symes on 2011-05-06
Hi

You have upgraded this installation from 10.10 to 11.04. It does not think it's 10.10 as those lines are commented out. They have a # infront of them.

To prove this to yourself open a terminal and type

```
cat /etc/lsb-release
```

You will see 11.04

The offending lines are not in your source.list file. This means they will be in one of the sub files.

From a terminal, please post the output of (copy and paste)

```
ls /etc/apt/sources.list.d/
```

This will list all the Sub files and the we can remove the correct one for you.

Kind regards

---

### Post by linuxsyst on 2011-05-06
```
peter@comp:~$ ls /etc/apt/sources.list.d/
dropbox.list                    mozillateam-firefox-next-natty.list
dropbox.list.save               mozillateam-firefox-next-natty.list.save
google-chrome.list              mozillateam-firefox-stable-natty.list
google-chrome.list.distUpgrade  mozillateam-firefox-stable-natty.list.save
google-chrome.list.save
```

---

### Post by matt_symes on 2011-05-06
Hi

Open a terminal and copy and paste this into it.

```
sudo rm /etc/apt/sources.list.d/mozillateam-firefox*
```

Enter your password. It will not be echoed to the screen. This is normal. Then type

```
sudo apt-get update
```

After that use synaptic package manager to install firefox.

Kind regards

---

### Post by linuxsyst on 2011-05-06
Thank you very much!

---

