---
title: "Upgrade of V7.10"
date: 2009-04-28
forum: New to Ubuntu
---

### Post by peter1608 on 2009-04-28
I am running Version 7.10 on a system which until a week or so ago had no internet connection.  When I did connect, I started receiving pop up messages telling me that a large number of upgrades were available.  Yet, when I tried to accept these upgrades I received a stream of error messages along the lines of 404 Not Found.  I have copied a small excerpt from these below.  

Already I can hear the replies saying I should update to the latest version.  Well, the upgrade panel has a button for doing just that, but warns you should apply all the upgrades first!   Also, I am a firm believer in the ‘If it ain’t broke then don’t fix it’ philosophy.

Is this a question of the V7.10 repositories no longer being available? Are they archived anywhere? If so, where, and do I just change the urls in /etc/apt/source.list? Or is there really no alternative to installing a more recent version from scratch? (Of course there is – keep the existing system. It does what I want so why go through the hassle of changing it?)

Peter


Sample error messages

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/main/g/glibc/libc6_2.6.1-1ubuntu10_i386.deb](http://gb.archive.ubuntu.com/ubuntu/pool/main/g/glibc/libc6_2.6.1-1ubuntu10_i386.deb)
  404 Not Found [IP: 194.169.254.10 80]


W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/main/g/glibc/libc6-i686_2.6.1-1ubuntu10_i386.deb](http://gb.archive.ubuntu.com/ubuntu/pool/main/g/glibc/libc6-i686_2.6.1-1ubuntu10_i386.deb)
  404 Not Found [IP: 194.169.254.10 80]

and so on for about 200 lines …

---

### Post by unutbu on 2009-04-28
Gutsy (version 7.10) is no longer an officially supported version of Ubuntu.
I think that is why gb.archive.ubuntu.com no longer makes Gutsy packages available.

However, if you change 
```

http://gb.archive.ubuntu.com
```

to 
```

http://old-releases.ubuntu.com
```

in your /etc/apt/sources.list, then you should be able to get Gutsy packages again.

---

### Post by peter1608 on 2009-04-28
Thanks for that tip.  I'll try tonight and post how I get on tomorrow.

Peter

---

### Post by peter1608 on 2009-04-29
Last night I tried changing the repository url as suggested, but sorry to report it still failed, with similar error messages presumably pointing to another repository which has now moved, eg:-

W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/e/e2fsprogs/e2fslibs_1.40.2-1ubuntu1.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/e/e2fsprogs/e2fslibs_1.40.2-1ubuntu1.1_i386.deb)
  404 Not Found

I have looked through my original /etc/apt/sources.list file, and tried all the url's in my browser. I'm guessing now, but it seems there should be a ./dist/gutsy subfolder in each one.  It's missing in both [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) and [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu), but present in [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu). So I think I need to be pointed towards an alternative for the security repository.

Have I worked this out correctly? Can anyone advise me where to find the missing repository/repositories?
  
I have posted my original /etc/apt/sources.list file below.  Have I missed anything?

Peter


deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071017)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy universe
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-updates universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse

---

### Post by unutbu on 2009-04-29
```
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071017)]/ gutsy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://old-releases.ubuntu.com/ubuntu/ gutsy main restricted
deb-src http://old-releases.ubuntu.com/ubuntu/ gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://old-releases.ubuntu.com/ubuntu/ gutsy-updates main restricted
deb-src http://old-releases.ubuntu.com/ubuntu/ gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://old-releases.ubuntu.com/ubuntu/ gutsy universe
deb-src http://old-releases.ubuntu.com/ubuntu/ gutsy universe
deb http://old-releases.ubuntu.com/ubuntu/ gutsy-updates universe
deb-src http://old-releases.ubuntu.com/ubuntu/ gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://old-releases.ubuntu.com/ubuntu/ gutsy multiverse
deb-src http://old-releases.ubuntu.com/ubuntu/ gutsy multiverse
deb http://old-releases.ubuntu.com/ubuntu/ gutsy-updates multiverse
deb-src http://old-releases.ubuntu.com/ubuntu/ gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://old-releases.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
deb-src http://old-releases.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu gutsy partner
# deb-src http://archive.canonical.com/ubuntu gutsy partner

# This does not work
# deb http://old-releases.ubuntu.com/ubuntu gutsy partner
# deb-src http://old-releases.ubuntu.com/ubuntu gutsy partner

deb http://old-releases.ubuntu.com/ubuntu gutsy-security main restricted
deb-src http://old-releases.ubuntu.com/ubuntu gutsy-security main restricted
deb http://old-releases.ubuntu.com/ubuntu gutsy-security universe
deb-src http://old-releases.ubuntu.com/ubuntu gutsy-security universe
deb http://old-releases.ubuntu.com/ubuntu gutsy-security multiverse
deb-src http://old-releases.ubuntu.com/ubuntu gutsy-security multiverse

```

security.ubuntu.com can also be changed to old-releases.ubuntu.com.

I have not found a substitute for the archive.canonical.com partner repository.

---

### Post by peter1608 on 2009-04-29
Thank you. Try again tonight

I am hoping the [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) repository is ok - it still seems to have a number of subfolders with 'gutsy' in the name.

Peter

---

### Post by peter1608 on 2009-04-30
Success!  Although there were couple of glitches along the way. 

Firstly the upgrade manager reported that my system was up to date.  I assume one of the failed attempts had set a flag somewhere.    But selecting some sort of rescan option made it change its mind.  

Secondly during the upgrade it popped up a dialog box asking me to confirm some action I didn't understand.  As I wasn't expecting any such dialog, and had left the system unattended, this lost me a couple of hours or so.  I hopy that confirming this action hasn't caused any future problems.

Thanks for the help.

Peter

---

### Post by Sef on 2009-04-30
It would be best to upgrade your system since gutsy is no longer supported, patches are no longer being done.

---

### Post by Paqman on 2009-04-30
> **Sef said:**
> It would be best to upgrade your system since gutsy is no longer supported, patches are no longer being done.

Agreed. Now that your system is available over the internet the lack of security updates puts you at risk.

If you've got Gutsy (7.10) you should be able to upgrade to the current Long-Term Support version, which is Hardy Heron (8.04). Alternatively you can do a full reinstall and get the current 6-monthly release, Jaunty Jackelope (9.04)

---

