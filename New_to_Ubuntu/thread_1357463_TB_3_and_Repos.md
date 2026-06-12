---
title: "TB 3 and Repos"
date: 2009-12-17
forum: New to Ubuntu
---

### Post by Domainbug on 2009-12-17
Can someone please upload Thunderbird 3 to a repo. Trying to install it any other way for a newbie is Mission Impossible.

Regards
Lee

---

### Post by Kobalt on 2009-12-17
You can install it from the Mozilla PPA. Add the PPA with this command line : ```
sudo add-apt-repository ppa:ubuntu-mozilla-daily/ppa
```
And then launch Synaptic, refresh, and search for Thunderbird-3.0

---

### Post by northern lights on 2009-12-17
Add ```
deb http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu karmic main
``` to your sources list.```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 247510BE
``````
sudo apt-get update
``````
sudo apt-get install thunderbird-3.0
```

---

