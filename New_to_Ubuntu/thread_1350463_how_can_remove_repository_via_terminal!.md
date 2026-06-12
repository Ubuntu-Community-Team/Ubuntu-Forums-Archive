---
title: "how can remove repository via terminal?!"
date: 2009-12-09
forum: New to Ubuntu
---

### Post by vanhelsing2009 on 2009-12-09
[SIZE="2"]i have added some repositories via terminal and have got this error
while i am updating my system :
[QUOTE][W: Failed to fetch [http://ppa.launchpad.net/PPA_gdb/ppa/ubuntu/dists/karmic/main/binary-i386/Packages.gz](http://ppa.launchpad.net/PPA_gdb/ppa/ubuntu/dists/karmic/main/binary-i386/Packages.gz)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/gdb/ppa/ubuntu/dists/karmic/main/binary-i386/Packages.gz](http://ppa.launchpad.net/gdb/ppa/ubuntu/dists/karmic/main/binary-i386/Packages.gz)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/yulia-novozhilova/ppa/ubuntu/dists/karmic/main/binary-i386/Packages.gz](http://ppa.launchpad.net/yulia-novozhilova/ppa/ubuntu/dists/karmic/main/binary-i386/Packages.gz)  404  Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.
/QUOTE]

for my surprise i did not find these repositories in the sources list
so how can i remove them via terminal?
thx [/SIZE]

---

### Post by adaucourt on 2009-12-09
> **vanhelsing2009 said:**
> [SIZE=2]i have added some repositories via terminal and have got this error
while i am updating my system :
[quote][W: Failed to fetch [http://ppa.launchpad.net/PPA_gdb/ppa/ubuntu/dists/karmic/main/binary-i386/Packages.gz](http://ppa.launchpad.net/PPA_gdb/ppa/ubuntu/dists/karmic/main/binary-i386/Packages.gz)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/gdb/ppa/ubuntu/dists/karmic/main/binary-i386/Packages.gz](http://ppa.launchpad.net/gdb/ppa/ubuntu/dists/karmic/main/binary-i386/Packages.gz)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/yulia-novozhilova/ppa/ubuntu/dists/karmic/main/binary-i386/Packages.gz](http://ppa.launchpad.net/yulia-novozhilova/ppa/ubuntu/dists/karmic/main/binary-i386/Packages.gz)  404  Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.
/QUOTE]

for my surprise i did not find these repositories in the sources list
so how can i remove them via terminal?
thx 

Read this:
[/SIZE][https://help.ubuntu.com/community/Repositories/CommandLine](https://help.ubuntu.com/community/Repositories/CommandLine)

---

### Post by vanhelsing2009 on 2009-12-09
i have already open my sources list but even that i can not remove them manually cuz these repositories dont exist in sources list at all!!
and yes i have added them by :
[QUOTE][sudo add-apt-repository ppa: repository_name/QUOTE]

---

### Post by snowpine on 2009-12-09
Check if there are any files in the /etc/apt/sources.list.d/ sub-folder.

---

### Post by vanhelsing2009 on 2009-12-09
no the sub folder is empty!

---

### Post by slakkie on 2009-12-09
Could you paste the output of the following commands here:

```

cat /etc/apt/sources.list
ls /etc/apt/sources.list.d/*.list
# If you the ls commands shows files, do the following
cat /etc/apt/sources.list.d/*.list

```

---

### Post by vanhelsing2009 on 2009-12-09
sry to take long time to reply
yes this is the output of the last code:

[QUOTE][sherif@sherif-desktop:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)]/ karmic main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://swtsrv.informatik.uni-mannheim.de/pub/linux/distributions/ubuntu/](http://swtsrv.informatik.uni-mannheim.de/pub/linux/distributions/ubuntu/) karmic main restricted
deb-src [http://swtsrv.informatik.uni-mannheim.de/pub/linux/distributions/ubuntu/](http://swtsrv.informatik.uni-mannheim.de/pub/linux/distributions/ubuntu/) karmic main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://swtsrv.informatik.uni-mannheim.de/pub/linux/distributions/ubuntu/](http://swtsrv.informatik.uni-mannheim.de/pub/linux/distributions/ubuntu/) karmic-updates main restricted
deb-src [http://swtsrv.informatik.uni-mannheim.de/pub/linux/distributions/ubuntu/](http://swtsrv.informatik.uni-mannheim.de/pub/linux/distributions/ubuntu/) karmic-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://swtsrv.informatik.uni-mannheim.de/pub/linux/distributions/ubuntu/](http://swtsrv.informatik.uni-mannheim.de/pub/linux/distributions/ubuntu/) karmic universe
deb-src [http://swtsrv.informatik.uni-mannheim.de/pub/linux/distributions/ubuntu/](http://swtsrv.informatik.uni-mannheim.de/pub/linux/distributions/ubuntu/) karmic universe
deb [http://swtsrv.informatik.uni-mannheim.de/pub/linux/distributions/ubuntu/](http://swtsrv.informatik.uni-mannheim.de/pub/linux/distributions/ubuntu/) karmic-updates universe
deb-src [http://swtsrv.informatik.uni-mannheim.de/pub/linux/distributions/ubuntu/](http://swtsrv.informatik.uni-mannheim.de/pub/linux/distributions/ubuntu/) karmic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://swtsrv.informatik.uni-mannheim.de/pub/linux/distributions/ubuntu/](http://swtsrv.informatik.uni-mannheim.de/pub/linux/distributions/ubuntu/) karmic multiverse
deb-src [http://swtsrv.informatik.uni-mannheim.de/pub/linux/distributions/ubuntu/](http://swtsrv.informatik.uni-mannheim.de/pub/linux/distributions/ubuntu/) karmic multiverse
deb [http://swtsrv.informatik.uni-mannheim.de/pub/linux/distributions/ubuntu/](http://swtsrv.informatik.uni-mannheim.de/pub/linux/distributions/ubuntu/) karmic-updates multiverse
deb-src [http://swtsrv.informatik.uni-mannheim.de/pub/linux/distributions/ubuntu/](http://swtsrv.informatik.uni-mannheim.de/pub/linux/distributions/ubuntu/) karmic-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://eg.archive.ubuntu.com/ubuntu/](http://eg.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse
# deb-src [http://eg.archive.ubuntu.com/ubuntu/](http://eg.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner

deb [http://swtsrv.informatik.uni-mannheim.de/pub/linux/distributions/ubuntu/](http://swtsrv.informatik.uni-mannheim.de/pub/linux/distributions/ubuntu/) karmic-security main restricted
deb-src [http://swtsrv.informatik.uni-mannheim.de/pub/linux/distributions/ubuntu/](http://swtsrv.informatik.uni-mannheim.de/pub/linux/distributions/ubuntu/) karmic-security main restricted
deb [http://swtsrv.informatik.uni-mannheim.de/pub/linux/distributions/ubuntu/](http://swtsrv.informatik.uni-mannheim.de/pub/linux/distributions/ubuntu/) karmic-security universe
deb-src [http://swtsrv.informatik.uni-mannheim.de/pub/linux/distributions/ubuntu/](http://swtsrv.informatik.uni-mannheim.de/pub/linux/distributions/ubuntu/) karmic-security universe
deb [http://swtsrv.informatik.uni-mannheim.de/pub/linux/distributions/ubuntu/](http://swtsrv.informatik.uni-mannheim.de/pub/linux/distributions/ubuntu/) karmic-security multiverse
deb [http://swtsrv.informatik.uni-mannheim.de/pub/linux/distributions/ubuntu/](http://swtsrv.informatik.uni-mannheim.de/pub/linux/distributions/ubuntu/) karmic-proposed restricted main multiverse universe
deb [http://swtsrv.informatik.uni-mannheim.de/pub/linux/distributions/ubuntu/](http://swtsrv.informatik.uni-mannheim.de/pub/linux/distributions/ubuntu/) karmic-backports restricted main multiverse universe
deb-src [http://swtsrv.informatik.uni-mannheim.de/pub/linux/distributions/ubuntu/](http://swtsrv.informatik.uni-mannheim.de/pub/linux/distributions/ubuntu/) karmic-security multiverse

deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) karmic free non-free #Medibuntu Repository By hello ubuntu
deb [http://ppa.launchpad.net/gnome-colors-packagers/ppa/ubuntu](http://ppa.launchpad.net/gnome-colors-packagers/ppa/ubuntu) karmic main #Gnome Colors Repository by hello ubuntu
deb [http://ppa.launchpad.net/tualatrix/ppa/ubuntu](http://ppa.launchpad.net/tualatrix/ppa/ubuntu) karmic main #Ubuntu Tweak Repository by hello ubuntu
deb [http://ppa.launchpad.net/blueman/ppa/ubuntu](http://ppa.launchpad.net/blueman/ppa/ubuntu) karmic main #Blueman Repository by hello ubuntu
deb [http://ppa.launchpad.net/shutter/ppa/ubuntu](http://ppa.launchpad.net/shutter/ppa/ubuntu) karmic main #shutter Repository by hello ubuntu
sherif@sherif-desktop:~$ ls /etc/apt/sources.list.d/*.list
/etc/apt/sources.list.d/gdb-ppa-karmic.list
/etc/apt/sources.list.d/opera.list
/etc/apt/sources.list.d/PPA_gdb-ppa-karmic.list
/etc/apt/sources.list.d/yulia-novozhilova-ppa-karmic.list
sherif@sherif-desktop:~$ # If you the ls commands shows files, do the following
sherif@sherif-desktop:~$ cat /etc/apt/sources.list.d/*.list
deb [http://ppa.launchpad.net/gdb/ppa/ubuntu](http://ppa.launchpad.net/gdb/ppa/ubuntu) karmic main
# This file makes sure that Opera Browser is kept up-to-date
# as part of regular system upgrades

deb [http://deb.opera.com/opera/](http://deb.opera.com/opera/) stable non-free

# The line above will make sure you get all final public releases.
# Uncomment the following line if you want to get alpha and beta
# releases, too.

# deb [http://deb.opera.com/opera-beta/](http://deb.opera.com/opera-beta/) stable non-free
deb [http://ppa.launchpad.net/PPA_gdb/ppa/ubuntu](http://ppa.launchpad.net/PPA_gdb/ppa/ubuntu) karmic main
deb [http://ppa.launchpad.net/yulia-novozhilova/ppa/ubuntu](http://ppa.launchpad.net/yulia-novozhilova/ppa/ubuntu) karmic main
sherif@sherif-desktop:~$ 
/QUOTE]

---

### Post by m-tarek on 2009-12-09
Try this:
```
sudo cp -p /etc/apt/sources.list /etc/apt/sources.list_backup
```Next:
```
gksudo gedit /etc/apt/sources.list
```remove everythings inside and paste this:
```
#deb cdrom:[Ubuntu 9.10 _Karmic_Koala - Release i386 (20081029.1)]/ karmic main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) karmic main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) karmic main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) karmic-updates main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) karmic-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) karmic universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) karmic universe
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) karmic-updates universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) karmic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) karmic multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) karmic multiverse
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) karmic-updates multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) karmic-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security multiverse

```save and quit, then: 
```
sudo apt-get update
```Now you can add repos again.

---

### Post by vanhelsing2009 on 2009-12-10
thx my dear brother tarek but that did not work too and same errors!
i think if i go to mars u will be there to give me help ;)

---

### Post by KIAaze on 2009-12-10
> **vanhelsing2009 said:**
> no the sub folder is empty!

It is clearly not empty since you got this:
```
sherif@sherif-desktop:~$ ls /etc/apt/sources.list.d/*.list
/etc/apt/sources.list.d/gdb-ppa-karmic.list
/etc/apt/sources.list.d/opera.list
/etc/apt/sources.list.d/PPA_gdb-ppa-karmic.list
/etc/apt/sources.list.d/yulia-novozhilova-ppa-karmic.list

```

Remove the following files to get rid of the error messages:
```
/etc/apt/sources.list.d/gdb-ppa-karmic.list
/etc/apt/sources.list.d/PPA_gdb-ppa-karmic.list
/etc/apt/sources.list.d/yulia-novozhilova-ppa-karmic.list

```

[B]Also, if you have no idea where they could come from, I would say it is likely that your machine has been compromised.
[/B]
I've never seen any instructions adding new sources in /etc/apt/sources.list.d/.
Usually people tell you to add sources in /etc/apt/sources.list (which can be done through System->Administration->Software sources).

edit:
Completely dead repositories (do you know where they came from?):
> deb [http://ppa.launchpad.net/gdb/ppa/ubuntu](http://ppa.launchpad.net/gdb/ppa/ubuntu) karmic main
deb [http://ppa.launchpad.net/PPA_gdb/ppa/ubuntu](http://ppa.launchpad.net/PPA_gdb/ppa/ubuntu) karmic main

Still valid repositories, but without support for karmic (seems legitimate):
> deb [http://ppa.launchpad.net/yulia-novozhilova/ppa/ubuntu](http://ppa.launchpad.net/yulia-novozhilova/ppa/ubuntu) karmic main

So you can replace "karmic" with "intrepid" in /etc/apt/sources.list.d/yulia-novozhilova-ppa-karmic.list and it should work.

---

### Post by slakkie on 2009-12-10
You don't have to remove the *.list files in /etc/apt/sources.list.d/, ust rename them to something which doesn't end with .list and then apt will not use them.

Adding sources in sources.list.d is done by the new thing to add ppa's. I never use it, but it has become the new and propper way to install PPA's, since it will also import the correct key.

So, rename all the files in /etc/apt/sources.list.d:

```

sudo rename 's/.list$/\.notinuse/' /etc/apt/sources.list.d/*.list
# now run
sudo aptitude update
# Now do whatever you wanted to do with apt-get/aptitude, eg
sudo aptitude safe-upgrade
sudo aptitude install <package>

```

---

### Post by vanhelsing2009 on 2009-12-10
[SIZE="3"]thx for all who tried t help me
i did remove the invalid repositories by this code :
> :
sudo gedit /etc/apt/sources.list.d/*.list
i have got the sub folder of sources list ready to be modified
so i removed corrupted repsitories and update my system

my problem is solved thank you so much
[/SIZE]

---

### Post by mummak on 2012-06-14
Hi all. Sorry for my ignorance,I am not a ubuntu expert. I think I have a problem similar to this and I did the following:

sudo apt-get install ppa-purge
sudo ppa-purge ppa:ubuntu-x-swat/x-updates

it corrected my update list automatically (as I am noob, I probably put smth in there that wasnt meant to be).
then just:

sudo apt-get update
sudo apt-get install
sudo apt-get autoremove

I know this might now be the proper answer to the question, but i believe this might come in handy

---

### Post by overdrank on 2012-06-14
[IMG]http://img147.imageshack.us/img147/5451/necromancing.jpg[/IMG]
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

