---
title: "Ubuntu's grub does not recognise (encrypted) lvm partitions"
date: 2011-01-22
forum: New to Ubuntu
---

### Post by saivinoba on 2011-01-22
Hi all,
I have kubuntu, slackware and fedora multibooting. fedora is installed on lvm partition and is also encrypted with luks. Kubuntu recognises slackware but does not recognise fedora.

I have installed lvm2 and cryptsetup. (rebooted system after lvm2 installation, just to add) I used luksOpen and mounted fedora partition just so the grub sees it. but grub is blind to lvm.

What can be done? I need to be able to boot fedora also.

---

