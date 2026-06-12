---
title: "Major failure of my software managemant system."
date: 2010-09-25
forum: New to Ubuntu
---

### Post by gnermal on 2010-09-25
Yikes--

Was trying to install skype and iceccam2 on 8.04 and something went terribly wrong. I cannot get into Add/Remove or Update Manager and have experienced several terminal problems. 

Here is the error i get for Add/Remove:

This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'.

And this is the error for Update Manager:

Could not initialize the package information

A unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Type 'sudo' is not known on line 51 in source list /etc/apt/sources.list, E:The list of sources could not be read.'



I figure these and the probs with the terminal are related but don't know how to fix them being very new to ubuntu--help plz!!

---

### Post by 666f6f on 2010-09-25
Have you tried running ```
sudo apt-get update' and 'sudo apt-get install -f
```?

If not, [boot into recovery mode]("https://wiki.ubuntu.com/RecoveryMode") and run the above command. It's what the error message suggests.

---

### Post by tgalati4 on 2010-09-25
Or

sudo apt-get clean

---

### Post by 666f6f on 2010-09-25
> **tgalati4 said:**
> Or

sudo apt-get clean

From man apt-get.. *apt-get clean clears out the local repository of retrieved package files. It removes everything but the lock file from /var/cache/apt/archives/ and /var/cache/apt/archives/partial/.*

There's no point in running apt-get clean except for freeing some disk space.

---

### Post by marshmallow1304 on 2010-09-25
> **gnermal said:**
> 'E:Type 'sudo' is not known on line 51 in source list /etc/apt/sources.list, E:The list of sources could not be read.'

This means that there's something wrong on line 51 of /etc/apt/sources.list.  Run
```
cat /etc/apt/sources.list
```
and post the output.

---

### Post by gnermal on 2010-09-25
thanks--

ok, here's the output from cat /etc/apt/sources.list:

# deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hardy main restricted
# deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hardy-updates main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hardy main restricted multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hardy-updates main restricted multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hardy universe
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hardy universe
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hardy-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hardy-updates universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hardy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://apt.freegeek.org/](http://apt.freegeek.org/) freegeek public ubuntu

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse

sudo apt-key adv --keyserver pgp.mit.edu --recv-keys 0xd66b746e
cd
cd Desktop

---

### Post by Soul-Sing on 2010-09-26
where did d> eb [http://apt.freegeek.org/](http://apt.freegeek.org/) freegeek public ubuntu come from? and where is it good for?

is this: > sudo apt-key adv --keyserver pgp.mit.edu --recv-keys 0xd66b746e
cd
cd Desktop on your sourceslist? please remove it.

---

### Post by 3rdalbum on 2010-09-26
After you've removed these lines from your /etc/apt/sources.list:

sudo apt-key adv --keyserver pgp.mit.edu --recv-keys 0xd66b746e
cd
cd Desktop

then DON'T directly modify the sources.list file again! Instead, if you want to add or disable repositories on your system, use the System > Administration > Software Sources program. It prevents mistakes like this from happening.

---

### Post by gnermal on 2010-09-26
ok--cool. I can't seem to remove it, tho. Forgiving my ignorance, can somebody walk me through the removal? I have tried but keep getting "no such file or directory" messages.

thanks

---

### Post by philinux on 2010-09-26
> **gnermal said:**
> ok--cool. I can't seem to remove it, tho. Forgiving my ignorance, can somebody walk me through the removal? I have tried but keep getting "no such file or directory" messages.

thanks

```
gksudo gedit /etc/apt/sources.list
```

and be careful. Use copy and paste to make sure you put the command in right.

---

### Post by gnermal on 2010-09-26
great--yeah, not copy/pasting is what got me into this mess, so lesson learned. I deleted the lines and everythang is cool.

thanks again to all

---

