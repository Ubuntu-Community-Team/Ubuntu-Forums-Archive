---
title: "Network problem with flexlm license manager"
date: 2007-01-17
forum: Networking &amp; Wireless
---

### Post by Palmstroem on 2007-01-17
I am using Ubuntu Edgy on an AMD64 Opteron system; system runs well. I installed Matlab 7.3 client version. This means that the flexlm license manager runs on a different Windows server within our LAN.

However, Matlab starts up on rare occasions only. If that happens, everything is fine. But in most cases I am getting license error -16. Still I can ping the server and extract info with "lmstat". Looks like a firewall problem although I am not running one.

Any help would be welcome!

---

### Post by Palmstroem on 2007-01-30
Problem solved!

It had nothing to do with Ubuntu 64bit Linux. The Windoze XP license server was not correctly configured.

Now Matlab runs quicker than ever before!

However, I got the impression that the flexnet software - quite popular for licensing purposes of many commercial programs - operates like a virus, continuously exchanging all kind of strange messages between daemons over the net...

---

### Post by pould on 2007-03-16
Actually it's not like a virus. It only communicate on fixed TCP ports which you choose. So you have control over all the traffic. There is much other software which is many times worse.

One useful thing we use in relation to flexlm is license statistics to see our license usage. It works out pretty good: [http://www.x-formation.com/license_statistics/index.html](http://www.x-formation.com/license_statistics/index.html)

-- Poul

---

