---
title: "Unable to Connect BSNL EVDO DATA CARD"
date: 2009-10-27
forum: New to Ubuntu
---

### Post by bbsrmm on 2009-10-27
Sir,
I have procured BSNL EVDO DATA CARD model no AC8700 three days ago.Though I am able to connect the same in windowsXP,same is not  happening in Ubuntu8.04LTS. I have tried the advise from the internet.Can some one help.

---

### Post by infinitejones on 2009-10-27
I googled "evdo ac8700 ubuntu" and found a couple of useful pages:

[https://bugs.launchpad.net/ubuntu/+source/hal-info/+bug/321213]("https://bugs.launchpad.net/ubuntu/+source/hal-info/+bug/321213")

which suggests it might be worth upgrading to a more recent version of Ubuntu (don't forget that 8.04 is now 1.5 years old); and

[http://satish.playdrupal.com/?q=node/41]("http://satish.playdrupal.com/?q=node/41")

which looks like it was written when 8.04 was the current version, although I didn't read it in detail.

The reasons you're not finding much information are the fact that it sounds like an product which is specific to India, and (I suspect) you're still using an older version of Ubuntu.

Good luck!

---

### Post by bbsrmm on 2009-10-27
> **infinitejones said:**
> I googled "evdo ac8700 ubuntu" and found a couple of useful pages:

[https://bugs.launchpad.net/ubuntu/+source/hal-info/+bug/321213]("https://bugs.launchpad.net/ubuntu/+source/hal-info/+bug/321213")

which suggests it might be worth upgrading to a more recent version of Ubuntu (don't forget that 8.04 is now 1.5 years old); and

[http://satish.playdrupal.com/?q=node/41]("http://satish.playdrupal.com/?q=node/41")

which looks like it was written when 8.04 was the current version, although I didn't read it in detail.

The reasons you're not finding much information are the fact that it sounds like an product which is specific to India, and (I suspect) you're still using an older version of Ubuntu.

Good luck!
I am regularly updating the ubuntu8.04.Last update done yesterday so I think the version is upto date.Regarding the product i.e EVDO data card of BSNL i dont know ?

---

### Post by adalal on 2009-10-27
> **bbsrmm said:**
> I am regularly updating the ubuntu8.04.Last update done yesterday so I think the version is upto date.Regarding the product i.e EVDO data card of BSNL i dont know ?

Ubuntu 8.04 is still supported. However, what infinitejones suggested was to upgrade to the new distro, which is Ubuntu 9.04 (Ubuntu 9.10 comes out in a couple of days, might as well upgrade to that with the RCs available, or wait for a couple of days).

To do this, all you have to do, is run ```
update-manager -d
``` and then follow the instructions to upgrade to the new distribution, quite painless...

---

### Post by infinitejones on 2009-10-27
> what infinitejones suggested was to upgrade to the new distro

That's right. Maybe this is a problem that was fixed when Ubuntu 8.10 or 9.04 was released. That might explain why the only details online about how to fix it appear to have been written with 8.04 was the current version.

If the problem was fixed by the release of 8.10 or 9.04, nobody would bother putting details online of how to fix it after those versions were released.

---

