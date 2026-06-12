---
title: "Why does software update not work ? Help please"
date: 2011-08-19
forum: New to Ubuntu
---

### Post by blitzburgh on 2011-08-19
I am using Ubuntu 11.04 Natty and when I tried the recent update, I got the following error message:

 [http://i25.lulzimg.com/b24b24.png](http://i25.lulzimg.com/b24b24.png)

Now, I think this is probably because I am using Macbuntu, but I am not sure. I think this because I never had a problem like this before. Can anyone shed some light as to why this is happening? Also, I cannot install or uninstall anything from the software center unless I install this package. Thanks in advance for your help.

---

### Post by hansdown on 2011-08-19
Hi blitzburgh.

Have you tried running 

apt-get install-f

Or turning off third party repos?

---

### Post by mikewhatever on 2011-08-19
You have a kernel dependency problem, which shouldn't be related to Macbuntu. Have you added more third party repositories? Can you show us your sources list?
```
cat /etc/apt/sources.list
```

---

### Post by blitzburgh on 2011-08-20
> **mikewhatever said:**
> You have a kernel dependency problem, which shouldn't be related to Macbuntu. Have you added more third party repositories? Can you show us your sources list?
```
cat /etc/apt/sources.list
```

Here you go: 

[B]# deb cdrom:[Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)]/ lucid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security multiverse
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) natty main #Third party developers repository

[/B]

---

### Post by fidelandche on 2011-08-20
Try this in a terminal

```
sudo rm /var/lib/apt/lists/* -vf
```

and then this

```
sudo apt-get update
```

---

### Post by blitzburgh on 2011-08-20
> **fidelandche said:**
> Try this in a terminal

```
sudo rm /var/lib/apt/lists/* -vf
```and then this

```
sudo apt-get update
```

hey, i tried this and then tried to update and i still get the same message: 

```
http://i25.lulzimg.com/237fd4.png
```

---

### Post by madjr on 2011-08-20
are you using lucid 10.04 or natty 11.04 ?

that kernel seems to be for natty but all your repos are from lucid...

---

### Post by gandaran on 2011-08-20
> **blitzburgh said:**
> Here you go: 

[B]# deb cdrom:[Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)]/ lucid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security multiverse
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) natty main #Third party developers repository

[/B]
did you do a upgrade to ubuntu 11.04?
you got a mixture of lucid and natty repositories which shouldn't be, I would recommend you do a clean ubuntu install instead but you can fix this software sources list too.

---

### Post by blade4 on 2011-08-20
Hi blitzburgh , 

Now I may be completely wrong here but if the problem is only due to the sources.list file then why not replace it with the same file from someone who has the same ubuntu version as you ( after backing up your original of course ) . You can ask someone to paste their own sources.list on this thread and replace yours with that one .

---

### Post by Miljet on 2011-08-20
It looks like all the references to Lucid are commented out, so that shouldn't be a problem.

---

### Post by coffeecat on 2011-08-20
Third party repositories usually have their own *.list files in /etc/apt/sources.list.d/. Post the output of:

```
ls /etc/apt/sources.list.d/
```

---

### Post by blitzburgh on 2011-08-20
> **coffeecat said:**
> Third party repositories usually have their own *.list files in /etc/apt/sources.list.d/. Post the output of:

```
ls /etc/apt/sources.list.d/
```

Here you are:

[B]am-monkeyd-nautilus-elementary-ppa-natty.list
am-monkeyd-nautilus-elementary-ppa-natty.list.save
elementaryart-elementarydesktop-natty.list
elementaryart-elementarydesktop-natty.list.save
google-chrome.list
google-chrome.list.distUpgrade
google-chrome.list.save
jd-team-jdownloader-lucid.list.distUpgrade
jd-team-jdownloader-lucid.list.save
jd-team-jdownloader-maverick.list
jd-team-jdownloader-maverick.list.save
lucid-partner.list
lucid-partner.list.distUpgrade
lucid-partner.list.save
mozillateam-firefox-stable-lucid.list.distUpgrade
mozillateam-firefox-stable-lucid.list.save
mozillateam-firefox-stable-maverick.list
mozillateam-firefox-stable-maverick.list.save
nikount-orta-desktop-natty.list
nikount-orta-desktop-natty.list.save
nilarimogard-webupd8-natty.list
nilarimogard-webupd8-natty.list.save
tiheum-equinox-natty.list
tiheum-equinox-natty.list.save
tualatrix-ppa-lucid.list.distUpgrade
tualatrix-ppa-lucid.list.save
tualatrix-ppa-maverick.list
tualatrix-ppa-maverick.list.save
tualatrix-ppa-natty.list
ubuntu-tweak-stable.list.save
weather-indicator-team-ppa-natty.list
weather-indicator-team-ppa-natty.list.save[/B]

