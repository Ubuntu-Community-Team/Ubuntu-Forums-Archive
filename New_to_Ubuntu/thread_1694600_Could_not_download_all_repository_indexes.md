---
title: "Could not download all repository indexes"
date: 2011-02-24
forum: New to Ubuntu
---

### Post by joenewtzie on 2011-02-24
Hello,
For some reason when I try to update my system with update manager, when I check for updates, I get this error.  Any idea on a fix? Thanks!


The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.

Failed to fetch [http://ppa.launchpad.net/canonical-dx-team/un/ubuntu/dists/lucid/main/binary-i386/Packages.gz](http://ppa.launchpad.net/canonical-dx-team/un/ubuntu/dists/lucid/main/binary-i386/Packages.gz)  404  Not Found
Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by Smart Viking on 2011-02-24
That's a faulty link. That is something you can just ignore, your system is fine.

btw this is the real working link: [http://ppa.launchpad.net/canonical-dx-team/une/ubuntu/dists/lucid/main/binary-i386/Packages.gz](http://ppa.launchpad.net/canonical-dx-team/une/ubuntu/dists/lucid/main/binary-i386/Packages.gz)

---

### Post by LowSky on 2011-02-24
do you need it, if not do this

go to system > administrator > software sources

go to other software tab, find the ppa, and disable or remove.

---

### Post by plucky on 2011-02-24
> **joenewtzie said:**
> Hello,
For some reason when I try to update my system with update manager, when I check for updates, I get this error.  Any idea on a fix? Thanks!


The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.

Failed to fetch [http://ppa.launchpad.net/canonical-dx-team/un/ubuntu/dists/lucid/main/binary-i386/Packages.gz](http://ppa.launchpad.net/canonical-dx-team/un/ubuntu/dists/lucid/main/binary-i386/Packages.gz)  404  Not Found
Some index files failed to download, they have been ignored, or old ones used instead.

The ppa address is incorrect in your sources.list.


Wrong one is 
```
http://ppa.launchpad.net/canonical-dx-team/un/ubuntu/dists/lucid/main/binary-i386/Packages.gz
```

Correct one is 
```
http://ppa.launchpad.net/canonical-dx-team/une/ubuntu/dists/lucid/main/binary-i386/Packages.gz
```

Notice the e in **une**

The PPA is probably located in **/etc/apt/sources.list.d**

Post output from a terminal of ```
cat /etc/apt/sources.list
ls - l /etc/apt/sources.list.c/
```

Good Luck

---

### Post by thefasterblueone on 2011-02-24
That URL is wrong, it is missing the "e" on .../un"e"/dists/.

Here is the correct URL:

[http://ppa.launchpad.net/canonical-dx-team/une/ubuntu/dists/lucid/main/binary-i386/Packages.gz]("http://ppa.launchpad.net/canonical-dx-team/une/ubuntu/dists/lucid/main/binary-i386/")

You will have to edit your sources.list. Run this command and add the "e" to the URL. Then click "File" and "Save"

```
sudo gedit /etc/apt/sources.list
```


Ahhh****, yah what he said.

---

### Post by joenewtzie on 2011-02-24
That worked out, thanks everyone! I figured I was missing something small. Thanks again!

---

