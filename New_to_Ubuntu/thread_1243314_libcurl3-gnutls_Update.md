---
title: "libcurl3-gnutls Update"
date: 2009-08-18
forum: New to Ubuntu
---

### Post by SDR on 2009-08-18
I'm quite new to Ubuntu and Linux in general still and am having a problem with an update.  It's called 'libcurl3-gnutls' and Update Manager describes it as 'Multi-protocol file transfer library (GnuTLS) (Size: 208KB)'.  However, when I try to install it, I get a warning box saying,

'Not enough free disk space

The upgrade needs a total of 63.1M free space on disk '/'. Please free at least an additional 48.3M of disk space on '/'. Empty your trash and remove temporary packages of former installations using 'sudo apt-get clean'.'

How can a 208KB update need 63M of space?   Can anyone help me?

Thank you!!!

---

### Post by zvacet on 2009-08-18
```
sudo apt-get autoremove
sudo apt-get clean
sudo apt-get autoclean

```

---

