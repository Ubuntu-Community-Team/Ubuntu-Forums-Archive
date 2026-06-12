---
title: "tcp ip 6? causing problems...."
date: 2008-05-19
forum: Networking &amp; Wireless
---

### Post by alphis on 2008-05-19
Hello all. I've a strange but persistant issue with gutsy gibbon install. I noticed that I wasn't able to get ssh tunnels to work on my ubuntu system and then I realized that the loopback interface was defined as follows (/etc/hosts):

::1     ip6-localhost ip6-loopback

After commenting this out my ssh tunnels connected and worked flawlessly. Therefore my problem was due to ubuntu ingeniously deciding that ip6 should be on by default on the loopback interface.

Now my next issue. Wine + internet access. Apparently there are threads saying enabling/disabling some nss-mdns package will solve the issue. I tried both and nothing helps. Anything in wine that requires internet access fails miserably. Now I'm wondering if this is simply another ingenious unbuntu ip6 related problem which is manifesting itself as a wine problem.

Can anyone tell me HOW to COMPLETELY AND FOREVER REMOVE IP6 as if it NEVER EXISTED? I wish for these network problems to go away before I end up installing a more intelligent distro.

---

### Post by alphis on 2008-05-19
anyone?

---

### Post by Iowan on 2008-05-19
It may be for an earlier version, but check the link in my signature.

---

