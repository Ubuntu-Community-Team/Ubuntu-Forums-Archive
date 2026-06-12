---
title: "Source List Trouble"
date: 2009-11-15
forum: New to Ubuntu
---

### Post by GatorMike on 2009-11-15
Hello everyone, I'm new to Linux. I just switched from windows and I have a basic understanding of how to use linux. I am having some problems with my source list. I get the error-

E: type 'usage' is not known on line 58 in source list /etc/apt/source.list, E:The source list could not be read

Could someone give me some help with this? I am running Karmic Koala

---

### Post by dependancyhell on 2009-11-15
Could you post the output of:

```

ls /etc/apt/sources.list.d -l

```

And 

```

cat /etc/apt/sources.list

```

---

### Post by Locke_99GS on 2009-11-15
If you could make that cat command like this instead, we'd all be very grateful :)

```

cat -n /etc/apt/sources.list

```

---

### Post by GatorMike on 2009-11-16
cat -n /etc/apt/sources.list
     1    
     2    # See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
     3    # newer versions of the distribution.
     4    
     5    deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic main restricted
     6    deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic main restricted
     7    
     8    ## Major bug fix updates produced after the final release of the
     9    ## distribution.
    10    deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates main restricted
    11    deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates main restricted
    12    
    13    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
    14    ## team. Also, please note that software in universe WILL NOT receive any
    15    ## review or updates from the Ubuntu security team.
    16    deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic universe
    17    deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic universe
    18    deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates universe
    19    deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates universe
    20    
    21    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
    22    ## team, and may not be under a free licence. Please satisfy yourself as to 
    23    ## your rights to use the software. Also, please note that software in 
    24    ## multiverse WILL NOT receive any review or updates from the Ubuntu
    25    ## security team.
    26    deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic multiverse
    27    deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic multiverse
    28    deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates multiverse
    29    deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates multiverse
    30    
    31    ## Uncomment the following two lines to add software from the 'backports'
    32    ## repository.
    33    ## N.B. software from this repository may not have been tested as
    34    ## extensively as that contained in the main release, although it includes
    35    ## newer versions of some applications which may provide useful features.
    36    ## Also, please note that software in backports WILL NOT receive any review
    37    ## or updates from the Ubuntu security team.
    38    # deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse
    39    # deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse
    40    
    41    ## Uncomment the following two lines to add software from Canonical's
    42    ## 'partner' repository.
    43    ## This software is not part of Ubuntu, but is offered by Canonical and the
    44    ## respective vendors as a service to Ubuntu users.
    45    # deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner
    46    # deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner
    47    
    48    deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security main restricted
    49    deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security main restricted
    50    deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security universe
    51    deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security universe
    52    deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security multiverse
    53    deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security multiverse
    54    deb [http://ppa.launchpad.net/compiz/ubuntu](http://ppa.launchpad.net/compiz/ubuntu) karmic main
    55    deb [http://repository.cairo-dock.org/ubuntu](http://repository.cairo-dock.org/ubuntu) karmic cairo-dock ## Cairo-Dock-Stable
    56    
    57    deb [http://repository.cairo-dock.org/ubuntu](http://repository.cairo-dock.org/ubuntu) jaunty cairo-dock  # For Ubuntu 9.04
    58    usage: sudo [-n] -h | -K | -k | -L | -V | -v
    59    usage: sudo -l[l] [-AnS] [-g groupname|#gid] [-U username] [-u username|#uid]
    60                [-g groupname|#gid] [command]
    61    usage: sudo [-AbEHnPS] [-C fd] [-g groupname|#gid] [-p prompt] [-u
    62                username|#uid] [-g groupname|#gid] [VAR=value] [-i|-s] [<command>]
    63    usage: sudo -e [-AnS] [-C fd] [-g groupname|#gid] [-p prompt] [-u
    64                username|#uid] file ...
    65    deb [http://repository.cairo-dock.org/ubuntu](http://repository.cairo-dock.org/ubuntu) karmic cairo-dock ## Cairo-Dock-Stable
    66    deb [http://repository.cairo-dock.org/ubuntu](http://repository.cairo-dock.org/ubuntu) karmic cairo-dock ## Cairo-Dock-Stable
    67    deb [http://repository.cairo-dock.org/ubuntu](http://repository.cairo-dock.org/ubuntu) karmic cairo-dock ## Cairo-Dock-Stable
    68    deb [http://repository.cairo-dock.org/ubuntu](http://repository.cairo-dock.org/ubuntu) karmic cairo-dock ## Cairo-Dock-Stable
    69    deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) karmic free non-free
    70    deb [http://repository.cairo-dock.org/ubuntu](http://repository.cairo-dock.org/ubuntu) karmic cairo-dock ## Cairo-Dock-Stable

---

### Post by GatorMike on 2009-11-16
ls /etc/apt/sources.list.d -l
total 0

---

### Post by dependancyhell on 2009-11-16
The comments have gone funny.

Delete

> 
58    usage: sudo [-n] -h | -K | -k | -L | -V | -v
    59    usage: sudo -l[l] [-AnS] [-g groupname|#gid] [-U username] [-u username|#uid]
    60                [-g groupname|#gid] [command]
    61    usage: sudo [-AbEHnPS] [-C fd] [-g groupname|#gid] [-p prompt] [-u
    62                username|#uid] [-g groupname|#gid] [VAR=value] [-i|-s] [<command>]
    63    usage: sudo -e [-AnS] [-C fd] [-g groupname|#gid] [-p prompt] [-u
    64                username|#uid] file ...


save the file

```

sudo apt-get update

```

Then you'll be working again.

---

