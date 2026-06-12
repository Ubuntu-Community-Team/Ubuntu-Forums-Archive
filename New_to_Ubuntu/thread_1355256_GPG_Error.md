---
title: "GPG Error"
date: 2009-12-14
forum: New to Ubuntu
---

### Post by barnaclebill18 on 2009-12-14
Hello,

For about ten days I have a notification icon for updates and when I run the Update Manager, I get this error message. I have been Googling and searching this site, but can not figure out how to fix it.

GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 5A9BF3BB4E5E17B5Failed to fetch [http://security.ubuntu.com/ubuntu/dists/karmic-security/Release](http://security.ubuntu.com/ubuntu/dists/karmic-security/Release)  Unable to find expected entry  multiversedeb-src/source/Sources in Meta-index file (malformed Release file?)

Could someone point me in the right direction?

Thanks in advance.

---

### Post by Geoff918 on 2009-12-14
It looks like you have some PPA (personal package archive) listed in your "other software sources" (if you're using the Graphical Version of sources.list).

You can uncheck the check box or delete the location. That should clear itself up.

What you're basically seeing is an "unsigned" archive of something. Which means there's no public shared key by which to identify the authenticity of the server. (That might be Greek, don't worry about it if it is)

*******

EDIT: Is your connection to the internet good? No proxy servers, etc.? I get that message when my g/f's public Wi-Fi needs to be authenticated before use.

---

### Post by drs305 on 2009-12-14
You can add the public key for the first message by running the following command - except it appears from your sig you are running Karmic and this is a repository for jaunty. More likely you want to remove this entry from /etc/apt/sources.list. 
```

gpg --keyserver keyserver.ubuntu.com --recv-keys 4E5E17B5 && gpg --export --armor 4E5E17B5 | sudo apt-key add - 

```

For the second, you have an error in /etc/apt/sources.list

You can edit it if you are familiar with sources.list formats with the following command or post the contents and we can help you out.
```

gksudo gedit /etc/apt/sources.list

```

---

### Post by barnaclebill18 on 2009-12-14
Hello Dave,

I am still here, trying to learn, thanks for the reply.

The first part of your reply, I think you are right and I should remove the Jaunty entry, is this what I should remove?

```
gpg --keyserver keyserver.ubuntu.com --recv-keys 4E5E17B5 && gpg --export --armor 4E5E17B5 | sudo apt-key add -
```

Here is the results of the last command.
```

deb http://ppa.launchpad.net/chromium-daily/ppa/ubuntu jaunty main #deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)]/ karmic main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://astromirror.uchicago.edu/ubuntu/ karmic main restricted
deb-src http://astromirror.uchicago.edu/ubuntu/ karmic main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://astromirror.uchicago.edu/ubuntu/ karmic-updates main restricted
deb-src http://astromirror.uchicago.edu/ubuntu/ karmic-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://astromirror.uchicago.edu/ubuntu/ karmic universe
deb-src http://astromirror.uchicago.edu/ubuntu/ karmic universe
deb http://astromirror.uchicago.edu/ubuntu/ karmic-updates universe
deb-src http://astromirror.uchicago.edu/ubuntu/ karmic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://astromirror.uchicago.edu/ubuntu/ karmic multiverse
deb-src http://astromirror.uchicago.edu/ubuntu/ karmic multiverse
deb http://astromirror.uchicago.edu/ubuntu/ karmic-updates multiverse
deb-src http://astromirror.uchicago.edu/ubuntu/ karmic-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ karmic-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ karmic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu karmic partner
# deb-src http://archive.canonical.com/ubuntu karmic partner

deb http://astromirror.uchicago.edu/ubuntu/ karmic-security main restricted
deb-src http://astromirror.uchicago.edu/ubuntu/ karmic-security main restricted
deb http://astromirror.uchicago.edu/ubuntu/ karmic-security universe
deb-src http://astromirror.uchicago.edu/ubuntu/ karmic-security universe
deb http://astromirror.uchicago.edu/ubuntu/ karmic-security multiverse
deb-src http://astromirror.uchicago.edu/ubuntu/ karmic-security multiversedeb-src http://ppa.launchpad.net/chromium-daily/ppa/ubuntu jaunty
```

---

### Post by plucky on 2009-12-15
```
deb http://ppa.launchpad.net/chromium-daily/ppa/ubuntu jaunty main
```

Delete this line from your sources.list using the ```
gksudo gedit /etc/apt/sources.list
``` command and then run ```
sudo apt-get update
``` in the terminal.Or just put a # in front of that line and again run "sudo apt-get update"


Good Luck

---

### Post by barnaclebill18 on 2009-12-15
Hello plucky,

A quick question, do you put a space after # when commenting out an entry?

---

### Post by bilalakhtar on 2009-12-15
> Hello plucky,

A quick question, do you put a space after # when commenting out an entry? 
Whether you put a space after # or not, it doesnt matter at all.

---

### Post by barnaclebill18 on 2009-12-15
Thank you.

---

