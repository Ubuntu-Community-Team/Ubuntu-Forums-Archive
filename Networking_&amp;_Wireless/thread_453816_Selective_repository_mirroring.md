---
title: "Selective repository mirroring"
date: 2007-05-24
forum: Networking &amp; Wireless
---

### Post by sergiodlc on 2007-05-24
Hi:

I work at a large university that is slowly migrating to Ubuntu. We have here a mirror of the official Ubuntu repositories to save internet bandwith. However most of us connect to our intranet from our houses through a 56K modem. This makes virtually impossible to use our repositories at home. I was wondering if there is a way to make a selective copy of the needed packages and transport them in a USB flash memory. For instance, if I'd want to install the libgtk2.0-dev package this would be a mess, since it has a lot of dependencies which, in turn, may have subdependencies. Is there a way to automate the process and download only the needed packages? Maybe there is some wget hacking to achieve this.

Burning the entire repositories in DVD is not an option, since many of us don't have DVD drives.

Please, help me.

Thanks in advance,

Sergio.

---

### Post by spd106 on 2007-05-26
I suggest that you start by investigating the aptoncd project over at sourceforge.net
[http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/)

You can use the -s switch with apt-get to simulate a package install and it will tell you what dependencies are needed for that particular package. There are probably other more advanced ways of retrieving this information.

---

### Post by sergiodlc on 2007-05-30
Yes, aptoncd looks like what I was looking for. It has to be started with the --download option and it can be used to create a local copy of the entire repository. I guess that then you can costomize your own CD repository with aptoncd.

Thanks a lot, pal.

Sergio

---