---

### Post by blitzburgh on 2011-08-20
> **gandaran said:**
> did you do a upgrade to ubuntu 11.04?
you got a mixture of lucid and natty repositories which shouldn't be, I would recommend you do a clean ubuntu install instead but you can fix this software sources list too.

I originally had XP on this laptop. Then, I did a complete install of Lucid. Then when the new update for Natty came out, I upgraded to that.

---

### Post by coffeecat on 2011-08-20
> **blitzburgh said:**
> Here you are:

[B]am-monkeyd-nautilus-elementary-ppa-natty.list
am-monkeyd-nautilus-elementary-ppa-natty.list.save
elementaryart-elementarydesktop-natty.list
elementaryart-elementarydesktop-natty.list.save
google-chrome.list
google-chrome.list.distUpgrade
google-chrome.list.save
jd-team-jdownloader-lucid.list.distUpgrade
jd-team-jdownloader-lucid.list.save
jd-team-jdownloader-maverick.list
jd-team-jdownloader-maverick.list.save
lucid-partner.list
lucid-partner.list.distUpgrade
lucid-partner.list.save
mozillateam-firefox-stable-lucid.list.distUpgrade
mozillateam-firefox-stable-lucid.list.save
mozillateam-firefox-stable-maverick.list
mozillateam-firefox-stable-maverick.list.save
nikount-orta-desktop-natty.list
nikount-orta-desktop-natty.list.save
nilarimogard-webupd8-natty.list
nilarimogard-webupd8-natty.list.save
tiheum-equinox-natty.list
tiheum-equinox-natty.list.save
tualatrix-ppa-lucid.list.distUpgrade
tualatrix-ppa-lucid.list.save
tualatrix-ppa-maverick.list
tualatrix-ppa-maverick.list.save
tualatrix-ppa-natty.list
ubuntu-tweak-stable.list.save
weather-indicator-team-ppa-natty.list
weather-indicator-team-ppa-natty.list.save[/B]

That is a lot of 3rd party repositories, several of which are for pre-Natty releases. The error message you have been getting tells you to disable 3rd party repositories. You need to examine each list file to see if the lines in it have been commented out and, if not, comment them. A commented line starts with a '#' symbol, meaning that it is disabled.

If you don't know how to do that, open Synaptic -> Settings -> Repositories -> "Other Software" tab and uncheck all the 3rd party repositories.

---

### Post by blitzburgh on 2011-08-20
> **coffeecat said:**
> That is a lot of 3rd party repositories, several of which are for pre-Natty releases. The error message you have been getting tells you to disable 3rd party repositories. You need to examine each list file to see if the lines in it have been commented out and, if not, comment them. A commented line starts with a '#' symbol, meaning that it is disabled.

If you don't know how to do that, open Synaptic -> Settings -> Repositories -> "Other Software" tab and uncheck all the 3rd party repositories.

I went to the synaptic and unchecked every box in the other software tab but i still get the same error message. And how exactly do I comment those lines, as in where do i find these lines to comment them?

---

### Post by coffeecat on 2011-08-21
If you've unticked the boxes in Synaptic (the GUI way), you don't need to comment the lines in those files. You would use a text editor with administrative privileges to do that, but doing what you've done in Synaptic is just fine. Now open a terminal, and:

```
sudo apt-get update
sudo apt=get upgrade
```

Do you get any error messages?

---

