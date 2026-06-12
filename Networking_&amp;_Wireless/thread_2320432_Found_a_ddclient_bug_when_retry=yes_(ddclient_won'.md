---
title: "Found a ddclient bug when retry=yes (ddclient won't update)"
date: 2016-04-13
forum: Networking &amp; Wireless
---

### Post by m12lrpv on 2016-04-13
I've just spent too many hours debugging why ddclient wouldn't update when the ip address changed. The issue is worth sharing because others must definitely be having this problem.

The culprit turned out to be a combination of retry=yes in the config and this piece of code in /usr/sbin/ddclient

```

    if (opt('retry')) {
        @hosts = map { $_ if $cache{$_}{'status'} ne 'good' } keys %cache;
    }

```

As far as I can tell it maps your config against a cache **which hasn't been loaded yet** (Like that's not a major bug) and the consequences are that it discards your config. Later on it loads the cache and without any config it presumes there's nothing to do and exits.
My solution is to comment out that code because it's ultra dumb and because I don't know enough perl nor have the background with ddclient to ensure the cache is loaded before it does this check.

---

