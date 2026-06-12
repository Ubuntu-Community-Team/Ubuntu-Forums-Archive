---
title: "cant add ppa"
date: 2010-06-13
forum: New to Ubuntu
---

### Post by nick_goodfate on 2010-06-13
I have tried to add several ppas but i cant. For example i m tring to add galaxium ppa and this is what happen(same for every ppa i have tried lately)
> Sun Jun 13 23:16:13 EEST 2010
~
virusmiurasv@virusmiurasv-laptop: pts/1: 15 files 1.5Gb -> sudo add-apt-repository ppa:galaxium/ppa
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv 356AE8F049D6E4A9B62D52233E0219167854A3A9
gpg: requesting key 7854A3A9 from hkp server keyserver.ubuntu.com
gpg: keyserver timed out
gpg: keyserver receive failed: keyserver error
my internet connection is ok ....

---

### Post by arrange on 2010-06-13
Are you able to connect to the server?```
cd /tmp
wget keyserver.ubuntu.com
```

---

### Post by howefield on 2010-06-13
keyserver.ubuntu.com has been flaky over the last few days, even more so than than usual.

Try swapping "keyserver.ubuntu.com" with "wwwkeys.eu.pgp.net"

Without the quotes.,

eg,

sudo apt-key adv --keyserver wwwkeys.eu.pgp.net --recv-keys F9CB8DB0

Substitute your key ID for F9CB8DB0.

---

