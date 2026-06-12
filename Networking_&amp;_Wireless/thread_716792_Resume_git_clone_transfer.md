---
title: "Resume git clone transfer?"
date: 2008-03-06
forum: Networking &amp; Wireless
---

### Post by der_vegi on 2008-03-06
Hi!

I would like to download the kernel-git with
```
 git clone git://git.kernel.org/pub/scm/linux/kernel/git/torvalds/linux-2.6.git
```
, but I am behind a quite restrictive proxy, so that doesn't work. Sometimes, I have the ability to connect to a less restrictive network, but the connection there is slow and I cannot stay there for hours and hours in one run. Is there a possibility to resume a git-clone transfer?

Thanks for the help!

---

### Post by alexrudd on 2008-03-30
I'm sorry to say this is not yet possible.  I found the following on the [git GSoC](http://git.or.cz/gitwiki/SoC2008Ideas#head-bcfe9e77ab9670575d242059ce3bedacd7f73126) page:
> Restartable Clone

When cloning a large repository (such as KDE, Open Office, Linux kernel) there is currently no way to restart an interrupted clone. It may take considerable time for a user on the end of a small pipe to download the data, and if the clone is interrupted in the middle the user currently needs to start over from the beginning and try again. For some users this may make it impossible to clone a large repository.

Goal: Allow git-clone to automatically resume a previously failed download over the native git:// protocol.
Language: C
Mentor: Shawn Pearce <email removed>
Suggested by: Shawn Pearce on gmane

---

