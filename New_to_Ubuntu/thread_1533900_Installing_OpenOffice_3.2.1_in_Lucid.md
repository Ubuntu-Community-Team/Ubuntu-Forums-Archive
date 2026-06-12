---
title: "Installing OpenOffice 3.2.1 in Lucid"
date: 2010-07-18
forum: New to Ubuntu
---

### Post by Norm24 on 2010-07-18
So far no luck doing so.Any ideas?

---

### Post by s.fox on 2010-07-18
Hello,

I would follow [this]("http://tutorial.downloadatoz.com/install-and-update-openoffice-3-2-1-in-ubuntu.html") guide.  If you have any troubles please post back.

-Silver Fox

---

### Post by Norm24 on 2010-07-18
Gonna stay away from upgrading for now per advice given in another thread.But I do appreciate your response.

---

### Post by VastOne on 2010-07-18
> **s.fox said:**
> Hello,

I would follow [this]("http://tutorial.downloadatoz.com/install-and-update-openoffice-3-2-1-in-ubuntu.html") guide.  If you have any troubles please post back.

-Silver Fox

I get the following error following this guide

```
404

W: Failed to fetch http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu/dists/lucid/main/binary-amd64/Packages.gz  404  Not Found
```

and I think it may be due to there not being a package for 64 bit  for 3.2.1 yet.

I can not confirm this but it is what it looks like

---

### Post by dburnet1 on 2010-07-26
Actually, I got the same error on a 32-bit platform.  So, it doesn't appear to be limited to 64-bit.  No joy.  :(

Anybody else have any luck by chance?

  - - Dave

---

### Post by jtarin on 2010-07-26
The Ubuntu concept is that once a flavor is released, there is no update for its content, except security issues. Therefore, once you stick to a flavor (Dapper, Edgy, Feisty, ...), your OOo version is not updated. Basic reason is : integration has been validated with this package, a new one could mess the system.But Ubuntu releases of OOo are known to be rather bugged, especially the Feisty one. From 2.3, OOo is also available in .deb format, no need to convert the packages with alien as before.

[Here is an installation method for all Debian-based distros :]("http://wiki.services.openoffice.org/wiki/Documentation/How_Tos/Installing_on_Debian_based_Distros")

---

### Post by BigMeanMikeRich on 2010-07-26
> **VastOne said:**
> I get the following error following this guide

```
404

W: Failed to fetch http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu/dists/lucid/main/binary-amd64/Packages.gz  404  Not Found
```

and I think it may be due to there not being a package for 64 bit  for 3.2.1 yet.

I can not confirm this but it is what it looks like

The repository has been returning 404 errors for about a week now, maybe longer (I just added it to grab OoO 3.2.1 when it came out).  I emailed the PPA maintainer, still haven't heard anything back :neutral:

With luck the respository will be working correctly soon, until then I'd disable it in your sources list so that the update manager can get properly updated package information.  If I happen to check the repo and find it working, I'll post back here.  Until then, you may just have to install the .deb package at openoffice.org

---

