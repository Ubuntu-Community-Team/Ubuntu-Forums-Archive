---
title: "Problems with ncpfs after upgrade to 7.10"
date: 2007-10-23
forum: Networking &amp; Wireless
---

### Post by pholden on 2007-10-23
Since upgrading to Ubuntu 7.10, I've been unable to mount my netware shares at work. I've got an entry in my fstab config file which worked fine prior to the upgrade.

To solve it, I've forced Synaptic to install an older version from edgy:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=47444&stc=1&d=1193154261[/IMG]

This works fine, but ideally I'd like to keep the system up to date. There's a bug report posted [**here**]("https://bugs.launchpad.net/ubuntu/+source/ncpfs/+bug/140464"). Does anyone have a solution to this? The responses in the bug report just recommend downgrading ncpfs, which is what I've done.

([**This post**]("http://ubuntuforums.org/showthread.php?t=553955") was posted 4 weeks ago, and it describes exactly the situation I'm experiencing and error I'm getting.)

---

