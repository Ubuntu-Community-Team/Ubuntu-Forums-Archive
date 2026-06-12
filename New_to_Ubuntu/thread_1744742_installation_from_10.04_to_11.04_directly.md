---
title: "installation from 10.04 to 11.04 directly"
date: 2011-04-30
forum: New to Ubuntu
---

### Post by tushar maroo on 2011-04-30
i have ubuntu 10.04 installed along with windows 7 dual boot in my laptop,i want to upgrade to 11.04 ,can i do it directly without going through 10.10 .if possible then suggest some methods to implement it???

---

### Post by KL_72_TR on 2011-04-30
p { margin-bottom: 0.08in; }  Hello
 I have dual boot: 10.04 and Windows XP.
 About two weeks ago I installed 11.04, twice. It is not a hard or special task to carry on. Just like any other Ubuntu installation or upgrade. Back-up your valuable data and go.
I don't think with laptops should be any difference.

---

### Post by tushar maroo on 2011-04-30
> **KL_72_TR said:**
> p { margin-bottom: 0.08in; }  Hello
 I have dual boot: 10.04 and Windows XP.
 About two weeks ago I installed 11.04, twice. It is not a hard or special task to carry on. Just like any other Ubuntu installation or upgrade. Back-up your valuable data and go.
I don't think with laptops should be any difference.
you directly upgraded through internet or some otherway.......and tell me the commands used if any???

---

### Post by Rubi1200 on 2011-04-30
> **tushar maroo said:**
> i have ubuntu 10.04 installed along with windows 7 dual boot in my laptop,i want to upgrade to 11.04 ,can i do it directly without going through 10.10 .if possible then suggest some methods to implement it???
The answer is no.

You can do one of 2 things:

1. upgrade to 10.10 and then to 11.04

2. backup all important data and do a fresh install of 11.04

