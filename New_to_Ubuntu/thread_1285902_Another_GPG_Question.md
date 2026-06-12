---
title: "Another GPG Question"
date: 2009-10-08
forum: New to Ubuntu
---

### Post by jmundinger on 2009-10-08
Whether using apt-get, update manager or Synaptic, the procedure includes the following error message:

W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY <key>
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY <key>

I searched the archives on this site and discovered that the following command was the procedure for acquiring keys, so I tried it.

~$ gpg --keyserver subkeys.pgp.net --recv <key>

I tried this a couple of times and the procedure timed out.  I tried it again last night and appeared that I had successfully downloaded both keys.  However, when I run the update procedure, I get the same error regarding the missing keys.  Now, when I run the command line, I get the following message:

gpg: key <key>: "Launchpad PPA for <**>" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1

Any thoughts about what is going on here?  Thanks.

---

### Post by sisco311 on 2009-10-08
[https://launchpad.net/+help/soyuz/ppa-sources-list.html]("https://launchpad.net/+help/soyuz/ppa-sources-list.html")

```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys **<key>**
```

---

### Post by jmundinger on 2009-10-08
Thanks.  That did something, although I'm not sure exactly what.  The following appeared in my Terminal window when attempting to receive both keys:

Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com -- recv-keys <key>
usage: gpg [options] [filename]

And, the same error message appears after running apt-get update.

---

### Post by plucky on 2009-10-08
Please post your **sources.list**.

Open a terminal and use ```
cat /etc/apt/sources.list
``` and copy and paste to the forum.

<key>=GPG key given on the PPA site.

What Launchpad PPA are you trying to access?


Good Luck

---

### Post by jmundinger on 2009-10-09
> **plucky said:**
> Please post your **sources.list**.

Open a terminal and use ```
cat /etc/apt/sources.list
``` and copy and paste to the forum.

<key>=GPG key given on the PPA site.

What Launchpad PPA are you trying to access?


Good Luck

# deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)]/ jaunty main restricted
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
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security multiverse
deb [http://ppa.launchpad.net/mapopa/ppa/ubuntu](http://ppa.launchpad.net/mapopa/ppa/ubuntu) jaunty main
deb-src [http://ppa.launchpad.net/mapopa/ppa/ubuntu](http://ppa.launchpad.net/mapopa/ppa/ubuntu) jaunty main
## Project Bisigi Ubuntu Themes
deb [http://ppa.launchpad.net/bisigi/ppa/ubuntu](http://ppa.launchpad.net/bisigi/ppa/ubuntu) jaunty main
deb-src [http://ppa.launchpad.net/bisigi/ppa/ubuntu](http://ppa.launchpad.net/bisigi/ppa/ubuntu) jaunty main

---

### Post by sisco311 on 2009-10-09
```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 881574DE
```

works for me.

---

### Post by plucky on 2009-10-09
> **sisco311 said:**
> ```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 881574DE
```

works for me.

What about the other PPA ```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys EF648708
```should fix that.

Good Luck

---

### Post by jmundinger on 2009-10-09
> **plucky said:**
> What about the other PPA ```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys EF648708
```should fix that.

Good Luck

I ran that command line, using each of the keys in yours and the previous posts.  In both cases, the resulting application included the following information.

Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com -- recv-keys EF648708
usage: gpg [options] [filename]

And, running apt-get update still results in the error message regarding the keys.

---

### Post by sisco311 on 2009-10-09
try:
```
w3m "http://keyserver.ubuntu.com:11371/pks/lookup?op=get&search=0x6E871C4A881574DE" | sudo apt-key add -
```

and

```
w3m "http://keyserver.ubuntu.com:11371/pks/lookup?op=get&search=0x0BE6D09EEF648708" | sudo apt-key add -
```

or dowload the key files and add the keys via the GUI: 
[http://www.youtube.com/watch?v=UUZOQsNo_ws]("http://www.youtube.com/watch?v=UUZOQsNo_ws")(youtube video)

---

### Post by jmundinger on 2009-10-09
> **sisco311 said:**
> try:
```
w3m "http://keyserver.ubuntu.com:11371/pks/lookup?op=get&search=0x6E871C4A881574DE" | sudo apt-key add -
```and

```
w3m "http://keyserver.ubuntu.com:11371/pks/lookup?op=get&search=0x0BE6D09EEF648708" | sudo apt-key add -
```or dowload the key files and add the keys via the GUI: 
[http://www.youtube.com/watch?v=UUZOQsNo_ws](http://www.youtube.com/watch?v=UUZOQsNo_ws)(youtube video)

Thank you.  I ran the command line twice, just as you suggested, and starting from $, i.e. I did not use sudo for the command that preceded the pipe.  In both cases, the application resulted in "OK".  And, now the error message no longer appears when I run apt-get.

---

### Post by garthcrocker on 2009-10-14
Hi! I'm a newbie and have used the instructions provided by Sarmacid (Aug 20th, 2008) to encrypt some .odt files successfully - and decrypt them, but I want to backup my keys. He says - Go to Keys - Backup key rings but I can't find that option anywhere. Heeelp?

---

