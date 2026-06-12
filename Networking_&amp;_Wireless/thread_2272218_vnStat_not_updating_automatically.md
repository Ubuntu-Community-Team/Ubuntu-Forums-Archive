---
title: "vnStat not updating automatically"
date: 2015-04-05
forum: Networking &amp; Wireless
---

### Post by Diablosblizz on 2015-04-05
Hi there,

I'm having a problem with vnstat where it will not automatically update traffic information on eth0. For example, if I run vnstat with no parameters it returns the following:

```
 eth0:
       Apr '15    211.65 MiB  /   58.26 MiB  /  269.91 MiB  /    2.35 GiB
     yesterday    210.81 MiB  /   21.23 MiB  /  232.05 MiB
         today       860 KiB  /   37.03 MiB  /   37.87 MiB  /      --

```

However, it will never update this information. The only way I can sometimes update this information is by running vnstat -u, but most of the time it will return the below and wipe out my data for the day:

```
Traffic rate for "eth0" higher than set maximum 100 Mbit (55->757, r2147 t49553), syncing.
```

Now, if I run vnstat again my stats for today will be different (notice the today sizes have changed):

```
 eth0:
       Apr '15    211.41 MiB  /   50.13 MiB  /  261.54 MiB  /    2.28 GiB
     yesterday    210.81 MiB  /   21.23 MiB  /  232.05 MiB
         today       607 KiB  /   28.90 MiB  /   29.49 MiB  /      --

```

From my understanding, the daemon must be running (which it is when I check):

```
root@ns513954:/home/keith# /etc/init.d/vnstat status
 * vnStat daemon is running

```

I really don't know what else I can try. I've let it run for about 24 hours and no information is updating. I also followed everything described [here]("http://askubuntu.com/questions/500663/vnstat-not-updating"). Does anybody have any ideas?

---

