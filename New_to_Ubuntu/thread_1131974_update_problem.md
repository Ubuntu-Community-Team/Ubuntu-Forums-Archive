---
title: "update problem"
date: 2009-04-21
forum: New to Ubuntu
---

### Post by mamamia88 on 2009-04-21
i am trying to update my sources.lst and i get this message when trying either apt-get update or aptitude update W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 620396F19C0042C8
W: You may want to run apt-get update to correct these problems

do you think it's related to me adding the chromium ppa yesterday?  and how would i go about fixit it?

---

### Post by amingv on 2009-04-21
See if this helps:

[https://help.launchpad.net/Packaging/PPA#Adding%20a%20PPA%27s%20keys%20to%20your%20system](https://help.launchpad.net/Packaging/PPA#Adding%20a%20PPA%27s%20keys%20to%20your%20system)

with this key

[http://keyserver.ubuntu.com:11371/pks/lookup?op=get&search=0x5A9BF3BB4E5E17B5](http://keyserver.ubuntu.com:11371/pks/lookup?op=get&search=0x5A9BF3BB4E5E17B5)

---

### Post by mamamia88 on 2009-04-21
that key didn't work

---

### Post by philinux on 2009-04-21
Post the output of this.

```
cat /etc/apt/sources.list
```

Dont forget to use code tags around the output.

---

### Post by mamamia88 on 2009-04-21
-------------------------------------------
cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Alpha i386 (20090312)]/ jaunty main restricted
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
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security multiverse
deb [http://ppa.launchpad.net/sargentd/ppa/ubuntu](http://ppa.launchpad.net/sargentd/ppa/ubuntu) jaunty main
deb-src [http://ppa.launchpad.net/sargentd/ppa/ubuntu](http://ppa.launchpad.net/sargentd/ppa/ubuntu) jaunty main
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-proposed restricted main multiverse universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-backports restricted main multiverse universe
deb [http://moblock-deb.sourceforge.net/debian](http://moblock-deb.sourceforge.net/debian) intrepid main
deb [http://ppa.launchpad.net/jre-phoenix/ppa/ubuntu](http://ppa.launchpad.net/jre-phoenix/ppa/ubuntu) jaunty main
deb [http://ppa.launchpad.net/chromium-daily/ppa/ubuntu](http://ppa.launchpad.net/chromium-daily/ppa/ubuntu) jaunty main
deb-src [http://ppa.launchpad.net/chromium-daily/ppa/ubuntu](http://ppa.launchpad.net/chromium-daily/ppa/ubuntu) jaunty main
---------------------------------------------------------
how do i do code tags?

---

### Post by cariboo on 2009-04-21
o to the ppa page and right below the text box with the source location you will see some numbers fro example on the chromium page they are 1024R/4E5E17B5, click on those numbers, you will be taken to another oage click on the link on the left had side and paste the resulting key in System-->Administration-->Software Sources-->Authentication-->Import Key File.

Jim

---

### Post by mamamia88 on 2009-04-21
i already have the chromium key that can't be the problem

---

### Post by mamamia88 on 2009-04-21
anyone?  i removed chromium and that didn't help

---

### Post by jre on 2009-04-22
You miss the key for my PPA (jre-phoenix, MoBlock). My other repository at moblock-deb.sourceforge.net uses another key.

There are many ways to get the new key, one is:
```
gpg --keyserver wwwkeys.eu.pgp.net --recv 9C0042C8
gpg --export --armor 9C0042C8 | sudo apt-key add -
```


> **mamamia88 said:**
> how do i do code tags?
click "Go Advanced", mark the text and then click on the #-Symbol.

---

### Post by manwell77 on 2009-04-27
Your public key doesn't exist:

> root@manwell77:/home/manwell77# gpg --keyserver wwwkeys.eu.pgp.net --recv 9C0042C8
gpg: richiesta della chiave 9C0042C8 dal server hkp wwwkeys.eu.pgp.net
gpgkeys: key 9C0042C8 not found on keyserver
gpg: non sono stati trovati dati OpenPGP validi.
gpg: Numero totale esaminato: 0
root@manwell77:/home/manwell77# 

Even the link there : [https://launchpad.net/~jre-phoenix/+archive/ppa]("https://launchpad.net/~jre-phoenix/+archive/ppa")
isn't working.

---

### Post by jre on 2009-04-27
sorry, I can't confirm that. The key exists on the keyserver and the link works, too.

But I just had the problem, that moblock blocked the keyserver. But stopping moblock fixes that ;-)

You could also use another keyserver, e.g. 
```
gpg --keyserver keyserver.ubuntu.com --recv 9C0042C8
gpg --export --armor 9C0042C8 | sudo apt-key add -
```

---

