---
title: "Jaunty server partitions: opinions?"
date: 2009-06-06
forum: New to Ubuntu
---

### Post by InvisibleMan on 2009-06-06
I'm installing Jaunty server on an old desktop (2.4 GHz, 3 GB RAM, 80 GB HD) that will be a fileserver as part of a domain in a Windows Active Directory LAN. My plan for partitioning is:

100 MB for boot
12 GB for root and var
6 GB for swap
61 GB (the remainder) for home

I would have preferred to have root and var in separate primary partitions, but I believe I'm limited to 4 primaries. I plan to use LVM to create 2 logical partitions in the root-var primary partition.

Why this plan? I like boot separate from the OS; I want to keep swap separate as well; home will be open to the network users; and that leaves one primary partition for the 2 remaining (root and var).

My question: In my situation, how would you partition your server, and why?

---

### Post by InvisibleMan on 2009-06-06
Although perhaps I should have posted this question in the Server forum.

Sorry about that.

---

### Post by unknownPoster on 2009-06-07
I fail to see the point of 6 GB of swap space, that's at least 5 GB of overkill in my opinion.

The server I run noost on (a forum with around 200 members), has 512 MB RAM and only has 256 MB of swap. As far as I know, it has never even accessed the swap space.

Other than that, it's personal preference.



I can post the partition scheme later if you want.

---

### Post by Nythain on 2009-06-07
i second to much swap space.

if it was a personal server, i would up root and var and drop home, but im assuming it will have numerous user accounts each doing thier own thing, so i guess that looks pretty good.

---

### Post by k3lt01 on 2009-06-07
Partitioning is always a personal preference. I personally don't see any advantage in separating /boot from / but then again I am only playing with my setup. With regards to SWAP I'd do a maximum of 2gb as that should be overkill for a smallish system like your describing that has an excess of physical RAM anyway

---

### Post by Nythain on 2009-06-07
yeah, that whole 2x swap of physical ram rule really only came to be for anything going into a suspend/hibernate mode, where the swap has to potentially store everything contained in the ram? or some jazz like that... theoretically, a server should never really be going into sleep or hibernate

with 3gb of physical ram, you could probably get away with 256-512mb of swap, you'll barely ever use it

---

### Post by -kg- on 2009-06-07
I'm not sure on a server installation, but is there any reason you can't create an Extended partition in such an installation?  Linux will run totally from an Extended partition, and you can have all the Logical partitions you care to create (well, up to around 60 or so, anyway...that enough? :D ).

Like I said, I know nothing about a server installation, and even less about LVM.  But it seems to me that, since my understanding is that Linux will run totally from (a) Logical partition(s), that would be the way I would try to go.  Any number of partitions you might need to make.

---

