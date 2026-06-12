---
title: "Can't update"
date: 2010-02-25
forum: New to Ubuntu
---

### Post by aliov_85 on 2010-02-25
Hi, 

I've some problems while updating.
sudo apt-get update returns:
> 
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://ir.archive.ubuntu.com](http://ir.archive.ubuntu.com) karmic-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: Failed to fetch [http://ir.archive.ubuntu.com/ubuntu/dists/karmic-updates/Release](http://ir.archive.ubuntu.com/ubuntu/dists/karmic-updates/Release)  

W: Some index files failed to download, they have been ignored, or old ones used instead.


Here is the source.list:
> 
#deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.2)]/ karmic main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://ir.archive.ubuntu.com/ubuntu/](http://ir.archive.ubuntu.com/ubuntu/) karmic main restricted
deb-src [http://ir.archive.ubuntu.com/ubuntu/](http://ir.archive.ubuntu.com/ubuntu/) karmic main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ir.archive.ubuntu.com/ubuntu/](http://ir.archive.ubuntu.com/ubuntu/) karmic-updates main restricted
deb-src [http://ir.archive.ubuntu.com/ubuntu/](http://ir.archive.ubuntu.com/ubuntu/) karmic-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://ir.archive.ubuntu.com/ubuntu/](http://ir.archive.ubuntu.com/ubuntu/) karmic universe
deb-src [http://ir.archive.ubuntu.com/ubuntu/](http://ir.archive.ubuntu.com/ubuntu/) karmic universe
deb [http://ir.archive.ubuntu.com/ubuntu/](http://ir.archive.ubuntu.com/ubuntu/) karmic-updates universe
deb-src [http://ir.archive.ubuntu.com/ubuntu/](http://ir.archive.ubuntu.com/ubuntu/) karmic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://ir.archive.ubuntu.com/ubuntu/](http://ir.archive.ubuntu.com/ubuntu/) karmic multiverse
deb-src [http://ir.archive.ubuntu.com/ubuntu/](http://ir.archive.ubuntu.com/ubuntu/) karmic multiverse
deb [http://ir.archive.ubuntu.com/ubuntu/](http://ir.archive.ubuntu.com/ubuntu/) karmic-updates multiverse
deb-src [http://ir.archive.ubuntu.com/ubuntu/](http://ir.archive.ubuntu.com/ubuntu/) karmic-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://ir.archive.ubuntu.com/ubuntu/](http://ir.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse
# deb-src [http://ir.archive.ubuntu.com/ubuntu/](http://ir.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security multiverse


How should I fix that? 

Best Regards

---

### Post by Kakers on 2010-02-25
Try this:
```
sudo apt-get clean
cd /var/lib/apt
mv lists lists.old
mkdir -p lists/partial
apt-get clean
apt-get update

```

---

### Post by aliov_85 on 2010-02-25
Thanks for your reply.

Now I get the following error:

> 
W: GPG error: [http://ir.archive.ubuntu.com](http://ir.archive.ubuntu.com) karmic-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>


---

### Post by Kakers on 2010-02-25
Humm...

Go to System > Administration > Software Sources
Click the Authentication tab and then the 'Restore Defaults' button
Open up a terminal - sudo apt-get clean

---

### Post by oldos2er on 2010-02-25
> **aliov_85 said:**
> Thanks for your reply.

Now I get the following error:

Try ```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 40976EAF437D05B5
```

---

