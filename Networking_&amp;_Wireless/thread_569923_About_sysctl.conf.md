---
title: "About sysctl.conf"
date: 2007-10-07
forum: Networking &amp; Wireless
---

### Post by frankabel on 2007-10-07
Hi all,

At [http://changelogs.ubuntu.com/changelogs/pool/main/n/netbase/netbase_4.29ubuntu2/changelog](http://changelogs.ubuntu.com/changelogs/pool/main/n/netbase/netbase_4.29ubuntu2/changelog) you can see:

netbase (4.29ubuntu1) gutsy; urgency=low

  * Merge from debian unstable, remaining changes:
    - added dependency to update-inetd to ensure smooth upgrade for
      packages that use update-inetd in their maintainer scripts (LP#96286)
    - drop dependency on inet superserver
    - drop /etc/network/options, migrate to sysctl
    - start networking only once

 -- Michael Vogt <michael.vogt@ubuntu.com>  Mon, 14 May 2007 11:24:39 +0200


Then I must continue putting the networking kernel tunning in &#8220;/etc/network/options&#8221; as say &#8220;/usr/share/doc/procps/examples/sysctl.conf&#8221; to avoid that &#8220;/etc/init.d/networking&#8221; sets some network options with builting values and overwrite what I put on &#8220;/etc/sysctl.conf&#8221;? I right?

In case of yes...where can I found the variable that &#8220;/etc/init.d/networking&#8221; script can overwrite to it default values from the &#8220;/etc/sysctl.conf&#8221; values?


Thanks in advance.

Salute
Frank Abel

---

