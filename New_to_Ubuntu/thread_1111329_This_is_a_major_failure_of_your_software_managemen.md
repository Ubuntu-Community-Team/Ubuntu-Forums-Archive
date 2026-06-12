---
title: "This is a major failure of your software management system."
date: 2009-03-30
forum: New to Ubuntu
---

### Post by gridd on 2009-03-30
hi I seem to have a bug in update manager I was trying to download the Ciro installation  when half way through I got this error message.


This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'.

~$ /etc/apt/sources.list

bash: /etc/apt/sources.list: Permission denied
~$ 

sudo apt-get update
 
E: Type 'wget' is not known on line 59 in source list /etc/apt/sources.list

sudo apt-get install -f

E: Type 'wget' is not known on line 59 in source list /etc/apt/sources.list
E: The list of sources could not be read.

any help would be welcome. I dont know weather or how to, file a bug report yet. Thanks.

OH ps i seem to be getting port scans from Static the planet.com which is apparently a Trojan host data miner of some sort   but my virus scan came up clean.

---

### Post by lykwydchykyn on 2009-03-30
> **gridd said:**
> 
~$ /etc/apt/sources.list

bash: /etc/apt/sources.list: Permission denied
~$ 

If you just put the name of the file, the shell tries to launch it as an app.  Since sources.list is a config file (without executable permissions), you get a permission denied error.
If you want to see the contents:
```

cat /etc/apt/sources.list

```
Or of course you can open it in gedit or any GUI text viewer/editor.

Once you do that, post the contents here, it may prove helpful in fixing the problem.
> 
sudo apt-get update
 
E: Type 'wget' is not known on line 59 in source list /etc/apt/sources.list

sudo apt-get install -f

E: Type 'wget' is not known on line 59 in source list /etc/apt/sources.list
E: The list of sources could not be read.

any help would be welcome. I dont know weather or how to, file a bug report yet. Thanks.

Sounds like something is messed up in your sources.list file.  On line 59, apparently.

---

### Post by gridd on 2009-03-30
-desktop:~$ cat /etc/apt/sources.list
# 
# deb cdrom:[Ubuntu 8.04.2 _Hardy Heron_ - Release i386 (20090121.2)]/ hardy main restricted

