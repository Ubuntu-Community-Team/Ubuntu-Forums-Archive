---
title: "Simple Home Network Setup"
date: 2008-08-13
forum: Networking &amp; Wireless
---

### Post by raywood on 2008-08-13
I'll appreciate it if someone could kindly point me toward an FAQ on target.  I haven't found one, and I suspect there must be a dozen.

Setup:  two dual-boot machines (64-bit Ubuntu 8.04 and 32-bit Windows XP).  One machine is booted into Ubuntu, the other into WinXP.  Linksys WRT54GL router.  Both machines are cabled to the router, which in turn is cabled to a DSL modem.  Both machines are able to go online.

Question:  what is the easiest secure way to network these two together for purposes of file-sharing?  I say "easiest" because, for some reason, networking uniquely vexes me.

Thanks in advance.

---

### Post by Iowan on 2008-08-14
There are a few options - Samba being the most common.  There's also SSHFS - NFS for unix-unix file transfer.  A couple of guides:
[https://help.ubuntu.com/community/SettingUpSamba]("https://help.ubuntu.com/community/SettingUpSamba")
[http://ubuntuforums.org/showthread.php?t=202605]("http://ubuntuforums.org/showthread.php?t=202605")
[https://help.ubuntu.com/community/SSHFS]("https://help.ubuntu.com/community/SSHFS")

---

