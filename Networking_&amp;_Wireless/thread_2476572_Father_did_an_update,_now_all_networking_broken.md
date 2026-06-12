---
title: "Father did an update, now all networking broken"
date: 2022-06-30
forum: Networking &amp; Wireless
---

### Post by sremick on 2022-06-30
So today my father did some sort of update. You'll have to pardon my lack of details... I'm in the middle of this, acting as a relay since he has no way to get online at the moment. According to him it wasn't a major OS version update or anything... in fact, I've confirmed he's still on Ubuntu 20.04.4 LTS. So presumably just app and maybe driver updates? Kernel updates?

However, after these "updates" all his networking is now broken, both wired and wifi (separate adapters, although both are Intel). The network status on either just keeps flapping off and on but unable to connect. I even had him try a USB ethernet adapter and the behavior is the same. So it is something general and not related to any specific network adapter or chipset.

I'm a bit at a loss, as I recommended him getting a computer with Intel-based networking since it always seemed to "just work" and I've not seen this behavior before. I realize I'm not providing as much detail as you'd like or as I'd normally give, but I'm hoping that it's enough to figure out a starting point to narrow this down. Any and all assistance greatly appreciated!

---

### Post by sremick on 2022-06-30
Solved... his router apparently decided to stop handing out DHCP requests for no reason. Rebooted the router, all is well.

---

