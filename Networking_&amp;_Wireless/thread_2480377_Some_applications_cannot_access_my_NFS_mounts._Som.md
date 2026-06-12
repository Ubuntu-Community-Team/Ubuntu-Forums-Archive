---
title: "Some applications cannot access my NFS mounts. Some can. Theories?"
date: 2022-10-27
forum: Networking &amp; Wireless
---

### Post by jfollmann on 2022-10-27
After a catastrophically failed upgrade from 20.04 to 22.04 I ended up having to reinstall Ubuntu. I installed 22.04 to begin with, which was an enormous pain due to some issues I won't go into here. Thankfully /home was a separate drive so I'm not set back TOO much in most ways, however I have run into an issue that's pretty much ruined the way I use this machine unless I can get it sorted out.

I have a NAS with several NFS shares. On my Ubuntu PC, these always got mounted into individual directories under /nas. For example, the "TV" share gets mounted to /nas/TV, and so on.

I had the sense to grab etc/fstab before reinstalling so I hoped all I'd have to do is drop the NFS lines from that into the new fstab, install nfs-common, and maybe set permissions on /nas and its contents so my user had access. And indeed, I DID need to do all of those things, and it did result in... some success. I can go into /nas/whatever share in Nautilus and use everything apparently normally. And SOME applications can access it. For example on Firefox right now i can easily download a file, and when browsing for a save location I can browse to those mounted locations and all is normal.

However, some applications can't see anything inside of /nas. In Musicbrainz Picard if I browse for files or folders and click on the /nas directory, the dialogue box shows what is clearly the contents of "/" instead. Some other apps have the same problem. I'm not really sure what the commonality is between the apps that have the problem. Any theories about why?

Fair warning, although I used Ubuntu every day prior to this setback, I don't have the time or inclination to dig into things the way I used to so in the past few years I have forgotten a lot. I can find my way around but I'm no expert. And I never really FULLY understood Linux permissions, just enough to get access to what I needed. I don't know that this IS a permissions problem, just putting that out there.

---

### Post by TheFu on 2022-10-27
snap packages run inside a sandbox environment and access outside your HOME is blocked.  This has been a known issue for snap packages since at least 2017 with the idea of local control over where snaps can and cannot have access ignored for some reason.

The fix is to not use snap packages for anything that needs access outside your HOME.

---

### Post by jfollmann on 2022-10-28
Aha, that was indeed my problem. Thank you for the tip!

I have to admit I've become a much more casual Linux user in the past few years. Combination of just not feeling inclined to mess around with my PC as much as I used to, and having an established system that just kinda worked for a long time (until that last upgrade attempt). So I'd barely even picked up on the fact that snaps existed. Certainly wasn't thinking about whether the newer software manager was using them.

BUT I know enough to realize that Synaptic probably doesn't know what a snap is, so I removed the version of Picard I had and renstalled it  via Synaptic (after installing it - pretty wild to realize it wasn't even there), and lo and behold it has proper access to those directories again. I imagine the reason I didn't have this issue before the upgrade was that most of my my apps were originally installed before snaps were a thing, and they just kept upgrading from whatever repos they came from? Whatever, I know what the issue is now. Thanks again!

---

