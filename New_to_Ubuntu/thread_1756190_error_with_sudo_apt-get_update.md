---
title: "error with sudo apt-get update"
date: 2011-05-12
forum: New to Ubuntu
---

### Post by jayaknn on 2011-05-12
I am getting this error when executing the following command
sudo apt-get update
Fetched 317B in 3s (106B/s)
Reading package lists... Done
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 0C5CE27EA088FF1E

Please help solve this issue. Because of this issue.
Thanx

---

### Post by bodhi.zazen on 2011-05-12
You can either ignore that message or import the key.

See this page for guidance:

[https://help.launchpad.net/Packaging/PPA/InstallingSoftware](https://help.launchpad.net/Packaging/PPA/InstallingSoftware)

---

### Post by jayaknn on 2011-05-12
Thanks, I tried the command
sudo add-apt-repository ppa:gwibber-daily/ppa-name

I get this error.
Error reading [https://launchpad.net/api/1.0/~gwibber-daily/+archive/ppa-name:]("https://launchpad.net/api/1.0/%7Egwibber-daily/+archive/ppa-name:") HTTP Error 404: Not Found

How do I get the PPA location.

I wanted to install Real player  using this command
sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet updateI got this error
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid/non-free Packages
Fetched 317B in 2s (132B/s)
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 0C5CE27EA088FF1E
W: Failed to fetch [http://ppa.launchpad.net/gwibber-daily/ppa-name/ubuntu/dists/lucid/main/binary-i386/Packages.gz](http://ppa.launchpad.net/gwibber-daily/ppa-name/ubuntu/dists/lucid/main/binary-i386/Packages.gz)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/user/ppa-name/ubuntu/dists/lucid/main/binary-i386/Packages.gz](http://ppa.launchpad.net/user/ppa-name/ubuntu/dists/lucid/main/binary-i386/Packages.gz)  404  Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.

My intention is to get the real player installed in my laptop.

---

### Post by Elfy on 2011-05-12
Try without the -name, however > It is totally untested. Please don't use this PPA if you feel unsure.

[https://launchpad.net/~gwibber-daily/+archive/ppa](https://launchpad.net/~gwibber-daily/+archive/ppa)

```
sudo add-apt-repository ppa:gwibber-daily/ppa
```

---

