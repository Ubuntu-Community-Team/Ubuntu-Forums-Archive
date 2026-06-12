---
title: "step by step removal of packagekit 9.04"
date: 2010-09-13
forum: New to Ubuntu
---

### Post by thatguy7669 on 2010-09-13
hi there,
my puter froze last night.eventually it got back on track(after 3 hours),but now all of the package management caches are corrupted and none of them will open.apt-get update/apt-get upgrade/apt-cache gencaches all return segmentation fault...0%.aptitude says it's dying and synaptic and add/remove aren't willing to open at all.package kit is waiting for other processes and since it was last installed it's first to go:D. can somebody give me a file by file instruction guide on how to remove it manually?it'd be highly appreciated.
thanks in advance,thatguy

---

### Post by viralmeme on 2010-09-13
> **thatguy7669 said:**
> all of the package management caches are corrupted

Try the solution here: [apt-get update segmentation fault]("http://ubuntuforums.org/showthread.php?t=773787")

---

### Post by thatguy7669 on 2010-09-13
> **viralmeme said:**
> Try the solution here: [apt-get update segmentation fault]("http://ubuntuforums.org/showthread.php?t=773787")
dude,you rock!!!
thanx for the quick reply,it worked like a charm.
that puts you on my virtual xmas-card mailing list:D
ran into one more problem during updating: my system told me "The backend took too much time to process the synchronous request - you need to fork!"
can you tell me where to stick the fork?
if not i'll find help here somewhere.:D

---

