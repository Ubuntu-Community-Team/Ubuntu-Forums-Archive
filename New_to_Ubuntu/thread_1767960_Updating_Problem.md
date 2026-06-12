---
title: "Updating Problem"
date: 2011-05-26
forum: New to Ubuntu
---

### Post by jiggajoe506 on 2011-05-26
I am trying to Update and am getting this message and it in the details section it reads the following....

```
Failed to fetch http://ppa.launchpad.net/chromium-daily/ppa/ubuntu/pool/main/c/chromium-browser/chromium-browser-l10n_13.0.773.0~svn20110522r86230-0ubuntu1~ucd1~natty_all.deb 404  Not Found
Failed to fetch http://ppa.launchpad.net/chromium-daily/ppa/ubuntu/pool/main/c/chromium-browser/chromium-codecs-ffmpeg_13.0.773.0~svn20110522r86230-0ubuntu1~ucd1~natty_i386.deb 404  Not Found
Failed to fetch http://ppa.launchpad.net/chromium-daily/ppa/ubuntu/pool/main/c/chromium-browser/chromium-browser-inspector_13.0.773.0~svn20110522r86230-0ubuntu1~ucd1~natty_all.deb 404  Not Found
Failed to fetch http://ppa.launchpad.net/chromium-daily/ppa/ubuntu/pool/main/c/chromium-browser/chromium-browser_13.0.773.0~svn20110522r86230-0ubuntu1~ucd1~natty_i386.deb 404  Not Found

```

Any ideas guys?

---

### Post by Pand5461 on 2011-05-26
There are no such files on the server. Probably package list in the PPA is somehow wrong (maybe they updated package list but didn't update repo). Don't worry, that won't break your system.

---

### Post by sanguinoso on 2011-05-26
Post your /etc/apt/sources.list

---

### Post by wildmanne39 on 2011-05-26
> **jiggajoe506 said:**
> I am trying to Update and am getting this message and it in the details section it reads the following....

```
Failed to fetch http://ppa.launchpad.net/chromium-daily/ppa/ubuntu/pool/main/c/chromium-browser/chromium-browser-l10n_13.0.773.0~svn20110522r86230-0ubuntu1~ucd1~natty_all.deb 404  Not Found
Failed to fetch http://ppa.launchpad.net/chromium-daily/ppa/ubuntu/pool/main/c/chromium-browser/chromium-codecs-ffmpeg_13.0.773.0~svn20110522r86230-0ubuntu1~ucd1~natty_i386.deb 404  Not Found
Failed to fetch http://ppa.launchpad.net/chromium-daily/ppa/ubuntu/pool/main/c/chromium-browser/chromium-browser-inspector_13.0.773.0~svn20110522r86230-0ubuntu1~ucd1~natty_all.deb 404  Not Found
Failed to fetch http://ppa.launchpad.net/chromium-daily/ppa/ubuntu/pool/main/c/chromium-browser/chromium-browser_13.0.773.0~svn20110522r86230-0ubuntu1~ucd1~natty_i386.deb 404  Not Found

```

Any ideas guys?

Hi, if you do not use chrome you can just go in and uncheck those for chrome that will not download,also you could just leave it as long as your updates are working it just cant update that package.

---

