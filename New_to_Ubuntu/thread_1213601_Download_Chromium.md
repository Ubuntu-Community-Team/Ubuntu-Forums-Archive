---
title: "Download Chromium"
date: 2009-07-15
forum: New to Ubuntu
---

### Post by ubudog on 2009-07-15
Where do I download chromium?  I can't seem to find it.

---

### Post by Bradtek on 2009-07-15
Add this line into your software sources for Chromium daily builds.

```
sudo gedit /etc/apt/sources.list
```

```

deb http://ppa.launchpad.net/chromium-daily/ppa/ubuntu jaunty main
``` 

Install it

```
sudo apt-get update
sudo apt-get install chromium-browser
```

From thread here
[http://forums.whirlpool.net.au/forum-replies.cfm?t=1239728](http://forums.whirlpool.net.au/forum-replies.cfm?t=1239728)

---

### Post by ubudog on 2009-07-15
Thanks a lot.

---

### Post by ubudog on 2009-07-15
Sweet I'm running it right now!

---

### Post by ubudog on 2009-07-15
Still gonna stick with firefox though.  Until chromium is out of dev stage.

---

