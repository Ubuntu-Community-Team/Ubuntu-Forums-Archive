---
title: "error upgrading from 8.04LTS to 10.04"
date: 2010-07-17
forum: New to Ubuntu
---

### Post by AndyInNYC on 2010-07-17
upgraded from 7.1 to 8.04 (no problem)
tried to upgrade from 8.04 to 10.04 following directions for the distribution upgrade.

My 8.04 was fully updated/patched.

Received, after download of all files, the message:

Could not install the upgrades
error during commit
'E:couldn't configure pre-depend for jre for openoffice.org-writer2latex, probably a dependency cycle,'
restoring original system state.

is there a way around this error to get 10.04 upgraded onto my system?

Andrew

---

### Post by DieB on 2010-07-17
> **AndyInNYC said:**
> 
'E:couldn't configure pre-depend for jre for openoffice.org-writer2latex, probably a dependency cycle,'
Andrew

In my readings of this Error, I would recommend to deinstall that above mentioned package, named openoffice.org-writer2latex. (you can do this via Synaptic Package Manager, or via
```
sudo apt-get remove openoffice.org-writer2latex
```

Pls try the upgrade afterwards again and report any success.

---

### Post by Kellemora on 2010-07-17
I'm going to wait until 8.04 expires before I try 10.04 again.

It wouldn't load on one machine at all, on another it loaded but wouldn't run.

So I decided to wait for them to get the bugs out of it.
I thought the purpose of all the intermediate releases were to get the bugs out before they released an LTS version.  Guess I was wrong!

TTUL
Gary

---

### Post by bodhi.zazen on 2010-07-17
> **AndyInNYC said:**
> upgraded from 7.1 to 8.04 (no problem)
tried to upgrade from 8.04 to 10.04 following directions for the distribution upgrade.

My 8.04 was fully updated/patched.

Received, after download of all files, the message:

Could not install the upgrades
error during commit
'E:couldn't configure pre-depend for jre for openoffice.org-writer2latex, probably a dependency cycle,'
restoring original system state.

is there a way around this error to get 10.04 upgraded onto my system?

Andrew

> **Kellemora said:**
> I'm going to wait until 8.04 expires before I try 10.04 again.

It wouldn't load on one machine at all, on another it loaded but wouldn't run.

So I decided to wait for them to get the bugs out of it.
I thought the purpose of all the intermediate releases were to get the bugs out before they released an LTS version.  Guess I was wrong!

TTUL
Gary

From the release announcement :

[https://lists.ubuntu.com/archives/ubuntu-announce/2010-April/000133.html](https://lists.ubuntu.com/archives/ubuntu-announce/2010-April/000133.html)

> 
Users of Ubuntu 8.04 LTS may wish to wait for 10.04.1 LTS, due in July 2010,
before upgrading.

---

### Post by AndyInNYC on 2010-07-19
OK, removed the package (message indicated that I would be *adding* to the used disk space).

Upgrade then went through with a variety of error messages, but the system is running 10.04 (desktop) and seems stable.

Thanks for the help.

Andrew

---

