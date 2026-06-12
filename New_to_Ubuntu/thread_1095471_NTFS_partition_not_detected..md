---
title: "NTFS partition not detected."
date: 2009-03-13
forum: New to Ubuntu
---

### Post by mig96 on 2009-03-13
**Info**

> Using latest 9.04 daily alternate cd/daily live cd.  031309.  x86 because compatibility problems may show up with x64...
> Used to use RAID 0 but had it removed because it was broken.
> nForce 650i motherboard / XPS 630i (Dell) / 2 500GB HD's
> Alternate installer still asks me if "I want to enable RAID devices in disk check."

**Problem(s)**

> When the installer starts to check for disks, both the hard drives SHOW UP but the PARTITIONS INSIDE (500GB Vista on one, 250GB XP and 250GB empty that I want to use for Kubuntu on the other one) do NOT show up.
> On live CD, installer gives error at Partman step: "error 141."

[B]Attempt at solution

[/B]Tried irqpoll and pci=nomsi switches and BOTH of them at SAME TIME at the boot prompt, none work.

---

### Post by martrn on 2009-03-13
1. File a bug report -- [https://bugs.launchpad.net/ubuntu/+source/ubiquity]("https://bugs.launchpad.net/ubuntu/+source/ubiquity")

2. Always use a latest version (not alpha or beta) for production machines from the  Ubuntu [http://www.ubuntu.com/getubuntu/download]("http://www.ubuntu.com/getubuntu/download") The latest version is 8.10 Desktop.

Hopefully it will be fixed before the April 23rd date.

---

