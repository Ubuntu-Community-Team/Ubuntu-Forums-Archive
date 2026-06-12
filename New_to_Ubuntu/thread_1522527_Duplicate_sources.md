---
title: "Duplicate sources"
date: 2010-07-02
forum: New to Ubuntu
---

### Post by Primus1 on 2010-07-02
Think I have 2, gdm2 installed. Ran synaptic to update and got this warning:

 "Duplicate sources.list entry [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) lucid/partner Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_lucid_partner_binary-i386_Packages)"

How can I sort this problem?

---

### Post by libssd on 2010-07-02
> **Primus1 said:**
> Think I have 2, gdm2 installed. Ran synaptic to update and got this warning:

 "Duplicate sources.list entry [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) lucid/partner Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_lucid_partner_binary-i386_Packages)"

How can I sort this problem?

```
sudo gedit /etc/apt/sources.list
```
Search for duplicate lines; comment out line that you suspect is a duplicate. Save, then sudo apt-get update

---

### Post by Primus1 on 2010-07-02
can't see any gdm2? how do you put a box around the "code" in a post please?



# deb cdrom:[Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)]/ lucid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid-updates main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid universe
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid-updates universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid multiverse
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid-updates multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security multiverse

---

### Post by plucky on 2010-07-02
Look in ```
ls /etc/apt/sources.list.d/
``` and see if you have a lucid-partner.list in there.

If so edit the sources.list and put a # in front of the partner repository line ```
deb http://archive.canonical.com/ubuntu lucid partner
```

Good Luck

---

### Post by Primus1 on 2010-07-02
Thanks,I got this:

ls /etc/apt/sources.list.d/
dave@dave-desktop:~$ ls /etc/apt/sources.list.d/
gdm2setup-gdm2setup-lucid.list           opera.list
gdm2setup-ppa-lucid.list                           opera.list.save
gdm2setup-ppa-lucid.list.save                ubuntu-tweak-stable.list
lucid-partner.list                                             ubuntu-tweak-stable.list.save
lucid-partner.list.save

how would I edit it?

---

### Post by Elfy on 2010-07-02
> can't see any gdm2? how do you put a box around the "code" in a post please?Ina  quick reply box put [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end of the tex you wish to be in a code box.

Also see here for other BB code = [http://ubuntuforums.org/misc.php?do=bbcode](http://ubuntuforums.org/misc.php?do=bbcode)

Either edit the file 

```
gksudo gedit gdm2setup-gdm2setup-lucid.list
``` and put # at beginning of all lines - save, close and run ```
sudo apt-get update
``` or delete one of the duplicates 

```
sudo rm gdm2setup-gdm2setup-lucid.list
``` then run the apt-get update

---

### Post by plucky on 2010-07-02
I think the problem is > Duplicate sources.list entry [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) lucid/partner Packages

So either edit the sources.list with ```
gksudo gedit /etc/apt/sources.list
``` and put a # in front of the line ```
deb http://archive.canonical.com/ubuntu lucid partner
```

Or 

Remove the file "lucid-partner.list" from the /etc/apt/sources.list directory ```
cd /etc/apt/sources.list.d
ls
sudo rm lucid-partner.list
```

Make sure you are in the correct directory by using the ls command before using the sudo rm command.

Good luck

---

### Post by Primus1 on 2010-07-02
Put ```

gksudo gedit gdm2setup-gdm2setup-lucid.list
```
and it opened a gedit text with nothing in it, sorry.

---

### Post by Primus1 on 2010-07-02
Ok, done it I think but did get this at the end:```
Err http://ppa.launchpad.net lucid/main Packages                     
  404  Not Found
Hit http://gb.archive.ubuntu.com lucid-updates/multiverse Sources
W: Failed to fetch http://ppa.launchpad.net/gdm2setup/ppa/ubuntu/dists/lucid/main/binary-i386/Packages.gz  404  Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.

``` Don't know what that part means?

---

### Post by plucky on 2010-07-03
> **Primus1 said:**
> Ok, done it I think but did get this at the end:```
Err http://ppa.launchpad.net lucid/main Packages                     
  404  Not Found
Hit http://gb.archive.ubuntu.com lucid-updates/multiverse Sources
W: Failed to fetch http://ppa.launchpad.net/gdm2setup/ppa/ubuntu/dists/lucid/main/binary-i386/Packages.gz  404  Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.

``` Don't know what that part means?

> ls /etc/apt/sources.list.d/
gdm2setup-gdm2setup-lucid.list
[color=red]gdm2setup-ppa-lucid.list
gdm2setup-ppa-lucid.list.save[/color] 
opera.list
opera.list.save
ubuntu-tweak-stable.list
ubuntu-tweak-stable.list.save
lucid-partner.list 
lucid-partner.list.save

Remove the ones marked in red as they are not valid repositories.

Good luck

---

### Post by Primus1 on 2010-07-03
Thanks Plucky, I can't remove that text in the terminal, I highlight it and press delete but nothing happens, try to get the cursor there but it wont move from the end. How do I delete the part you indicate?

---

### Post by Elfy on 2010-07-03
```
sudo rm /etc/apt/sources.list.d/gdm2setup-gdm2setup-lucid.list
```

The .save file will not affect the apt-get update - but it can be removed in the same way.

---

### Post by Primus1 on 2010-07-03
Thanks, ran your rm code and got```
Err http://ppa.launchpad.net lucid/main Packages
  404  Not Found
Hit http://gb.archive.ubuntu.com lucid-updates/multiverse Sources
W: Failed to fetch http://ppa.launchpad.net/gdm2setup/ppa/ubuntu/dists/lucid/main/binary-i386/Packages.gz  404  Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.
``` after updating.

---

### Post by plucky on 2010-07-03
Try removing the other gdm2setup-ppa-lucid.list with the command ```
sudo rm /etc/apt/sources.list.d/gdm2setup-ppa-lucid.list
``` and see if that fixes the problem.

Good Luck

---

### Post by Primus1 on 2010-07-03
> **plucky said:**
> Try removing the other gdm2setup-ppa-lucid.list with the command ```
sudo rm /etc/apt/sources.list.d/gdm2setup-ppa-lucid.list
``` and see if that fixes the problem.

Good Luck
  Done! updated after that input with no errors. Thanks Plucky and everyone who helped here.

I'll have to leave stuff alone till I can use the Terminal - if ever, thanks again :).

---

