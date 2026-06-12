---
title: "Update KDE"
date: 2009-01-16
forum: New to Ubuntu
---

### Post by Jynxx on 2009-01-16
How do I go about updating KDE to the newest version?

---

### Post by taurus on 2009-01-16
Which release are you running right now?

```
lsb_release -a
```

---

### Post by snova on 2009-01-16
Newest, as in, 4.2 RC1?

Add this to the end of /etc/apt/sources.list ("gksudo kwrite /etc/apt/sources.list" or whatever editor you prefer):

```
deb http://ppa.launchpad.net/kubuntu-experimental/ubuntu intrepid main
```

Then run:

```
sudo apt-get update
```

This next step will download and install the new KDE. I suggest you not be in KDE while you do this (it was screwy when I did it, though that may have just been me):

```
sudo apt-get upgrade
```

Hopefully this'll do it.

---

### Post by Jynxx on 2009-01-16
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 8.10
Release:        8.10
Codename:       intrepid

---

### Post by snova on 2009-01-16
> **Jynxx said:**
> No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 8.10
Release:        8.10
Codename:       intrepid

It was a good idea to ask what version you were using. Thanks, taurus. ;)

My instructions are what I did a few days ago, and I run Intrepid, so I think you should be fine.

---

