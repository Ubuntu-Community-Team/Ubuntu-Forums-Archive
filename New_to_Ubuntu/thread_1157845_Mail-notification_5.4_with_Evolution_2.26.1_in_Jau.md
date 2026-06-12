---
title: "Mail-notification 5.4 with Evolution 2.26.1 in Jaunty"
date: 2009-05-13
forum: New to Ubuntu
---

### Post by pietro2580 on 2009-05-13
Dear all,

After upgrading to Ubuntu 9.04, the mail-notification software (Jean-Yves lefort) cannot connect anymore with Ubuntu. The message I got is:

Unhandled Evolution Mailbox - Unable to contact evolution.

Does anyone has a solution for this? Even recompiling from the source pacakge does not give any help. The error I got there when running the configure script is:
WARNING: Package evolution-plugin was not found in the pkg-config search path.
WARNING: Perhaps you should add the directory containing `evolution-plugin.pc'
WARNING: to the PKG_CONFIG_PATH environment variable
WARNING: No package 'evolution-plugin' found
WARNING: disabling option "evolution" since Evolution was not found

Anyone else suffering the same problem?

Thanks in advance!

---

### Post by metapaso on 2009-06-03
I had this same problem and the workaround from 

[https://bugs.launchpad.net/ubuntu/+source/mail-notification/+bug/355209](https://bugs.launchpad.net/ubuntu/+source/mail-notification/+bug/355209)

fixed this issue for me.  It seems that the plugin is installed in the wrong place and either copying or linking it to the right folder fixes it.

---

