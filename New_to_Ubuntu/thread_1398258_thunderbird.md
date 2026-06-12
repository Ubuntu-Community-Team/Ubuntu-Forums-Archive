---
title: "thunderbird"
date: 2010-02-04
forum: New to Ubuntu
---

### Post by Drenriza on 2010-02-04
Anyone who has a sources list to get and install thunderbird 3.1 with an apt-get install ...............


Thanks on advance

---

### Post by porchrat on 2010-02-04
> deb [http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu) jaunty main
deb-src [http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu) jaunty main

Obviously you would replace "jaunty" with whatever version you are currently running, in your case it looks like 8.04 so use "hardy"

guide [here]("http://www.ubuntugeek.com/how-to-install-thunderbird-3-in-ubuntu-9-109-048-108-04.html") if you need it.

Hope that helps.

---

### Post by howefield on 2010-02-04
> **porchrat said:**
> guide [here]("http://www.ubuntugeek.com/how-to-install-thunderbird-3-in-ubuntu-9-109-048-108-04.html")

Hope that helps.

Even if he is using Hardy ?

Think again ;)

The hardy lines are only a little further down the page.

deb [http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu) hardy main
deb-src [http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu) hardy main

Ah, you edited :)

---

### Post by porchrat on 2010-02-04
> **howefield said:**
> Even if he is using Hardy ?

Think again ;)

The hardy lines are only a little further down the page.

deb [http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu) hardy main
deb-src [http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu) hardy main

Ah, you edited :)

Lol yeah I noticed after I had posted that the little bio thing said he/she was running Hardy so I thought I had better make special note of that.

Either way though apt would've complained when the install was attempted anyway, but at least this way we have saved everyone a lot of stress :p

---

