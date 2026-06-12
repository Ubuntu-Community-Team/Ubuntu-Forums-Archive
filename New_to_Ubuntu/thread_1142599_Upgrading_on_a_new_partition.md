---
title: "Upgrading on a new partition"
date: 2009-04-29
forum: New to Ubuntu
---

### Post by Falc7 on 2009-04-29
Hi
Currently using Ipex, thinking about upgrading to Jaunty, but i would also like the new file system. In most of the other threads i've found, people recommend a clean install as they say it can be a pain to get grub to recognise the new file system. So anyway, rather than moving all my data onto an external HB, could i just make a new partition, install Jaunty on that, then move all the files across, then delete Ipex, would that work?

---

### Post by taurus on 2009-04-29
Yes.  Or you could create a separate /home partition.  Then, move your $HOME to that new /home and install Jaunty on /.  Don't forget to mount the partition where /home is but do not format that partition--/home.  (Do format the / partition to ext4 filesystem if that is what you want to use.)

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

