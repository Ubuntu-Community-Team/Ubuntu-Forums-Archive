---
title: "[solved] lockd: failed to monitor &lt;insert your nfs server here&gt;"
date: 2007-05-04
forum: Networking &amp; Wireless
---

### Post by fourbissime on 2007-05-04
Hi there. Yesterday I installed Feisty Fawn on my computer at work. With the previous ubuntu version, everything was working fine, but not here. Now my problem is solved, but as I found the solution so counter-intuitive, I thought it would be a good idea to share it.

Firefox was taking a long long time to start (several minutes) and a quick look at dmesg would give me this :

> [ 1734.725922] statd: server localhost not responding, timed out
[ 1734.725928] lockd: cannot monitor waly
[ 1734.725930] lockd: failed to monitor waly
[ 3465.421998] statd: server localhost not responding, timed out
[ 3465.422026] lockd: cannot monitor waly
[ 3465.422029] lockd: failed to monitor waly
[ 3549.325212] statd: server localhost not responding, timed out
[ 3549.325229] lockd: cannot monitor waly
[ 3549.325231] lockd: failed to monitor waly
[ 3580.851807] statd: server localhost not responding, timed out
[ 3580.851824] lockd: cannot monitor waly
[ 3580.851826] lockd: failed to monitor waly
[ 3580.851868] statd: server localhost not responding, timed out
[ 3580.851874] lockd: cannot monitor waly
[ 3580.851876] lockd: failed to monitor waly


Seems like my computer had some troubles to get in touch with the server, even though it was able to mount the partition with the home directories. Weird thing.

The trick to solve this :

> sudo apt-get install nfs-common

I don't really understand why this package hasn't been installed through the dependencies of autofs which was installed. well, that's it.

---

