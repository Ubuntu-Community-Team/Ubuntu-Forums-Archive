---
title: "Upgrading to 10.04"
date: 2010-04-30
forum: New to Ubuntu
---

### Post by fly_boy on 2010-04-30
Hi, I want ot update my Karmic Koala install to the latest Ubunti build, do I need to install form scratch or can I just upgrade through some process or another....

---

### Post by Paqman on 2010-04-30
You can do either.

Either grab the new ISO, burn a new LiveCD and reinstall, or do an upgrade through Update Manager (it'll have a box at the top telling you an upgrade is available).

---

### Post by fly_boy on 2010-04-30
Brill. If I do it via upgrade manager, do I lose the config of my current install etc....

---

### Post by Paqman on 2010-04-30
> **fly_boy said:**
> Brill. If I do it via upgrade manager, do I lose the config of my current install etc....

Nope. Couple of points though:
[LIST=1]
[*]The servers are swamped. If you upgrade right now it'll be really slow. Give it a few days, and try scanning for the fastest available server.
[*]Do a backup anyway. It never hurts to have backups.
[/LIST]

---

### Post by gwilkins82 on 2010-04-30
Ok, another question about upgrading.  I'd like to do it via the update manager but I have a few old repository errors I am not sure how to correct so it bounces me out of the process when they come up faulty.  How do I get rid of these two errors?:
Failed to fetch [http://archive.ubuntu.com/dists/karmic/main/binary-i386/Packages.gz](http://archive.ubuntu.com/dists/karmic/main/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.88.45 80]
Failed to fetch [http://archive.ubuntu.com/dists/karmic/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/dists/karmic/universe/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.88.45 80]
Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by Automat2 on 2010-04-30
I have upgraded to 10.04, but I have a question. How do I know whether I am using 64-bit or 32-bit? If I have the 32-bit, can I change it to the 64-bit?

I've got:
AMD Athlon II x4
Asus M4A78
4GB RAM
500GB HD

Uname -a gives:
> Linux jordi-desktop 2.6.32-21-generic-pae #32-Ubuntu SMP Fri Apr 16 09:39:35 UTC 2010 i686 GNU/Linux


---

### Post by gwilkins82 on 2010-04-30
Whoops - the hyperlinks above are giving me problems, but are abbreviated...

W: Failed to fetch [http://archive.ubuntu.com/dists/karmic/main/binary-i386/Packages.gz](http://archive.ubuntu.com/dists/karmic/main/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.88.45 80]

W: Failed to fetch [http://archive.ubuntu.com/dists/karmic/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/dists/karmic/universe/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.88.45 80]

Hopefully these will remain full length.

ETA - damn.  Didn't work...at any rate the problem sources are /karmic/main/binary-i386/Packages.gz  and the 2nd one is the same except /universe instead of /main.  Any help out there?

---

### Post by stoneage on 2010-04-30
> **gwilkins82 said:**
> Whoops - the hyperlinks above are giving me problems, but are abbreviated...

W: Failed to fetch [http://archive.ubuntu.com/dists/karmic/main/binary-i386/Packages.gz](http://archive.ubuntu.com/dists/karmic/main/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.88.45 80]

W: Failed to fetch [http://archive.ubuntu.com/dists/karmic/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/dists/karmic/universe/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.88.45 80]

Hopefully these will remain full length.

ETA - damn.  Didn't work...at any rate the problem sources are /karmic/main/binary-i386/Packages.gz  and the 2nd one is the same except /universe instead of /main.  Any help out there?
It seems you have the wrong url. These ones exist:-
archive.ubuntu.com/ubuntu/dists/karmic/main/binary-i386/Packages.gz
archive.ubuntu.com/ubuntu/dists/karmic/universe/binary-i386/Packages.gz

You will have to update before upgrading.

---

### Post by gwilkins82 on 2010-04-30
> **stoneage said:**
> It seems you have the wrong url. These ones exist:-
archive.ubuntu.com/ubuntu/dists/karmic/main/binary-i386/Packages.gz
archive.ubuntu.com/ubuntu/dists/karmic/universe/binary-i386/Packages.gz

You will have to update before upgrading.

My problem is that I do not see in my sources list where anything with i-386 is.  I'll copy the list below:

# deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)]/ karmic main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic restricted main universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates restricted main universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-security restricted main universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-security restricted
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-security multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-security multiverse
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) karmic free non-free
deb [http://ppa.launchpad.net/banshee-team/ubuntu](http://ppa.launchpad.net/banshee-team/ubuntu) karmic main
deb [http://ppa.launchpad.net/c-korn/ubuntu](http://ppa.launchpad.net/c-korn/ubuntu) karmic main
deb [http://ppa.launchpad.net/deluge-team/ubuntu](http://ppa.launchpad.net/deluge-team/ubuntu) karmic main
deb [http://ftp.osuosl.org/pub/pculture.org/miro/linux/repositories/ubuntu](http://ftp.osuosl.org/pub/pculture.org/miro/linux/repositories/ubuntu) karmic/
deb [http://ppa.launchpad.net/jre-phoenix/ppa/ubuntu](http://ppa.launchpad.net/jre-phoenix/ppa/ubuntu) karmic main
deb-src [http://ppa.launchpad.net/jre-phoenix/ppa/ubuntu](http://ppa.launchpad.net/jre-phoenix/ppa/ubuntu) karmic main
deb [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic main universe
deb-src [http://ppa.launchpad.net/jason-scheunemann/ppa/ubuntu](http://ppa.launchpad.net/jason-scheunemann/ppa/ubuntu) karmic main

---

### Post by Paqman on 2010-04-30
> **Automat2 said:**
> How do I know whether I am using 64-bit or 32-bit?


You have 32-bit. 

> 
If I have the 32-bit, can I change it to the 64-bit?


Not without reinstalling, no.

---

### Post by Automat2 on 2010-04-30
Thanks paqman. If I reinstall, does it have to be a clean one from scratch?

PS: Anyhow, how did you know I am using a 32-bit?

---

### Post by jrandolph on 2010-04-30
> **Automat2 said:**
> Thanks paqman. If I reinstall, does it have to be a clean one from scratch?

PS: Anyhow, how did you know I am using a 32-bit?

It would definitely have to be from scratch - IMHO there isnt really much that 64bit can do that 32bit cant - memory is the only big one that comes to mind 
My box has 64bit capabilities but I am running 32 and have been since the first install of Ubuntu a while back
hope that helps

---

### Post by Automat2 on 2010-04-30
> **jrandolph said:**
> It would definitely have to be from scratch - IMHO there isnt really much that 64bit can do that 32bit cant - memory is the only big one that comes to mind 
My box has 64bit capabilities but I am running 32 and have been since the first install of Ubuntu a while back
hope that helps
Thanks a lot. I don't think I am the only one who wants to save passwords, bookmarks, preferences...

---

### Post by jrandolph on 2010-04-30
> **Automat2 said:**
> Thanks a lot. I don't think I am the only one who wants to save passwords, bookmarks, preferences...

I agree with that - but there is ways to do a fresh install and still be able to reload all those things - im definitely not the guy to ask 
but its for sure worth looking into - mostly because I am a big fan of a fresh install and there is alot of people that will agree

---

### Post by vaslat29 on 2010-04-30
Hi! When I try to upgrade from 9.10 to 10.04 through the Update Manager, I get an error of unauthenticated  packages and takes me out of the upgrade process by reverting back to the original installation - what do i do.

---

### Post by Automat2 on 2010-04-30
> **jrandolph said:**
>  I am a big fan of a fresh install and there is alot of people that will agree
Of course, mate. Every option has its pros and cons, though.

---

### Post by stoneage on 2010-04-30
> **gwilkins82 said:**
> My problem is that I do not see in my sources list where anything with i-386 is.  I'll copy the list below:


deb [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic main universe


I think this is your main/universe source:-

deb [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic main universe

Try changing it to read
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic main universe

---

### Post by jrandolph on 2010-04-30
> **vaslat29 said:**
> Hi! When I try to upgrade from 9.10 to 10.04 through the Update Manager, I get an error of unauthenticated  packages and takes me out of the upgrade process by reverting back to the original installation - what do i do.


this could be caused by the servers being backed up do to others upgrading as well - try again later

---

### Post by Paqman on 2010-04-30
> **jrandolph said:**
> IMHO there isnt really much that 64bit can do that 32bit cant

It's not that 64-bit does anything different, it just does some things a lot faster. Any computationally intensive task like video encoding will show a hefty speed improvement.

---

### Post by jrandolph on 2010-04-30
> **Paqman said:**
> It's not that 64-bit does anything different, it just does some things a lot faster. Any computationally intensive task like video encoding will show a hefty speed improvement.

completely agree with you there - but for the "average" end-user there wouldnt be a very big difference 
by average I mean someone who has the computer for web, email, text related activities
I have another box that runs 64 but its also quite "suped up"

---

