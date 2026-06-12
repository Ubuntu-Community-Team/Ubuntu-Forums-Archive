---
title: "Can't update or dload packages but can use web"
date: 2008-12-17
forum: New to Ubuntu
---

### Post by McSwan on 2008-12-17
Hi,

I can't seem to synaptic down packages. 

I try to download zziplib I mark for upgrade and it hangs at 1 of 10 updates. Can't seem to find the server or something.

I went to Software sources and looked for the "best server" and it found none.

I can access the net because I typed in the address of aarnet server in mozilla and it came up fine.

Any ideas on what's going on ??

---

### Post by Tatty on 2008-12-17
what is the output of

```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by McSwan on 2008-12-17
sudo apt-get update
[sudo] password for michael:
0% [Connecting to au.archive.ubuntu.com (91.189.88.46)]

sudo apt-get upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


no luck there . I've triedthe apt-get install zziplib too.

I didn't install this version of ubuntu so it's possible I've been locked out of updates? Any way I can tell ?

---

### Post by adobrakic on 2008-12-17
There does not seem to be any issues.
It just seems like there aren't any updates for you to download.

I don't know what 'zziplib' is, but you may want to try doing:

```

sudo apt-get install libzzip-0-13

```

The description is:

> 
library providing read access on ZIP-archives - library
The zziplib library is intentionally lightweight, it offers the ability
to easily extract data from files archived in a single zip file.
Applications can bundle files into a single zip archive and access them.
The implementation is based only on the (free) subset of compression
with the zlib algorithm which is actually used by the zip/unzip tools.

This package contains the zziplib runtime library.

Canonical does not provide updates for libzzip-0-13. Some updates may be provided by the Ubuntu community.


---

### Post by Tatty on 2008-12-17
> **McSwan said:**
> sudo apt-get update
[sudo] password for michael:
0% [Connecting to au.archive.ubuntu.com (91.189.88.46)]

It seems as though it is struggling to connect to the repo server.  It could be that this particular server is just down at the moment.

Either switch to another server or just wait for it to come back up.

---

