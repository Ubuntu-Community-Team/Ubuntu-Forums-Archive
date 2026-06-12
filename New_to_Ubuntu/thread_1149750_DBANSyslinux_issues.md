---
title: "DBAN/Syslinux issues"
date: 2009-05-05
forum: New to Ubuntu
---

### Post by iamshawnrice on 2009-05-05
Hi.

I need to wipe my drive due to some irresponsible partition editing.
My system is highly unstable and will only boot from a usb device.

I am trying to use DBAN, but upon booting from USB, SYSLINUX loads with a 'boot:' prompt.

Typing 'autonuke' per DBAN's instructions produce: ' Could not find kernel image: autonuke'

Any ideas as to what I am doing wrong?

---

### Post by Alterax on 2009-05-06
Probably just a screw up in the build.  Uncommon, but it happens.  Usually I just use DBAN with the dod command (rather than autonuke).  Takes longer as it's a 7-pass rather than a 3-pass, but usually I start them off and let them run overnight.

---

