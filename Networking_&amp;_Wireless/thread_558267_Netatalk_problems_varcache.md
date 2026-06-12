---
title: "Netatalk problems var/cache"
date: 2007-09-23
forum: Networking &amp; Wireless
---

### Post by pinkpanther_bc on 2007-09-23
E: /var/cache/apt/archives/netatalk_2.0.3-6ubuntu1_i386.deb: subprocess new pre-removal script returned error exit status 1 this is the message, I would apreciate any help to solve this problem it has been going on since upgrade to Feisty now run Gustsy
frank@frank-laptop:~$ sudo dpkg --configure -a
[sudo] password for frank:
dpkg: error processing netatalk (--configure):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting configuration.
Errors were encountered while processing:
 netatalk
Cannot reinstall

---

### Post by Cheesehead on 2007-11-13
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/netatalk/+bug/158076](https://bugs.launchpad.net/ubuntu/+source/netatalk/+bug/158076) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				See [https://bugs.launchpad.net/ubuntu/+source/netatalk/+bug/158076](https://bugs.launchpad.net/ubuntu/+source/netatalk/+bug/158076)

I fixed my package by changing two files:

/etc/default/netatalk
FROM: ATALK_NAME=`/bin/hostname --short`
TO: ATALK_NAME=`/bin/hostname`

/etc/init.d/netatalk
FROM: ATALK_NAME=`/bin/hostname --short`
TO: ATALK_NAME=`/bin/hostname`

After the changes, seems to work normally: (Hooray!)

---

