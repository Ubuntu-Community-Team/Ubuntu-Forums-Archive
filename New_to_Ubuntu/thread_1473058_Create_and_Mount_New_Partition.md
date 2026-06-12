---
title: "Create and Mount New Partition"
date: 2010-05-04
forum: New to Ubuntu
---

### Post by cmdrbozo on 2010-05-04
What I want is two volumes, one with the OS and one with data. I thought this would be easy to create, but so far unsuccessful. What's the esasies way to accomplish this?

Installed 10.04 with LVM2 encrypted root cuz I thought this allowed dynamic resizing of partitions, so now I find this is not so and LVM is mostly good for spanning different physical drives. So should I reinstall without it?

Anyhow, I created a 100 GB volume allowing room for a /data volume, the latter was created with system-config-lvm 1.1.11. How do I mount it? "Places" shows "200 GB Encrypted" When I click this I get "Unable to mount... One or more blocks are holding /dev/sda5.

Any documentation on system-config-lvm?

Suggestions?

---

