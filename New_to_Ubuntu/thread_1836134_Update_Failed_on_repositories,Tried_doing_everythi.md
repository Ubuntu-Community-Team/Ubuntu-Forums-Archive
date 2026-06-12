---
title: "Update Failed on repositories,Tried doing everything I could find on this forum but s"
date: 2011-08-30
forum: New to Ubuntu
---

### Post by sarang031705 on 2011-08-30
here's the error:

W:Failed to fetch [http://ppa.launchpad.net/globalmenu-team/ppa/ubuntu/dists/natty/main/source/Sources](http://ppa.launchpad.net/globalmenu-team/ppa/ubuntu/dists/natty/main/source/Sources)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/globalmenu-team/ppa/ubuntu/dists/natty/main/binary-amd64/Packages](http://ppa.launchpad.net/globalmenu-team/ppa/ubuntu/dists/natty/main/binary-amd64/Packages)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/dists/natty/main/source/Sources](http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/dists/natty/main/source/Sources)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/dists/natty/main/binary-amd64/Packages](http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/dists/natty/main/binary-amd64/Packages)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/team=xbmc=svn/ppa/ubuntu/dists/natty/main/source/Sources](http://ppa.launchpad.net/team=xbmc=svn/ppa/ubuntu/dists/natty/main/source/Sources)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/team=xbmc=svn/ppa/ubuntu/dists/natty/main/binary-amd64/Packages](http://ppa.launchpad.net/team=xbmc=svn/ppa/ubuntu/dists/natty/main/binary-amd64/Packages)  404  Not Found
, E:Some index files failed to download. They have been ignored, or old ones used instead.

---

### Post by seawolf167 on 2011-08-30
You have added some PPAs that are non-existent, have been moved, deleted, something. You'll need to delete the offending lines from your sources.list file

Backup the file and then open the file for editing

```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.backup
gedit /etc/apt/sources.list
```

then find and delete the bad PPAs that have been added (usually at the bottom).

---

### Post by Frogs Hair on 2011-08-30
Are the PPA's still  supported  ? The global menu ppa has not been updated in 74 weeks  and the other 64 weeks . If they are not supported you can remove the sources from the software sources list and use the applications as is without complaint from the updae manager .

---

