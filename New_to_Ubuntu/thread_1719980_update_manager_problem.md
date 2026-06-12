---
title: "update manager problem"
date: 2011-04-02
forum: New to Ubuntu
---

### Post by dazthejunglist on 2011-04-02
hi i have a problem with update manager on ubuntu 10.10 i keep getting this message and im not sure what to do about it any ideas please

W:Failed to fetch [http://ppa.launchpad.net/user/ppa-nam/ubuntu/dists/maverick/main/source/Sources.gz](http://ppa.launchpad.net/user/ppa-nam/ubuntu/dists/maverick/main/source/Sources.gz)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/user/ppa-nam/ubuntu/dists/maverick/main/binary-amd64/Packages.gz](http://ppa.launchpad.net/user/ppa-nam/ubuntu/dists/maverick/main/binary-amd64/Packages.gz)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/user/ppa-name/ubuntu/dists/maverick/main/source/Sources.gz](http://ppa.launchpad.net/user/ppa-name/ubuntu/dists/maverick/main/source/Sources.gz)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/user/ppa-name/ubuntu/dists/maverick/main/binary-amd64/Packages.gz](http://ppa.launchpad.net/user/ppa-name/ubuntu/dists/maverick/main/binary-amd64/Packages.gz)  404  Not Found
, E:Some index files failed to download, they have been ignored, or old ones used instead.:confused::confused::confused::confused:

---

### Post by wolfen69 on 2011-04-02
It actually doesn't hurt your ability to download anything.

Post the output of
```
gksudo gedit /etc/apt/sources.list
```

---

### Post by Norm24 on 2011-04-02
Those PPAs are not currently up and running.Could be for updating or maintenance.

No big deal.When they're back up you'll no longer receive that error message.

---

### Post by dazthejunglist on 2011-04-03
cheers ive disabled them for the time being cos it was getting annoying

---

