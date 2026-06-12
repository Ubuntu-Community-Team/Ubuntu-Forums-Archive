---
title: "No access to software centre (error messages)"
date: 2011-04-05
forum: New to Ubuntu
---

### Post by Evanfox on 2011-04-05
Hi guys,
 
It's been only a few weeks I installed ubuntu 10.10 so I'm not really acquainted :-)

Anyhoo, on the toolbar there is a no-entry sign and when I click on it the following message shows up:


[FONT=Courier New]Could not initialize the package information
An unresolvable problem occured, while initializing the package information 

Please report this bug against the 'update-manager' package and include the following error message:
'E:Malformed line 50 in source list /etc/apt/sources.list (dist parse)'[/FONT]


In addition, I do not have access to Ubuntu software centre so I can download nothing at the moment.

Thank you in advance :-)

Evan

---

### Post by Dutch70 on 2011-04-05
Do you have the same problem installing software from synaptic package manager?

Please run the following command in a terminal. Copy and paste the contents from gedit into your next post. Be sure to highlight the info and click the "#" symbol in the toolbar, to put it between ```
[ /CODE] tags.

[CODE]sudo gedit /etc/apt/sources.list
```

---

### Post by Evanfox on 2011-04-05
I can't get into the synaptic package manager either..

Ok this is what the command you mentioned yields

```
# deb cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)]/ maverick main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://gr.archive.ubuntu.com/ubuntu/ maverick main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://gr.archive.ubuntu.com/ubuntu/ maverick-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://gr.archive.ubuntu.com/ubuntu/ maverick universe
deb http://gr.archive.ubuntu.com/ubuntu/ maverick-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://gr.archive.ubuntu.com/ubuntu/ maverick multiverse
deb http://gr.archive.ubuntu.com/ubuntu/ maverick-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://gr.archive.ubuntu.com/ubuntu/ maverick-backports main restricted universe multiverse
# deb-src http://gr.archive.ubuntu.com/ubuntu/ maverick-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu maverick partner
# deb-src http://archive.canonical.com/ubuntu maverick partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu maverick main
deb-src http://extras.ubuntu.com/ubuntu maverick main

deb http://security.ubuntu.com/ubuntu maverick-security main restricted
deb http://security.ubuntu.com/ubuntu maverick-security universe
deb http://security.ubuntu.com/ubuntu maverick-security multiverse
deb http://archive.canonical.com/lucid partner
deb-src http://archive.canonical.com/lucid partner

```

---

### Post by plucky on 2011-04-05
Edit the file and remove ```
deb http://archive.canonical.com/lucid partner
deb-src http://archive.canonical.com/lucid partner
```

Use ```
gksudo gedit /etc/apt/sources.list
``` to edit the file.

Then run ```
sudo apt-get update
```

Good Luck

---

