---
title: "hardy sources.list"
date: 2009-05-02
forum: New to Ubuntu
---

### Post by kaston on 2009-05-02
i noticed that my sources.list file seemed to have a lot of the word "gutsy" in it so i figured i would update it.  i copied the sources.list shown here:  [http://ubuntuguide.org/wiki/Ubuntu:Hardy#sources.list](http://ubuntuguide.org/wiki/Ubuntu:Hardy#sources.list) but now my update manager gives me an error when i try to run it.  

is there a standard sources.list file that i should have for hardy?  where can i get it?

---

### Post by fugaki on 2009-05-02
Here is mine, I havent modified it at all from the default install.

#deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)]/ jaunty main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse

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
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security

---

### Post by fugaki on 2009-05-02
ah sorry, i thought you wanted jaunty, my apologies.

---

### Post by kaston on 2009-05-02
no problem.  yeah i guess i'm looking for the list that should have come with hardy when i installed.  not sure how i got rid of it but i don't think i have it anymore

---

### Post by llamabr on 2009-05-02
> **kaston said:**
> i noticed that my sources.list file seemed to have a lot of the word "gutsy" in it so i figured i would update it.  i copied the sources.list shown here:  [http://ubuntuguide.org/wiki/Ubuntu:Hardy#sources.list](http://ubuntuguide.org/wiki/Ubuntu:Hardy#sources.list) but now my update manager gives me an error when i try to run it.  

is there a standard sources.list file that i should have for hardy?  where can i get it?

Man, that's alot of stuff.

What are you doing, and what's the error?

---

### Post by kaston on 2009-05-02
here's the error:
Could not initialize the package information

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Malformed line 31 in source list /etc/apt/sources.list (dist parse), E:The list of sources could not be read.'

i don't do anything crazy.  i just want the standard stuff and medibuntu

---

### Post by scradock on 2009-05-02
> **kaston said:**
> here's the error:
Could not initialize the package information

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Malformed line 31 in source list /etc/apt/sources.list (dist parse), E:The list of sources could not be read.'

i don't do anything crazy.  i just want the standard stuff and medibuntu
So what does line 31 in your sources.list actually say? It looks like a typo might cause such a response....

---

### Post by llamabr on 2009-05-02
Here's mine.  when upgrading, I just change the intrepid for jaunty, or whatever, and do an update, upgrade, and dist-upgrade.

```
deb http://ftp.usf.edu/pub/ubuntu/ jaunty main restricted
deb-src http://ftp.usf.edu/pub/ubuntu/ jaunty main restricted

deb http://ftp.usf.edu/pub/ubuntu/ jaunty-updates main restricted universe mult$
deb-src http://ftp.usf.edu/pub/ubuntu/ jaunty-updates main restricted universe $

deb http://ftp.usf.edu/pub/ubuntu/ jaunty universe
deb-src http://ftp.usf.edu/pub/ubuntu/ jaunty universe

deb http://ftp.usf.edu/pub/ubuntu/ jaunty multiverse
deb-src http://ftp.usf.edu/pub/ubuntu/ jaunty multiverse

deb http://ftp.usf.edu/pub/ubuntu/ jaunty-backports main restricted universe mu$
deb-src http://ftp.usf.edu/pub/ubuntu/ jaunty-backports main restricted univers$

deb http://ftp.usf.edu/pub/ubuntu/ jaunty-security main restricted
deb-src http://ftp.usf.edu/pub/ubuntu/ jaunty-security main restricted
deb http://ftp.usf.edu/pub/ubuntu/ jaunty-security universe
deb-src http://ftp.usf.edu/pub/ubuntu/ jaunty-security universe
deb http://ftp.usf.edu/pub/ubuntu/ jaunty-security multiverse

```

---

### Post by llamabr on 2009-05-02
You can go right to line 31 by doing:

```
nano +31 /etc/apt/sources.list
```

Or you could just count down there.

---

### Post by kaston on 2009-05-02
> **llamabr said:**
> Here's mine.  when upgrading, I just change the intrepid for jaunty, or whatever, and do an update, upgrade, and dist-upgrade.

```
deb http://ftp.usf.edu/pub/ubuntu/ jaunty main restricted
deb-src http://ftp.usf.edu/pub/ubuntu/ jaunty main restricted

deb http://ftp.usf.edu/pub/ubuntu/ jaunty-updates main restricted universe mult$
deb-src http://ftp.usf.edu/pub/ubuntu/ jaunty-updates main restricted universe $

deb http://ftp.usf.edu/pub/ubuntu/ jaunty universe
deb-src http://ftp.usf.edu/pub/ubuntu/ jaunty universe

deb http://ftp.usf.edu/pub/ubuntu/ jaunty multiverse
deb-src http://ftp.usf.edu/pub/ubuntu/ jaunty multiverse

deb http://ftp.usf.edu/pub/ubuntu/ jaunty-backports main restricted universe mu$
deb-src http://ftp.usf.edu/pub/ubuntu/ jaunty-backports main restricted univers$

deb http://ftp.usf.edu/pub/ubuntu/ jaunty-security main restricted
deb-src http://ftp.usf.edu/pub/ubuntu/ jaunty-security main restricted
deb http://ftp.usf.edu/pub/ubuntu/ jaunty-security universe
deb-src http://ftp.usf.edu/pub/ubuntu/ jaunty-security universe
deb http://ftp.usf.edu/pub/ubuntu/ jaunty-security multiverse

```

maybe i'll just copy this and substitute in hardy for jaunty.  still, isn't there some ubuntu site with the "official" list that comes with the hardy upgrade?

---

### Post by overdrank on 2009-05-02
> **kaston said:**
> maybe i'll just copy this and substitute in hardy for jaunty.  still, isn't there some ubuntu site with the "official" list that comes with the hardy upgrade?

Sure is, [Here]("https://help.ubuntu.com/community/Repositories/CommandLine")

---

### Post by kaston on 2009-05-02
> **overdrank said:**
> Sure is, [Here]("https://help.ubuntu.com/community/Repositories/CommandLine")

thanks.  no mention of medibuntu though.  i guess that's considered one of the "other" repositories

---

### Post by overdrank on 2009-05-02
> **kaston said:**
> thanks.  no mention of medibuntu though.  i guess that's considered one of the "other" repositories

Hi and yes. About half way through the link it mention
>  There are some (but not many) good reasons for which you might want to add non-Ubuntu repositories to your list of software sources. Some software cannot be distributed by Ubuntu due to patent and licensing restrictions in some countries (see the **[RestrictedFormats]("https://help.ubuntu.com/community/RestrictedFormats")** page for examples). You might want to add repositories that offer such software. Make sure that all repositories you add in this way have been tested and are known to work on Ubuntu systems. Repositories that are not designed to work with your version of Ubuntu can introduce inconsistencies in your system and might force you to re-install.

---

