---
title: "Error message I don't understand"
date: 2009-07-01
forum: New to Ubuntu
---

### Post by hector24 on 2009-07-01
I have only had Ubuntu for a couple of weeks so still very new to it all.  I have an error message which reads:

"An error occurred, please run Package Manager from the right-click menu or apt-get in a terminal to see what is wrong.  The error message was: Error: Opening the cache (E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/
gb.archive.unbuntu.com_ubuntu_dists_juanty-updates_restricted_binary-i386_Packages, E:The package lists or stus file could not be parsed or opened.)'This usually means that your installed packages have unmet dependencies"

All this is way beyond me.  

Please can someone tell me what to do.

Many thanks.

---

### Post by Michael.Godawski on 2009-07-01
OK.

Let's go through the standard procedure here.
Open up the terminal (Applications > Accessories > Terminal)
and fire off these commands:
```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get install -f
sudo dpkg --configure -a
```

Any weird stuff (errors) showing up?

---

### Post by hector24 on 2009-07-03
I am really lacking confidence here.  I didn't get as far as putting in all your instructions.  I got loads of stuff back including: Reading package lists... Error! E: Encountered a section with no Package: header  E: Problem with MergeList /var/lib/apt/lists/packages.medibuntu.org_dists_jaunty_free_binary-i386_Packages E: The package lists or stus file could not be parsed or opened.

---

### Post by Michael.Godawski on 2009-07-03
What happens if you run:
```
sudo dpkg --configure -a
```

---

### Post by hector24 on 2009-07-03
Nothing happens at all.  It just comes back with my name @ my name.

---

### Post by Jackelope on 2009-07-03
First thing to check: are you on the Internet when trying this?

---

### Post by Michael.Godawski on 2009-07-03
Can you please post your sources list:

```
cat /etc/apt/sources.list
```

---

### Post by hector24 on 2009-07-03
Yes, I'm on broadband.
This is what came up:
#deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)]/ jaunty main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty-updates main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty universe
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty-updates universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty multiverse
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty-updates multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse
## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security multiverse

---

### Post by hector24 on 2009-07-18
Please help someone.  I'm still not able to download updates.  I clicked on update manager and got this message: 

E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/packages.medibuntu.org_dists_jaunty_free_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.

It says I should report this.  Can anyone tell me how to do this please?:confused:

---

### Post by RomeReactor on 2009-07-18
Hi. Maybe [this post]("http://ubuntuforums.org/showpost.php?p=5415838&postcount=4") can be of help.

---

### Post by hector24 on 2009-07-19
Yes, it did.  The last terminal entry worked.  Thanks:P

---

### Post by esunday on 2009-07-21
I just developed the exact same problem after adding KDE, and then removing it.  The post before mine solved it, thank you.  But what was the root cause?

---

### Post by hector24 on 2009-07-26
I've no idea what the cause was.  I've hardly used Ubuntu as it's new to me.  All I did was download updates using the update manager.

---

### Post by mc4100 on 2009-07-26
> **hector24 said:**
> I've no idea what the cause was.

Doesn't hurt to know:
When you check for updates, in fact you're basically just looking at a list of you're computer's installed software, and comparing that list with another one, which you have downloaded, to see how recent you are.

Unfortunately that list (or lists) can get messed up, for various reasons (bad download, etc.), and it can't be read (giving that error) ... so what you did to fix it was remove the faulty lists and get new ones.

---

