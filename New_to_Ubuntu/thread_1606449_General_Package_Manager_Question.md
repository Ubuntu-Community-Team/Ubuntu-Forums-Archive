---
title: "General Package Manager Question"
date: 2010-10-26
forum: New to Ubuntu
---

### Post by CombinedEffort on 2010-10-26
Hi,

I'm new to Ubuntu, although I've used Gentoo / LFS for about 10 years.

I had a general question as to how apt-get and the version of Ubuntu work together to decide what version of a package can be installed. 

It appears a version of Ubuntu (say 10.04) is 'locked' to particular version of a package (mythtv (0.23.0+fixes24158-0ubuntu2)). Would I be right in thinking you can't install a newer version (mythtv (0.23.1+fixes26437-0ubuntu1)) without upgrading the whole server to 10.10? Or does it depend on the repo you're using?

Cheers,

Rich

---

### Post by CombinedEffort on 2010-11-07
(Cross-posted from [Installation &  Upgrades]("http://ubuntuforums.org/forumdisplay.php?f=333"), since no responses there after > 1 week)

Hi,

I'm new to Ubuntu, although I've used Gentoo / LFS for about 10 years.

I had a general question as to how apt-get and the version of Ubuntu  work together to decide what version of a package can be installed. 

It appears a version of Ubuntu (say 10.04) is 'locked' to major  version of a package (mythtv (0.23.0+fixes24158-0ubuntu2)). Would I be  right in thinking you can't install a newer version (mythtv  (0.23.1+fixes26437-0ubuntu1)) without upgrading the whole server to  10.10? Or does it depend on the repo you're using?

Cheers,

Rich

---

### Post by AngusH on 2010-11-07
Hi, the package managers get the software they install from repos. When you do a default install of ubuntu it comes with 4 repos enabled (for 4 different categories of software). As a general policy canonical do not do major updates to the software in the repos (only security updates and the like) so as to maintain stability.
Neither ubuntu or apt-get are actually "locked" to a particular version, that's just the version that's available to apt. When you do an upgrade it switches the repos over to a new set of 4 which will have more up to date software in.
If you want to get your hands on more up to date software all you need to do is find another source. This can be done either by using a different install mechanism (a .deb file or a .tar.gz) or more likely through using a different repo. For example Launchpad allows anyone to create a repo using it's PPA system.

I'm a little tired so if anything up there ^^ doesn't make sense just tell me and I'll explain.
Regards
Angus

---

### Post by uRock on 2010-11-07
They have separate servers for each release. The maintainers decide which versions go onto the servers. apt-get finds the new packages when it checks for updates.

In the future, bump the thread after 24 hours if it goes unanswered instead of creating a new thread.

Threads merged.

---

