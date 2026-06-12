---
title: "Massive Clusters"
date: 2007-08-07
forum: Networking &amp; Wireless
---

### Post by NonPermissive on 2007-08-07
I had an idea to make my entire school's network (100+ computers) into one giant, massive, throbbing cluster, and I was wondering what problems might be presented with this (I heard something about needing a supercomputer to allocate all the resources). I really just wanted to know if this is practical.

---

### Post by saphid on 2007-08-07
There are a few different methods of doing this I'd use a live or network boot to do it. Look up

Open Mosix or Cluster Knoppix

If you google for it you'll find that people have events where you bring your computers in to a big hall and  hook them up to a live boot cluster for a weekend to do mass processing. 

Hope that helped at all.

Best of luck

---

### Post by NonPermissive on 2007-08-07
Thanks, at least I know it's possible.

Another thing, my school is a Windows school, is there any way to do this on Windows (blech!)?

---

### Post by tutomlin on 2007-08-10
Well if you look up the clusterknoppix distribution that Saphid mentioned, you'll find that it's live cd based, so you can walk around and boot all the computers from the cd then get them crunching once you've got the head node set up.

If you want to just run some sort of clustering software in the background and let people keep using the computers as workstations at the same time I think you are out of luck for free solutions.  I think there are some java based grid computing solutions that can add any computer running the java virtual machine to the grid, but these are pretty much all proprietary to my knowledge.

Just curious, what do you want to do with this cluster-o-doom?  I've got a bunch of computers at home and I just can't think of a compelling use for a cluster to justify the electricity bill for running them all.

Cheers.

Tucker

---