Some things to read before you start:
[https://help.ubuntu.com/community/UpgradeNotes](https://help.ubuntu.com/community/UpgradeNotes)
[https://wiki.ubuntu.com/NattyNarwhal/ReleaseNotes](https://wiki.ubuntu.com/NattyNarwhal/ReleaseNotes)
[https://wiki.ubuntu.com/DemystifyingUnityGraphicsHardwareRequirements](https://wiki.ubuntu.com/DemystifyingUnityGraphicsHardwareRequirements)

---

### Post by yetiman64 on 2011-04-30
> **tushar maroo said:**
> i have ubuntu 10.04 installed along with windows 7 dual boot in my laptop,i want to upgrade to 11.04 ,can i do it directly without going through 10.10 .if possible then suggest some methods to implement it???

To use the update manager to upgrade your system you need to do the step to 10.10 then on to 11.04 from there. You can only skip versions when going from one LTS (Long term support) version to another LTS version.

If you don't want to do the two steps a fresh install will be needed.

Edit: beaten to it by Rubi1200 :-)

---

### Post by kansasnoob on 2011-04-30
> **Rubi1200 said:**
> The answer is no.

You can do one of 2 things:

1. upgrade to 10.10 and then to 11.04

2. backup all important data and do a fresh install of 11.04

Some things to read before you start:
[https://help.ubuntu.com/community/UpgradeNotes](https://help.ubuntu.com/community/UpgradeNotes)
[https://wiki.ubuntu.com/NattyNarwhal/ReleaseNotes](https://wiki.ubuntu.com/NattyNarwhal/ReleaseNotes)
[https://wiki.ubuntu.com/DemystifyingUnityGraphicsHardwareRequirements](https://wiki.ubuntu.com/DemystifyingUnityGraphicsHardwareRequirements)

That's no longer accurate :)

You can now upgrade and/or replace an existing Ubuntu OS. I hate the ad's here but:

[http://www.techdrivein.com/2011/04/how-to-upgrade-to-ubuntu-1104-natty.html](http://www.techdrivein.com/2011/04/how-to-upgrade-to-ubuntu-1104-natty.html)

I've tried it four times upgrading to Natty from Hardy, Karmic, Lucid, and Maverick and they all worked out fine.

**But**, anyone that performs any install/upgrade/re-partitioning without a backup is just looking for trouble!

The data you don't back up is the data you'll lose!

---

### Post by Rubi1200 on 2011-04-30
The page you linked to says it is for an upgrade from **10.10** to 11.04.

The OP stated, however, that they have[COLOR=Red] 10.04[/COLOR]. 

Does the same method still apply?

---

### Post by kansasnoob on 2011-05-01
I'm trying to cook up something ASAP to better explain this as well as I can, here's the only official documentation regarding upgrade/replace using Live CD/USB that I'm aware of:

[https://lists.ubuntu.com/archives/ubuntu-devel-announce/2011-April/000841.html](https://lists.ubuntu.com/archives/ubuntu-devel-announce/2011-April/000841.html)

> In 11.04 and later versions, the desktop CD installer (ubiquity)
presents an option to upgrade Ubuntu if it finds a single copy on the
system.  This functionality is not exactly equal in operation to
upgrade-manager, nor does it share much code with that application.

Such an upgrade will first make a backup of apt's state, including
repacked debs (using dpkg-repack) for any packages that it cannot find
a source for.  Following this, it will delete all non-user and
non-local files on the existing partitions.  This is roughly
everything but /usr/local, /var/local, /usr/src, and /home. It will
then install Ubuntu over top of the partially-cleared directory
structure and install the packages referenced in the apt state backup.

When triaging upgrade bugs, please make sure they're targeted to and
have logs for the correct package.  If the user upgrades via the
option in the desktop CD installer, change the package to ubiquity and
have the user run `sudo apport-collect $bug_number`.

Thanks,
Evan


If you're a real glutton for punishment you can read the full spec here:

[https://docs.google.com/View?id=dfkkjjcj_101gnkrpg5v#4_5_1_Automatic_partitioning_o_8475526086986065](https://docs.google.com/View?id=dfkkjjcj_101gnkrpg5v#4_5_1_Automatic_partitioning_o_8475526086986065)

---

### Post by Rubi1200 on 2011-05-01
Thanks for the update. I hope this is not going to cause new users more confusion than necessary.

In any event, as you mentioned in your private message, the most important thing is to always backup anything important before updating/upgrading/installing etc.

---

### Post by kansasnoob on 2011-05-01
OK, I'm in the process of completing just such an upgrade via ubiquity, hardly flawless ATM. Sort of bummed out because I know I did the same thing during Natty Beta and it worked better :(

Anyway I began with a fresh Lucid to which I added the Medibuntu repo and then all of this:

```
sudo apt-get install abiword gparted gphoto2 gthumb gtkam gufw hplip-gui mozilla-plugin-vlc vlc-plugin-pulse startupmanager totem-mozilla totem-plugins-extra totem-xine ubuntu-restricted-extras gnome-themes-more gnome-themes-extras shiki-colors-metacity-theme gnome-backgrounds nautilus-gksu sensors-applet desktop-base libdvdcss2 w32codecs zsync

```

Those are my typical packages. I then also added Opera browser which by default installs it's own repo.

**Neither the Opera or Medibuntu repos survive this type of upgrade!**

But, I uploaded a load of files to my home folder before starting and it all survived! So that's a huge plus :D

Perhaps one of the most negative things is that I ended up with some duplicate entries in my sources.list:

```
# deb cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1)]/ natty main restricted
# deb cdrom:[Ubuntu 10.04.2 LTS _Lucid Lynx_ - Release i386 (20110211.1)]/ lucid main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ natty main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ natty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ natty-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ natty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ natty universe
deb-src http://us.archive.ubuntu.com/ubuntu/ natty universe
deb http://us.archive.ubuntu.com/ubuntu/ natty-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ natty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ natty multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ natty multiverse
deb http://us.archive.ubuntu.com/ubuntu/ natty-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ natty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
[B][COLOR="Red"]deb http://archive.canonical.com/ubuntu natty partner
deb-src http://archive.canonical.com/ubuntu natty partner[/COLOR][/B]

deb http://security.ubuntu.com/ubuntu natty-security main restricted
deb-src http://security.ubuntu.com/ubuntu natty-security main restricted
deb http://security.ubuntu.com/ubuntu natty-security universe
deb-src http://security.ubuntu.com/ubuntu natty-security universe
deb http://security.ubuntu.com/ubuntu natty-security multiverse
deb-src http://security.ubuntu.com/ubuntu natty-security multiverse

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
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
# deb http://us.archive.ubuntu.com/ubuntu/ natty-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ natty-backports main restricted universe multiverse


## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
[B][COLOR="Red"]# deb http://archive.canonical.com/ubuntu natty partner
# deb-src http://archive.canonical.com/ubuntu natty partner[/COLOR][/B]

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu natty main
deb-src http://extras.ubuntu.com/ubuntu natty main
```

Since one set of those partner repos is commented out it's not a huge deal, but for a noob that only looks at software sources in the GUI and activates the dupes it would be a problem. I need to report that bug.

Anyway look here to see what my DE normally looks like:

[http://ubuntuforums.org/showpost.php?p=10748512&postcount=49](http://ubuntuforums.org/showpost.php?p=10748512&postcount=49)

After this upgrade (and errors) it looks like crap:

[ATTACH]190676[/ATTACH]

Anyway at the very end of the upgrade I got this error:

[ATTACH]190677[/ATTACH]

This is generally what the upgrade offer looks like:

[ATTACH]190679[/ATTACH]

You'll notice in the shot on the left that the Forward button changed to Install now :D

Time for a reboot since I'm trying to see just what it takes to recover. I've already DLed the Medibuntu repo again, reinstalled all packages, and then reinstalled Opera.

---

### Post by kansasnoob on 2011-05-01
Software center also kind of sucks. It complains about installing Opera so I install gdebi :)

---

### Post by kansasnoob on 2011-05-01
Back to normal now but I can assure you that "apt state backup & restore" DOES NOT work :(

It did a couple of weeks ago so I need to look for what broke it, not that it matters ATM because they absolutely will not create a new iso :mad:

So, this option is basically broken. It does save data in /home, but the apt backup does not work.

Although with that tz-data error preceding the apt-clone error I'm thinking I had selected to DL updates so I wonder what would happen if I didn't do so :confused:

In other words, did the update DL during install trigger the tzdata error?

This really does tick me off because it was working OK a couple of weeks ago :mad:

Anyway, the apt-clone part no longer works, if I could cuss here I'd use a word that starts with F!

---

### Post by beew on 2011-05-01
Just do a fresh install, why go through all these troubles,it is not even a good learning experience for anything useful.

But then there is a third option, wait and see a few weeks before you do anything so you don't end up with a broken desktop or something you hate,  you don't need to do an OS update/upgrade.

---

### Post by Rubi1200 on 2011-05-01
To be honest, until this has been tested more thoroughly I do not feel at all comfortable recommending this as a **safe** upgrade option.

---

### Post by kansasnoob on 2011-05-01
For those who might think I take things lightly look here:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/775009](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/775009)

When I find something wrong I try to get it fixed!

---

### Post by Rubi1200 on 2011-05-01
> **kansasnoob said:**
> For those who might think I take things lightly look here:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/775009](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/775009)

When I find something wrong I try to get it fixed!
No one here doubts your sincerity or attitude towards getting things fixed.

We all value and appreciate the very hard work you do trying to make Ubuntu a safe and stable computing experience.

Kudos :)

---

### Post by tushar maroo on 2011-05-03
hey guys thanks to all of you for all replies,
i just made dpkg-repack of all my installed packages and did a fresh install of ubuntu 11.04 natty........i recommend all the future viewers to do the same.......:D

---

