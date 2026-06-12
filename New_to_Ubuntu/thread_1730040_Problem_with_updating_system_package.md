---
title: "Problem with updating system package"
date: 2011-04-15
forum: New to Ubuntu
---

### Post by Lateefah-ubuntoo on 2011-04-15
Hello,


I have some problem with the automatic update, when I try to update in, always the same message;


W: Failed to fetch [http://archive.ubuntustudio.org/ubuntustudio/dists/feisty/Release.gpg](http://archive.ubuntustudio.org/ubuntustudio/dists/feisty/Release.gpg)  Something wicked happened resolving 'archive.ubuntustudio.org:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://archive.ubuntustudio.org/ubuntustudio/dists/feisty/main/i18n/Translation-en_US.bz2](http://archive.ubuntustudio.org/ubuntustudio/dists/feisty/main/i18n/Translation-en_US.bz2)  Something wicked happened resolving 'archive.ubuntustudio.org:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://archive.ubuntustudio.org/ubuntustudio/dists/feisty/main/binary-i386/Packages.gz](http://archive.ubuntustudio.org/ubuntustudio/dists/feisty/main/binary-i386/Packages.gz)  Something wicked happened resolving 'archive.ubuntustudio.org:http' (-5 - No address associated with hostname)

E: Some index files failed to download, they have been ignored, or old ones used instead.

And it's written that the last update was like 140 days ago. Some programs began to operate differently, and also VLC player, I cannot click pause and open something else after that, I have to turn off whatever I watch in VLC and then do something else. How can I know where is the problem?

---

### Post by sanguinoso on 2011-04-15
Can you post the output of this command

```
cat /etc/apt/sources.list
```

Also, what version of Ubuntu are you using?

---

### Post by Lateefah-ubuntoo on 2011-04-15
10.04  - is that the problem? All of this is happening because I did not get the newer version?

here is the output

# deb cdrom:[Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)]/ lucid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://ba.archive.ubuntu.com/ubuntu/](http://ba.archive.ubuntu.com/ubuntu/) lucid main restricted
deb-src [http://ba.archive.ubuntu.com/ubuntu/](http://ba.archive.ubuntu.com/ubuntu/) lucid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ba.archive.ubuntu.com/ubuntu/](http://ba.archive.ubuntu.com/ubuntu/) lucid-updates main restricted
deb-src [http://ba.archive.ubuntu.com/ubuntu/](http://ba.archive.ubuntu.com/ubuntu/) lucid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://ba.archive.ubuntu.com/ubuntu/](http://ba.archive.ubuntu.com/ubuntu/) lucid universe
deb-src [http://ba.archive.ubuntu.com/ubuntu/](http://ba.archive.ubuntu.com/ubuntu/) lucid universe
deb [http://ba.archive.ubuntu.com/ubuntu/](http://ba.archive.ubuntu.com/ubuntu/) lucid-updates universe
deb-src [http://ba.archive.ubuntu.com/ubuntu/](http://ba.archive.ubuntu.com/ubuntu/) lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://ba.archive.ubuntu.com/ubuntu/](http://ba.archive.ubuntu.com/ubuntu/) lucid multiverse
deb-src [http://ba.archive.ubuntu.com/ubuntu/](http://ba.archive.ubuntu.com/ubuntu/) lucid multiverse
deb [http://ba.archive.ubuntu.com/ubuntu/](http://ba.archive.ubuntu.com/ubuntu/) lucid-updates multiverse
deb-src [http://ba.archive.ubuntu.com/ubuntu/](http://ba.archive.ubuntu.com/ubuntu/) lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://ba.archive.ubuntu.com/ubuntu/](http://ba.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse
# deb-src [http://ba.archive.ubuntu.com/ubuntu/](http://ba.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse

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
deb [http://archive.ubuntustudio.org/ubuntustudio](http://archive.ubuntustudio.org/ubuntustudio) feisty main

---

### Post by Lateefah-ubuntoo on 2011-04-15
When I tried to install Ubuntu 10.10 , there is the same message again...

---

### Post by ajgreeny on 2011-04-15
You appear to have entries for Feisty in your sources.list file, which should not really be there if you are running Lucid 10.04.

The command given you by sanguinoso will probably show this.  You can then edit it out either manually with ```
gksu gedit /etc/apt/sources.list
``` or by using **System->Administration->Software Sources**

EDIT:

I've just seen your newly added list, and it is the bottom line that needs removing or commenting out with # at the start of the line, like this:-.
# deb [http://archive.ubuntustudio.org/ubuntustudio](http://archive.ubuntustudio.org/ubuntustudio) feisty main

---

### Post by Lateefah-ubuntoo on 2011-04-15
I typed this  gksu gedit /etc/apt/sources.listand I got the same output as before

---

### Post by sanguinoso on 2011-04-15
Place this character '#' (without quotes) in front of the last line when you type 
```
gksu gedit /etc/apt/sources.list
```

---

