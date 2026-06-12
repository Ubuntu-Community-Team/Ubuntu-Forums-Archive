---
title: "updating problems"
date: 2010-08-22
forum: New to Ubuntu
---

### Post by laurenzanam on 2010-08-22
this is the error it says before i start up dating this operating system

" Could not download all repository indexes

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct."

and then in the box it says 

"Failed to fetch [http://archive.canonical.com/ubuntu/dists/lucid/Release.gpg](http://archive.canonical.com/ubuntu/dists/lucid/Release.gpg)  Something wicked happened resolving 'archive.canonical.com:http' (-5 - No address associated with hostname)
Failed to fetch [http://archive.canonical.com/ubuntu/dists/lucid/partner/i18n/Translation-en_GB.bz2](http://archive.canonical.com/ubuntu/dists/lucid/partner/i18n/Translation-en_GB.bz2)  Something wicked happened resolving 'archive.canonical.com:http' (-5 - No address associated with hostname)
Failed to fetch [http://deb.paissad.net/dists/unstable/Release.gpg](http://deb.paissad.net/dists/unstable/Release.gpg)  Something wicked happened resolving 'deb.paissad.net:http' (-5 - No address associated with hostname)
Failed to fetch [http://mirrors.dotsrc.org/getdeb/ubuntu/dists/lucid-getdeb/Release.gpg](http://mirrors.dotsrc.org/getdeb/ubuntu/dists/lucid-getdeb/Release.gpg)  Something wicked happened resolving 'mirrors.dotsrc.org:http' (-5 - No address associated with hostname)
Failed to fetch [http://dl.dropbox.com/u/1108539/dbupdate/./Release.gpg](http://dl.dropbox.com/u/1108539/dbupdate/./Release.gpg)  Something wicked happened resolving 'dl.dropbox.com:http' (-5 - No address associated with hostname)
Failed to fetch [http://linux.dropbox.com/ubuntu/dists/lucid/Release.gpg](http://linux.dropbox.com/ubuntu/dists/lucid/Release.gpg)  Something wicked happened resolving 'linux.dropbox.com:http' (-5 - No address associated with hostname)
Failed to fetch [http://archive.getdeb.net/ubuntu/dists/lucid-getdeb/Release.gpg](http://archive.getdeb.net/ubuntu/dists/lucid-getdeb/Release.gpg)  Something wicked happened resolving 'archive.getdeb.net:http' (-5 - No address associated with hostname)
Failed to fetch [http://dl.google.com/linux/deb/dists/stable/Release.gpg](http://dl.google.com/linux/deb/dists/stable/Release.gpg)  Something wicked happened resolving 'dl.google.com:http' (-5 - No address associated with hostname)
Failed to fetch [http://deb.playonlinux.com/dists/lucid/Release.gpg](http://deb.playonlinux.com/dists/lucid/Release.gpg)  Something wicked happened resolving 'deb.playonlinux.com:http' (-5 - No address associated with hostname)
Failed to fetch [http://deb.playonlinux.com/dists/lucid/main/i18n/Translation-en_GB.bz2](http://deb.playonlinux.com/dists/lucid/main/i18n/Translation-en_GB.bz2)  Something wicked happened resolving 'deb.playonlinux.com:http' (-5 - No address associated with hostname)
Some index files failed to download, they have been ignored, or old ones used instead."

could someone help diagnose this problem

---

### Post by ranch hand on 2010-08-22
This sounds like a connection problem to me.

Try running, in terminal (Applications>Addessories>Terminal);
```

sudo apt-get update

```
Have the terminal on full screen and watch.  If it downloads anything, but does not complete, hit the up arrow key.  This will bring up your last command.  Hit enter again.  If it does not complete then, post the terminal out put here.

---

### Post by sandyd on 2010-08-22
> **laurenzanam said:**
> this is the error it says before i start up dating this operating system

" Could not download all repository indexes

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct."

and then in the box it says 

"Failed to fetch [http://archive.canonical.com/ubuntu/dists/lucid/Release.gpg](http://archive.canonical.com/ubuntu/dists/lucid/Release.gpg)  Something wicked happened resolving 'archive.canonical.com:http' (-5 - No address associated with hostname)
Failed to fetch [http://archive.canonical.com/ubuntu/dists/lucid/partner/i18n/Translation-en_GB.bz2](http://archive.canonical.com/ubuntu/dists/lucid/partner/i18n/Translation-en_GB.bz2)  Something wicked happened resolving 'archive.canonical.com:http' (-5 - No address associated with hostname)
Failed to fetch [http://deb.paissad.net/dists/unstable/Release.gpg](http://deb.paissad.net/dists/unstable/Release.gpg)  Something wicked happened resolving 'deb.paissad.net:http' (-5 - No address associated with hostname)
Failed to fetch [http://mirrors.dotsrc.org/getdeb/ubuntu/dists/lucid-getdeb/Release.gpg](http://mirrors.dotsrc.org/getdeb/ubuntu/dists/lucid-getdeb/Release.gpg)  Something wicked happened resolving 'mirrors.dotsrc.org:http' (-5 - No address associated with hostname)
Failed to fetch [http://dl.dropbox.com/u/1108539/dbupdate/./Release.gpg](http://dl.dropbox.com/u/1108539/dbupdate/./Release.gpg)  Something wicked happened resolving 'dl.dropbox.com:http' (-5 - No address associated with hostname)
Failed to fetch [http://linux.dropbox.com/ubuntu/dists/lucid/Release.gpg](http://linux.dropbox.com/ubuntu/dists/lucid/Release.gpg)  Something wicked happened resolving 'linux.dropbox.com:http' (-5 - No address associated with hostname)
Failed to fetch [http://archive.getdeb.net/ubuntu/dists/lucid-getdeb/Release.gpg](http://archive.getdeb.net/ubuntu/dists/lucid-getdeb/Release.gpg)  Something wicked happened resolving 'archive.getdeb.net:http' (-5 - No address associated with hostname)
Failed to fetch [http://dl.google.com/linux/deb/dists/stable/Release.gpg](http://dl.google.com/linux/deb/dists/stable/Release.gpg)  Something wicked happened resolving 'dl.google.com:http' (-5 - No address associated with hostname)
Failed to fetch [http://deb.playonlinux.com/dists/lucid/Release.gpg](http://deb.playonlinux.com/dists/lucid/Release.gpg)  Something wicked happened resolving 'deb.playonlinux.com:http' (-5 - No address associated with hostname)
Failed to fetch [http://deb.playonlinux.com/dists/lucid/main/i18n/Translation-en_GB.bz2](http://deb.playonlinux.com/dists/lucid/main/i18n/Translation-en_GB.bz2)  Something wicked happened resolving 'deb.playonlinux.com:http' (-5 - No address associated with hostname)
Some index files failed to download, they have been ignored, or old ones used instead."

could someone help diagnose this problem
it seems that there is a problem with ubuntu 10.04 for some users.
The DNS settings are screwed up, when they should be working.

see my guide here.
[http://openubuntu.com/index.php/topic,230.0.html](http://openubuntu.com/index.php/topic,230.0.html)

---

### Post by BillybobT on 2011-06-25
Well, this thing is absolutely killing my update process. I think I'll just delete the dang thing for now until you get it fixed.

---

