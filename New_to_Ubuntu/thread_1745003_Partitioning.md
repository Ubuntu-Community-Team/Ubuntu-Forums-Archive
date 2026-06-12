---
title: "Partitioning"
date: 2011-04-30
forum: New to Ubuntu
---

### Post by blairm on 2011-04-30
Hi,

Have installed Natty with a separate home partition and a 12gb root partition with 4gb swap; how would I go about installing Fedora as well? Would I be better to resize the home partition or the root partition to make space for it? Would like Fedora to make use of the existing /home.

Cheers,

Blair

---

### Post by mr_luksom on 2011-05-01
It would probably be better to resize your /home if you can spare the space, as a future proof buffer.

Having said that, I'm only using about 2GB of my / partition, after allow 25GB.... So knock yourself out!

---

### Post by Elfy on 2011-05-01
If you want fedora to make use of the /home you'll need to look into uid's. Fedora and ubuntu do not use the same default uid.

Personally I'd say that if you're going to start looking at different OS's and sharing data then seperate data partitions and either symlinks or mounting in fstab would be better. Still need to look at uid's though.

It does though I guess depend on what space you have available.

---

### Post by srs5694 on 2011-05-01
> **forestpiskie said:**
> Personally I'd say that if you're going to start looking at different OS's and sharing data then seperate data partitions and either symlinks or mounting in fstab would be better.

I disagree. It's advisable to create separate *user* home directories within the /home partition for each distribution (say, /home/blairm for Ubuntu and /home/blairm-fed for Fedora), but creating a shared-data partition for use between Linux distributions is redundant and limiting. It's redundant because /home is designed to hold different users' home partitions, and whether those are different people with accounts on a single distribution or the same person with accounts on different distributions is irrelevant. It's limiting because if you go with a separate data partition, you must decide on the sizes of /home and the data partition, and if you judge your needs incorrectly you'll have to employ some sort of workaround or fix, which could take time or even be risky.

---

### Post by Elfy on 2011-05-02
> **srs5694 said:**
> I disagree. It's advisable to create separate *user* home directories within the /home partition for each distribution (say, /home/blairm for Ubuntu and /home/blairm-fed for Fedora), but creating a shared-data partition for use between Linux distributions is redundant and limiting. It's redundant because /home is designed to hold different users' home partitions, and whether those are different people with accounts on a single distribution or the same person with accounts on different distributions is irrelevant. It's limiting because if you go with a separate data partition, you must decide on the sizes of /home and the data partition, and if you judge your needs incorrectly you'll have to employ some sort of workaround or fix, which could take time or even be risky.
Good points :)

---

