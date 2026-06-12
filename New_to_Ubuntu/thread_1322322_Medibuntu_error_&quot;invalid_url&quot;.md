---
title: "Medibuntu error &quot;invalid url&quot;"
date: 2009-11-10
forum: New to Ubuntu
---

### Post by Mark_in_Hollywood on 2009-11-10
Clean install of Karmic. All updates performed. While installing ANY Medibuntu package, the following comes on screen:

"Invalid url: 'apt://googleearth/' given, exiting

it does not matter which package I click, all return the Invalid url error.

I've quadruplechecked the install as given at:

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

that being:

sudo wget http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list \
 --output-document=/etc/apt/sources.list.d/medibuntu.list &&
sudo apt-get -q update &&
sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring &&
sudo apt-get -q update

and all I get is the same error message.

Looking at the System/Admin/Software Sources/Other Software I see:
Medibuntu-Ubuntu 9.10 "karmic koala" free non-free

and the same line with (source) after it.

Netsearching for "invalid url", medibuntu, karmic shows nothing useful.

---

### Post by marshmallow1304 on 2009-11-10
> **Mark_in_Hollywood said:**
> "Invalid url: 'apt://googleearth/' given, exiting'

You've added a trailing slash.  It should be
```
apt://googleearth
```


Any reason you didn't try Synaptic, apt-get, aptitude, etc.?

---

### Post by Mark_in_Hollywood on 2009-11-10
No, I have not added a 

/

See screenshot attached.

Synaptic pkg. mgr, apt-get, aptitude all fail to install the medibuntu packages.

---

