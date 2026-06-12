---
title: "What am I doing wrong trying to install LinSSID onto Ubuntu 13.10?"
date: 2013-12-25
forum: Networking &amp; Wireless
---

### Post by Jim_Granite on 2013-12-25
Following [directions provided over here]("http://www.ubuntugeek.com/linssid-graphical-wireless-scanning-for-linux.html") ... I can't seem to install LinSSID onto my stock Ubuntu 13.10 laptop:
```

$ sudo add-apt-repository ppa:wseverin/ppa
$ sudo apt-get update
$ sudo apt-get install linssid

```

**Here's what happens when I run the update command:**
```

$ sudo add-apt-repository ppa:wseverin/ppa
 LinSSID is graphically and functionally similar to iwscanner (Linux) and Inssider (Microsoft&#8482; Windows®). It is written entirely in C++ using Linux wireless tools and Qt4.
 More info: https://launchpad.net/~wseverin/+archive/ppa
Press [ENTER] to continue or ctrl-c to cancel adding it
< at this point I press the ENTER key >
gpg: keyring `/tmp/tmp1el9z5/secring.gpg' created
gpg: keyring `/tmp/tmp1el9z5/pubring.gpg' created
gpg: requesting key 08E6D617 from hkp server keyserver.ubuntu.com
gpg: /tmp/tmp1el9z5/trustdb.gpg: trustdb created
gpg: key 08E6D617: public key "Launchpad PPA for Warren" imported
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
OK

```

**This is what happens when I run the installation command:**
```

... stuff ... 
Err http://ppa.launchpad.net saucy/main amd64 Packages
  404  Not Found
Err http://ppa.launchpad.net saucy/main i386 Packages
  404  Not Found
... stuff ... 
W: Failed to fetch http://ppa.launchpad.net/wseverin/ppa/ubuntu/dists/saucy/main/binary-amd64/Packages  404  Not Found
W: Failed to fetch http://ppa.launchpad.net/wseverin/ppa/ubuntu/dists/saucy/main/binary-i386/Packages  404  Not Found
E: Some index files failed to download. They have been ignored, or old ones used instead.

```

**This is what happens when I run the third of three commands:**
```

$ sudo apt-get install linssid
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package linssid

```

---

### Post by steeldriver on 2013-12-25
you're not doing anything wrong - the ppa currently only contains packages for Precise / Quantal / Raring (not Saucy)

---

### Post by Jim_Granite on 2013-12-28
> **steeldriver said:**
> the ppa currently only contains packages for Precise / Quantal / Raring (not Saucy)

Ah. I see. Thanks.
I'll wait.

---