#deb cdrom:[Ubuntu 8.04.2 _Hardy Heron_ - Release i386 (20090121.2)]/ hardy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) hardy main restricted
deb-src [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) hardy-updates main restricted
deb-src [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) hardy universe
deb-src [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) hardy universe
deb [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) hardy-updates universe
deb-src [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) hardy multiverse
deb-src [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) hardy multiverse
deb [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) hardy-updates multiverse
deb-src [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
# deb-src [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiversedeb [http://repository.cairo-dock.org/ubuntu](http://repository.cairo-dock.org/ubuntu) hardy cairo-dock
wget -q [http://repository.cairo-dock.org/ubuntu/cairo-dock.gpg](http://repository.cairo-dock.org/ubuntu/cairo-dock.gpg) -O- | sudo apt-key add -sudo apt-get updateapt-get install cairo-dock cairo-dock-plug-ins
sudo apt-get install cairo-dock-plugins



-desktop:~$ 


hi here's the result.

---

### Post by Tibuda on 2009-03-30
```
wget -q http://repository.cairo-dock.org/ubuntu/cairo-dock.gpg -O- | sudo apt-key add -sudo apt-get updateapt-get install cairo-dock cairo-dock-plug-ins
sudo apt-get install cairo-dock-plugins
```
This should not be on sources.list

---

### Post by LowSky on 2009-03-30
> **gridd said:**
> 
```
wget -qhttp://repository.cairo-dock.org/ubuntu/cairo-dock.gpg -O- | sudo apt-key add -sudo apt-get updateapt-get install cairo-dock cairo-dock-plug-ins
sudo apt-get install cairo-dock-plugins
```
  

remove this, I dont know what you did but you ended up with command that you would use in terminal in your sources list, they dont belong there, infact these codes would add the correct lines to your source list if entered from a terminal

---

### Post by gridd on 2009-03-30
> **danielrmt said:**
> ```
wget -q http://repository.cairo-dock.org/ubuntu/cairo-dock.gpg -O- | sudo apt-key add -sudo apt-get updateapt-get install cairo-dock cairo-dock-plug-ins
sudo apt-get install cairo-dock-plugins
```
This should not be on sources.list


hi I cant edit it out in terminal please advise.

---

### Post by anjilslaire on 2009-03-30
LowSky is correct. You want to remove that line and do this in a terminal:
```

wget -q http://repository.cairo-dock.org/ubuntu/cairo-dock.gpg -O- | sudo apt-key add -sudo apt-get updateapt-get install cairo-dock cairo-dock-plug-ins
sudo apt-get install cairo-dock-plugins

```

---

### Post by anjilslaire on 2009-03-30
> **gridd said:**
> hi I cant edit it out in terminal please advise.

Ok, in terminal do:
```

sudo gedit /etc/apt/sources.list

```

Then delete the noted entry and save. Then, run that line in the terminal as noted.

---

### Post by kanikilu on 2009-03-30
You'll need to edit the sources.list file (Applications > Accessories > Terminal, then type *gksu gedit /etc/apt/sources.list* and press enter. You should be prompted for your password, and then the file should open in gedit. Each line should start with "deb" or "deb-src".

Scroll to the end, to this area and make the changes:
```
deb-src http://security.ubuntu.com/ubuntu hardy-security multiverse[COLOR="Red"]<INSERT NEW LINE HERE>[/COLOR]deb http://repository.cairo-dock.org/ubuntu hardy cairo-dock
[COLOR="Red"]- Remove these last two lines - they are meant to be run in a terminal -[/COLOR]
wget -q http://repository.cairo-dock.org/ubuntu/cairo-dock.gpg -O- | sudo apt-key add -sudo apt-get updateapt-get install cairo-dock cairo-dock-plug-ins
sudo apt-get install cairo-dock-plugins
```

---

### Post by Therion on 2009-03-30
Open a terminal and cut and paste: ```
sudo nano /etc/apt/sources.list
```
Remove the offending code as explained above, save and exit.  

Joy!

---

### Post by gridd on 2009-03-30
-desktop:~$ cat /etc/apt/sources.list
# 
# deb cdrom:[Ubuntu 8.04.2 _Hardy Heron_ - Release i386 (20090121.2)]/ hardy main restricted

#deb cdrom:[Ubuntu 8.04.2 _Hardy Heron_ - Release i386 (20090121.2)]/ hardy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) hardy main restricted
deb-src [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) hardy-updates main restricted
deb-src [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) hardy universe
deb-src [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) hardy universe
deb [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) hardy-updates universe
deb-src [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) hardy multiverse
deb-src [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) hardy multiverse
deb [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) hardy-updates multiverse
deb-src [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
# deb-src [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiversedeb 




hi I have removed the offending two lines well three infact and will have to lie down and give up for now as my head hurts at least I have my repository working again many thanks folks. Ill try again tomorrow or so I hope.

---

### Post by LowSky on 2009-03-31
> **gridd said:**
> -desktop:~$ cat /etc/apt/sources.list
# 
# deb cdrom:[Ubuntu 8.04.2 _Hardy Heron_ - Release i386 (20090121.2)]/ hardy main restricted

#deb cdrom:[Ubuntu 8.04.2 _Hardy Heron_ - Release i386 (20090121.2)]/ hardy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) hardy main restricted
deb-src [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) hardy-updates main restricted
deb-src [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) hardy universe
deb-src [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) hardy universe
deb [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) hardy-updates universe
deb-src [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) hardy multiverse
deb-src [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) hardy multiverse
deb [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) hardy-updates multiverse
deb-src [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
# deb-src [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse[COLOR="Red"]deb [/COLOR]




hi I have removed the offending two lines well three infact and will have to lie down and give up for now as my head hurts at least I have my repository working again many thanks folks. Ill try again tomorrow or so I hope.


you still have an issue please remove this part i shaded in red

---

