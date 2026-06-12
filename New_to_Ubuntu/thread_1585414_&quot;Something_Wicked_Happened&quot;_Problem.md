---
title: "&quot;Something Wicked Happened&quot; Problem"
date: 2010-09-30
forum: New to Ubuntu
---

### Post by mbyrd11 on 2010-09-30
Could not download all repository indexes

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.
```
Failed to fetch http://packages.medibuntu.org/dists/lucid/Release.gpg  Something wicked happened resolving 'packages.medibuntu.org:http' (-5 - No address associated with hostname)
Failed to fetch http://ppa.launchpad.net/psyke83/ppa/ubuntu/dists/lucid/Release.gpg  Something wicked happened resolving 'ppa.launchpad.net:http' (-5 - No address associated with hostname)
Some index files failed to download, they have been ignored, or old ones used instead.
```

I get this whenever I press the Check button in the Update Manager.
(Yes I know I'm a button pusher)

---

### Post by sandyd on 2010-09-30
> **mbyrd11 said:**
> Could not download all repository indexes

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.
```
Failed to fetch http://packages.medibuntu.org/dists/lucid/Release.gpg  Something wicked happened resolving 'packages.medibuntu.org:http' (-5 - No address associated with hostname)
Failed to fetch http://ppa.launchpad.net/psyke83/ppa/ubuntu/dists/lucid/Release.gpg  Something wicked happened resolving 'ppa.launchpad.net:http' (-5 - No address associated with hostname)
Some index files failed to download, they have been ignored, or old ones used instead.
```I get this whenever I press the Check button in the Update Manager.
(Yes I know I'm a button pusher)
can you post output of
```

cat /etc/apt/sources.list.d/medibuntu.list
```

also try [http://openubuntu.com/index.php/topic,230.0.html](http://openubuntu.com/index.php/topic,230.0.html)

---

### Post by jtarin on 2010-09-30
[First source is reachable.]("http://packages.medibuntu.org/dists/lucid/Release.gpg") 
[Second source is reachable.]("http://ppa.launchpad.net/psyke83/ppa/ubuntu/dists/lucid/Release.gpg")

[Download and run this script to update all your ppa keys.]("http://www.webupd8.org/2009/05/ubuntu-script-to-automatically-install.html")

[Or here]("http://www.webupd8.org/2010/05/automatically-import-all-missing.html")

---

### Post by mbyrd11 on 2010-09-30
> **sandyd said:**
> can you post output of
```

cat /etc/apt/sources.list.d/medibuntu.list
```

also try [http://openubuntu.com/index.php/topic,230.0.html](http://openubuntu.com/index.php/topic,230.0.html)

Here is what I got
```
## Please report any bug on https://bugs.launchpad.net/medibuntu/
deb http://packages.medibuntu.org/ lucid free non-free #Medibuntu - Ubuntu 10.04 "lucid lynx"
deb-src http://packages.medibuntu.org/ lucid free non-free #Medibuntu (source) - Ubuntu 10.04 "lucid lynx"

```

And jtarin what exactly do you mean?
Sorry I am confused.

---

### Post by jtarin on 2010-09-30
> **mbyrd11 said:**
> 
And jtarin what exactly do you mean?
Sorry I am confused.
1. I can reach both sources from my location...possibly its your network.
If your network is OK then....
2.The first script will update your ppa repositories if you have any. (ppa.launchpad.net/psyke83/ppa)
3. The second one does the same except it installs as a .deb pkg as you will read on the linked page.
These update all your ppa sources and .gpg keys. Then try again to download.

---

### Post by mbyrd11 on 2010-09-30
> **jtarin said:**
> 1. I can reach both sources from my location...possibly its your network.
If your network is OK then....
2.The first script will update your ppa repositories if you have any. (ppa.launchpad.net/psyke83/ppa)
3. The second one does the same except it installs as a .deb pkg as you will read on the linked page.
These update all your ppa sources and .gpg keys. Then try again to download.

So I ran the fist link with the Lunchpad update. and which link is the one that will install as a .deb for me?

---

### Post by jtarin on 2010-10-01
> **mbyrd11 said:**
> So I ran the fist link with the Lunchpad update. and which link is the one that will install as a .deb for me?
I wrote....> 3. The second one does the same except it installs as a .deb pkg as you will read on the linked page.
These update all your ppa sources and .gpg keys. Then try again to download.

---

