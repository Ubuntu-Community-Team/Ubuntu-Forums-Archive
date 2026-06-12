---
title: "Update manager error"
date: 2011-06-26
forum: New to Ubuntu
---

### Post by DGINSD on 2011-06-26
I went to do an update and got an error message just want to know what it means and if theres anything I need to do to fix it the error is a s follows

> W:Failed to fetch [http://packages.medibuntu.org/dists/maverick/Release.gpg](http://packages.medibuntu.org/dists/maverick/Release.gpg)  Something wicked happened resolving 'packages.medibuntu.org:http' (-5 - No address associated with hostname)
, E:Some index files failed to download, they have been ignored, or old ones used instead.


Just kind of seemed odd to me, as I haven't changed anything. Any help is appreciated.

---

### Post by nzjethro on 2011-06-26
The problem is that update manager is attempting to download packages from a host that doesn't exist. It's likely that your repos are from a mixture of Medibuntu releases.
First up try
```
sudo apt-get update
```

Then please post the output of
```
ls /etc/apt/sources.list.d/
```

---

### Post by DGINSD on 2011-06-26
K output of above command

> glasen-intel-driver-maverick.list       medibuntu.list.save
glasen-intel-driver-maverick.list.save  tualatrix-ppa-maverick.list
medibuntu.list


If I recall correctly these were intel graphics driver fixes I tried to load which didn't work. What should I do about it?

---

### Post by jtarin on 2011-06-26
> **DGINSD said:**
> K output of above command
```
glasen-intel-driver-maverick.list medibuntu.list.save
glasen-intel-driver-maverick.list.save tualatrix-ppa-maverick.list
medibuntu.list 
```



If I recall correctly these were intel graphics driver fixes I tried to load which didn't work. What should I do about it?If these are entries in you sources list, as root,  place a # at the beginning of the line and save. Then try to run again.

---

### Post by DGINSD on 2011-06-26
Where is my sources list located? Can I revert all my sources back to the original ones and then reload the medibuntu repository on manually? I really just don't understand this.

---

### Post by jtarin on 2011-06-26
> **DGINSD said:**
> Where is my sources list located? Can I revert all my sources back to the original ones and then reload the medibuntu repository on manually? I really just don't understand this.It is located in /etc/apt/sources.list.d.
You can manipulate by using Synaptic Package Manager from its menu or Software Sources from Main Menu>System>Administration or edit as root with gedit directly.

Additionally...[look here.]("http://medibuntu.org/repository.php")

---

### Post by DGINSD on 2011-06-27
K this is kind of got me very confused and I'm totally lost. I removed the added PPA repos and their keys, and also removed the Medibuntu repo and key and then reinstalled the Medibuntu one.

Now it's giving me a differant error it reads as follows

> W:GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 6AF0E1940624A220, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/maverick/Release.gpg)  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://archive.getdeb.net/ubuntu/dists/maverick-getdeb/Release.gpg](http://archive.getdeb.net/ubuntu/dists/maverick-getdeb/Release.gpg)  Could not connect to archive.getdeb.net:80 (209.105.191.78). - connect (113: No route to host)
, W:Failed to fetch [http://archive.getdeb.net/ubuntu/dists/maverick-getdeb/apps/i18n/Translation-en.bz2](http://archive.getdeb.net/ubuntu/dists/maverick-getdeb/apps/i18n/Translation-en.bz2)  Unable to connect to archive.getdeb.net:http:
, W:Failed to fetch [http://archive.getdeb.net/ubuntu/dists/maverick-getdeb/apps/source/Sources.gz](http://archive.getdeb.net/ubuntu/dists/maverick-getdeb/apps/source/Sources.gz)  Unable to connect to archive.getdeb.net:http:
, W:Failed to fetch [http://archive.getdeb.net/ubuntu/dists/maverick-getdeb/apps/binary-i386/Packages.gz](http://archive.getdeb.net/ubuntu/dists/maverick-getdeb/apps/binary-i386/Packages.gz)  Unable to connect to archive.getdeb.net:http:
, E:Some index files failed to download, they have been ignored, or old ones used instead.

I don't get this prior to me getting these errors I never messed with my sources, I added Medi., GetDeb, and the PPA all three worked fine up untill a few days ago.

The only thing that I can think that's differant is we got our own internet installed this weekend, could that have anything to do with it?

---

### Post by gvorik on 2011-06-27
I'm getting the getdeb repo errors as well. My guess is its something outside of your system. Wait a day and retry.

---

