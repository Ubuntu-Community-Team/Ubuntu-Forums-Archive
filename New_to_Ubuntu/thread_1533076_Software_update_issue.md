---
title: "Software update issue"
date: 2010-07-17
forum: New to Ubuntu
---

### Post by Marceau on 2010-07-17
I sometimes get the red exclamation mark to notify me of an update/issue with update manager.

When I check, I see the following error:

> Could not download all repository indexes

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.


Failed to fetch cdrom://Ubuntu-Netbook 10.04 _Lucid Lynx_ - Release i386 (20100429.4)/dists/jaunty/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom://Ubuntu-Netbook 10.04 _Lucid Lynx_ - Release i386 (20100429.4)/dists/jaunty/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Some index files failed to download, they have been ignored, or old ones used instead.

The thing is, I don't have a CDRom in my sources, and I even went so far as to delete every software source that I had added myself, but I still get this error from time to time.

How can I get rid of this?

---

### Post by wojox on 2010-07-17
Open a terminal:

```
gksudo gedit /etc/apt/sources.list
```

Now look at the very top and you should see a reference to your cd-rom. You want to comment this out with the pound sign (#).

---

### Post by Marceau on 2010-07-17
> **wojox said:**
> Open a terminal:

```
gksudo gedit /etc/apt/sources.list
```Now look at the very top and you should see a reference to your cd-rom. You want to comment this out with the pound sign (#).

Awesome. That's probably it. Thank you.

---

### Post by wojox on 2010-07-18
> **Marceau said:**
> Awesome. That's probably it. Thank you.

Your Welcome.

---

