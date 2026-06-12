---
title: "apt-cacher-ng hogging network bandwidth"
date: 2015-11-02
forum: Networking &amp; Wireless
---

### Post by Spency on 2015-11-02
I run a small server with apt-cacher-ng on it. When the server starts, after a while web pages take forever to load, game latency spikes to nearly unplayable levels, even ssh to local computers is very laggy. Then when the server is rebooted, everything returns to normal. 

I have now stopped the apt-cacher-ng daemon. This is a really annoying issue especially considering how much data the cache has accumulated and am wondering how can I diagnose and fix the issue?

---

### Post by Spency on 2015-11-02
I should also mention the same server runs apt-mirror and backuppc. I believe apt-cacher-ng is stopped (since I can no longer access the web gui), however I still see the same issues occurring.

---

### Post by sandyd on 2015-11-02
It may be [https://bugs.launchpad.net/ubuntu/+bug/1001780](https://bugs.launchpad.net/ubuntu/+bug/1001780) (regression)

It will cause apt-cacher-ng to download files every 2 hours (which is a bit excessive).
If you wait, does apt-cacher-ng ever stop hogging the network bandwidth?

Edit:

Try running the command
```

sudo iftop
```
to check what is using the bandwidth.

If you have multiple interfaces, use the "-i" flag to specify the interface.
Example
```

sudo iftop -i eth1
```

You can install it with
```

sudo apt-get install iftop
```

---

### Post by Spency on 2015-11-07
Thank you for your help! Using iftop and top together I found the culprit - it was backuppc, not apt-cacher. I adjusted the blackout period for backuppc and now everything is good. Thank you again.

---

