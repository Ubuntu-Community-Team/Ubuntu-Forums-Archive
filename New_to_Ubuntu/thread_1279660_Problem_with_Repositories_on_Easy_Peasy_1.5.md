---
title: "Problem with Repositories on Easy Peasy 1.5"
date: 2009-10-01
forum: New to Ubuntu
---

### Post by louvros10 on 2009-10-01
I just installed Easy Peasy 1.5 on my Asus EEE 701 and when I reload the package information in the synaptic package manager, I get the following error:
```
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: http://ppa.launchpad.net jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 3B22AB97AF1CDFA9

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: http://gr.archive.ubuntu.com jaunty Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: Failed to fetch http://gr.archive.ubuntu.com/ubuntu/dists/jaunty/Release  

W: Failed to fetch http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu/dists/jaunty/Release  

W: Some index files failed to download, they have been ignored, or old ones used instead.

```

I remove the missing signature because in previous error message, it was saying that it was invalid. When I press the restore to default, it doesn't get but on the list of signing keys. 
When I try to add/remove applications, in the applications info, it says that cannot be installed on your computer type (i386). It is the first time that I see such a funny message...!!!
What is the problem with all these signing keys and repositories???

---

### Post by zvacet on 2009-10-01
In applications<accessories>terminal type

```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys AF1CDFA9
```

---

### Post by louvros10 on 2009-10-01
OK...That command adds the key I remove from the trusted software providers.
And I get the original error message:
```
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: http://ppa.launchpad.net jaunty Release: The following signatures were invalid: BADSIG 3B22AB97AF1CDFA9 Launchpad PPA for Ubuntu-X

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: http://gr.archive.ubuntu.com jaunty Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: Failed to fetch http://gr.archive.ubuntu.com/ubuntu/dists/jaunty/Release  

W: Failed to fetch http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu/dists/jaunty/Release  

W: Some index files failed to download, they have been ignored, or old ones used instead.

```

What is wrong???:confused:

---

### Post by louvros10 on 2009-10-01
Does anyone know what might be the problem with repositories...
I cannot install any application...!!!
Please someone help...

---

### Post by LowSky on 2009-10-01
Whoa -- Calm Down!!!

You are not using Ubuntu, you are using a customized 3 party version of Ubuntu which might not work exactly the same, so the errors you are seeing are not caused by normal distro behavior.

Please open a terminal and type this 

```
gedit /etc/apt/sources.list 
``` and please post the results here

---

### Post by louvros10 on 2009-10-01
```
# deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)]/ jaunty main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://gr.archive.ubuntu.com/ubuntu/ jaunty main restricted universe
deb-src http://gr.archive.ubuntu.com/ubuntu/ jaunty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://gr.archive.ubuntu.com/ubuntu/ jaunty-updates main restricted universe
deb-src http://gr.archive.ubuntu.com/ubuntu/ jaunty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Easy Peasy security team.
deb http://gr.archive.ubuntu.com/ubuntu/ jaunty universe
deb-src http://gr.archive.ubuntu.com/ubuntu/ jaunty universe
deb http://gr.archive.ubuntu.com/ubuntu/ jaunty-updates universe
deb-src http://gr.archive.ubuntu.com/ubuntu/ jaunty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Easy Peasy 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://gr.archive.ubuntu.com/ubuntu/ jaunty multiverse
deb-src http://gr.archive.ubuntu.com/ubuntu/ jaunty multiverse
deb http://gr.archive.ubuntu.com/ubuntu/ jaunty-updates multiverse
deb-src http://gr.archive.ubuntu.com/ubuntu/ jaunty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Easy Peasy security team.
# deb http://gr.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse
# deb-src http://gr.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Easy Peasy users.
deb http://archive.canonical.com/ubuntu jaunty partner
deb-src http://archive.canonical.com/ubuntu jaunty partner

deb http://security.ubuntu.com/ubuntu jaunty-security main restricted universe
deb-src http://security.ubuntu.com/ubuntu jaunty-security main restricted
deb http://security.ubuntu.com/ubuntu jaunty-security universe
deb-src http://security.ubuntu.com/ubuntu jaunty-security universe
deb http://security.ubuntu.com/ubuntu jaunty-security multiverse
deb-src http://security.ubuntu.com/ubuntu jaunty-security multiverse

```

---

### Post by mikewhatever on 2009-10-01
There is no problem. Some mirrors might go offline for maintenance or whatever, but there are about 290 other mirror around the world. Open software sources and in the 'Download from' select other, then hit the 'Choose the best derver' button.
To get the best results, it's advisable to close file sharing applications and let it run solo.

---

### Post by louvros10 on 2009-10-01
That seems to work...but I still get error when I reload the package information:
```
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: http://ppa.launchpad.net jaunty Release: The following signatures were invalid: BADSIG 3B22AB97AF1CDFA9 Launchpad PPA for Ubuntu-X

W: Failed to fetch http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu/dists/jaunty/Release  

W: Some index files failed to download, they have been ignored, or old ones used instead.

```

Thanks a lot...btw...nice avatar...!!!:)

---

### Post by mikewhatever on 2009-10-01
The remaining error is related to a third party ppa repository, which is no big deal. You most probably don't need stuff from there all the time, and hopefully it will come back online soon.

---

