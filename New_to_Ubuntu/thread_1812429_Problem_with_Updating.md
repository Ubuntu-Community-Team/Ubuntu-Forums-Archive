---
title: "Problem with Updating"
date: 2011-07-26
forum: New to Ubuntu
---

### Post by Hellfish03 on 2011-07-26
Hi

I recently changed from Ubuntu 10.10 to 10.04 64bit. I have a problem when running the update manager. I get this message:

[I][B]
Could not download all repository indexes

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.

GPG error: [http://linux.dropbox.com](http://linux.dropbox.com) karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY FC918B335044912EGPG error: [http://deb.opera.com](http://deb.opera.com) lenny Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A2019EA84E7532C8GPG error: [http://deb.playonlinux.com](http://deb.playonlinux.com) lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY E0F72778C4676186Failed to fetch [http://download.skype.com/linux/repos/debian/dists/stable/non-free/binary-amd64/Packages.gz](http://download.skype.com/linux/repos/debian/dists/stable/non-free/binary-amd64/Packages.gz)  404  Not Found
Some index files failed to download, they have been ignored, or old ones used instead.[/B][/I]


Any help appreciated!

---

### Post by thefasterblueone on 2011-07-26
Looks like the keys are missing. In Terminal run these commands one at a time.

Dropbox key: ```
sudo apt-key adv --keyserver pgp.mit.edu --recv-keys 5044912E
```

Opera key: ```
wget -O - http://deb.opera.com/archive.key | sudo apt-key add -
```

PlayOnLinux key: ```
wget -q "http://deb.playonlinux.com/public.gpg" -O- | sudo apt-key add -
```

Skype key: ```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 1E5D5E8D66AE0775
```

Then: ```
sudo apt-get update
```

Try Update Manager again.

---

### Post by Hellfish03 on 2011-07-28
Thanks seems to have fixed all but skype. I still get this:

[B]Failed to fetch [http://download.skype.com/linux/repos/debian/dists/stable/non-free/binary-amd64/Packages.gz](http://download.skype.com/linux/repos/debian/dists/stable/non-free/binary-amd64/Packages.gz)  404  Not Found
Some index files failed to download, they have been ignored, or old ones used instead.[/B]

---

### Post by thefasterblueone on 2011-07-28
Try reinstalling skype.

[http://linuxtree.blogspot.com/2010/05/how-to-install-skype-in-ubuntu-1004.html]("http://linuxtree.blogspot.com/2010/05/how-to-install-skype-in-ubuntu-1004.html")

---

### Post by Hellfish03 on 2011-07-29
ok reinstalled skype, ran the update manager again and got this!

Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/lucid-security/Release.gpg)  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/main/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/lucid-security/main/i18n/Translation-en_US.bz2)  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-proposed/Release.gpg](http://security.ubuntu.com/ubuntu/dists/lucid-proposed/Release.gpg)  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.167 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-proposed/main/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/lucid-proposed/main/i18n/Translation-en_US.bz2)  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.167 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-proposed/restricted/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/lucid-proposed/restricted/i18n/Translation-en_US.bz2)  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.167 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-proposed/universe/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/lucid-proposed/universe/i18n/Translation-en_US.bz2)  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.167 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-proposed/multiverse/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/lucid-proposed/multiverse/i18n/Translation-en_US.bz2)  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.167 80]
Failed to fetch [http://archive.canonical.com/ubuntu/dists/lucid-updates/Release.gpg](http://archive.canonical.com/ubuntu/dists/lucid-updates/Release.gpg)  Could not connect to archive.canonical.com:80 (91.189.88.33). - connect (110: Connection timed out)
Failed to fetch [http://archive.canonical.com/ubuntu/dists/lucid-updates/partner/i18n/Translation-en_US.bz2](http://archive.canonical.com/ubuntu/dists/lucid-updates/partner/i18n/Translation-en_US.bz2)  Unable to connect to archive.canonical.com:http:
Failed to fetch [http://archive.canonical.com/ubuntu/dists/lucid-security/Release.gpg](http://archive.canonical.com/ubuntu/dists/lucid-security/Release.gpg)  Unable to connect to archive.canonical.com:http:
Failed to fetch [http://archive.canonical.com/ubuntu/dists/lucid-security/partner/i18n/Translation-en_US.bz2](http://archive.canonical.com/ubuntu/dists/lucid-security/partner/i18n/Translation-en_US.bz2)  Unable to connect to archive.canonical.com:http:
Failed to fetch [http://archive.canonical.com/ubuntu/dists/lucid-proposed/Release.gpg](http://archive.canonical.com/ubuntu/dists/lucid-proposed/Release.gpg)  Unable to connect to archive.canonical.com:http:
Failed to fetch [http://archive.canonical.com/ubuntu/dists/lucid-proposed/partner/i18n/Translation-en_US.bz2](http://archive.canonical.com/ubuntu/dists/lucid-proposed/partner/i18n/Translation-en_US.bz2)  Unable to connect to archive.canonical.com:http:
Failed to fetch [http://deb.playonlinux.com/dists/lucid/Release.gpg](http://deb.playonlinux.com/dists/lucid/Release.gpg)  Something wicked happened resolving 'deb.playonlinux.com:http' (-5 - No address associated with hostname)
Failed to fetch [http://deb.playonlinux.com/dists/lucid/main/i18n/Translation-en_US.bz2](http://deb.playonlinux.com/dists/lucid/main/i18n/Translation-en_US.bz2)  Something wicked happened resolving 'deb.playonlinux.com:http' (-5 - No address associated with hostname)
Failed to fetch [http://deb.opera.com/opera/dists/lenny/Release.gpg](http://deb.opera.com/opera/dists/lenny/Release.gpg)  Something wicked happened resolving 'deb.opera.com:http' (-5 - No address associated with hostname)
Failed to fetch [http://deb.opera.com/opera/dists/lenny/non-free/i18n/Translation-en_US.bz2](http://deb.opera.com/opera/dists/lenny/non-free/i18n/Translation-en_US.bz2)  Something wicked happened resolving 'deb.opera.com:http' (-5 - No address associated with hostname)
Failed to fetch [http://linux.dropbox.com/ubuntu/dists/karmic/Release.gpg](http://linux.dropbox.com/ubuntu/dists/karmic/Release.gpg)  Something wicked happened resolving 'linux.dropbox.com:http' (-5 - No address associated with hostname)
Failed to fetch [http://linux.dropbox.com/ubuntu/dists/karmic/main/i18n/Translation-en_US.bz2](http://linux.dropbox.com/ubuntu/dists/karmic/main/i18n/Translation-en_US.bz2)  Something wicked happened resolving 'linux.dropbox.com:http' (-5 - No address associated with hostname)
Failed to fetch [http://download.skype.com/linux/repos/debian/dists/stable/Release.gpg](http://download.skype.com/linux/repos/debian/dists/stable/Release.gpg)  Something wicked happened resolving 'download.skype.com:http' (-5 - No address associated with hostname)
Failed to fetch [http://download.skype.com/linux/repos/debian/dists/stable/non-free/i18n/Translation-en_US.bz2](http://download.skype.com/linux/repos/debian/dists/stable/non-free/i18n/Translation-en_US.bz2)  Something wicked happened resolving 'download.skype.com:http' (-5 - No address associated with hostname)
Failed to fetch [http://archive.canonical.com/ubuntu/dists/lucid/partner/binary-amd64/Packages.gz](http://archive.canonical.com/ubuntu/dists/lucid/partner/binary-amd64/Packages.gz)  Unable to connect to archive.canonical.com:http:
Failed to fetch [http://archive.canonical.com/ubuntu/dists/lucid/partner/source/Sources.gz](http://archive.canonical.com/ubuntu/dists/lucid/partner/source/Sources.gz)  Unable to connect to archive.canonical.com:http:
Failed to fetch [http://archive.canonical.com/ubuntu/dists/lucid-backports/partner/binary-amd64/Packages.gz](http://archive.canonical.com/ubuntu/dists/lucid-backports/partner/binary-amd64/Packages.gz)  Unable to connect to archive.canonical.com:http:
Failed to fetch [http://archive.canonical.com/ubuntu/dists/lucid-backports/partner/source/Sources.gz](http://archive.canonical.com/ubuntu/dists/lucid-backports/partner/source/Sources.gz)  Unable to connect to archive.canonical.com:http:
Failed to fetch [http://archive.canonical.com/ubuntu/dists/lucid-updates/partner/binary-amd64/Packages.gz](http://archive.canonical.com/ubuntu/dists/lucid-updates/partner/binary-amd64/Packages.gz)  Unable to connect to archive.canonical.com:http:
Failed to fetch [http://archive.canonical.com/ubuntu/dists/lucid-updates/partner/source/Sources.gz](http://archive.canonical.com/ubuntu/dists/lucid-updates/partner/source/Sources.gz)  Unable to connect to archive.canonical.com:http:
Failed to fetch [http://archive.canonical.com/ubuntu/dists/lucid-security/partner/binary-amd64/Packages.gz](http://archive.canonical.com/ubuntu/dists/lucid-security/partner/binary-amd64/Packages.gz)  Unable to connect to archive.canonical.com:http:
Failed to fetch [http://archive.canonical.com/ubuntu/dists/lucid-security/partner/source/Sources.gz](http://archive.canonical.com/ubuntu/dists/lucid-security/partner/source/Sources.gz)  Unable to connect to archive.canonical.com:http:
Failed to fetch [http://archive.canonical.com/ubuntu/dists/lucid-proposed/partner/binary-amd64/Packages.gz](http://archive.canonical.com/ubuntu/dists/lucid-proposed/partner/binary-amd64/Packages.gz)  Unable to connect to archive.canonical.com:http:
Failed to fetch [http://archive.canonical.com/ubuntu/dists/lucid-proposed/partner/source/Sources.gz](http://archive.canonical.com/ubuntu/dists/lucid-proposed/partner/source/Sources.gz)  Unable to connect to archive.canonical.com:http:
Failed to fetch [http://packages.medibuntu.org/dists/lucid/free/binary-amd64/Packages.gz](http://packages.medibuntu.org/dists/lucid/free/binary-amd64/Packages.gz)  Unable to connect to packages.medibuntu.org:http:
Failed to fetch [http://packages.medibuntu.org/dists/lucid/non-free/binary-amd64/Packages.gz](http://packages.medibuntu.org/dists/lucid/non-free/binary-amd64/Packages.gz)  Unable to connect to packages.medibuntu.org:http:
Failed to fetch [http://packages.medibuntu.org/dists/lucid/free/source/Sources.gz](http://packages.medibuntu.org/dists/lucid/free/source/Sources.gz)  Unable to connect to packages.medibuntu.org:http:
Failed to fetch [http://packages.medibuntu.org/dists/lucid/non-free/source/Sources.gz](http://packages.medibuntu.org/dists/lucid/non-free/source/Sources.gz)  Unable to connect to packages.medibuntu.org:http:
Failed to fetch [http://download.skype.com/linux/repos/debian/dists/stable/non-free/binary-amd64/Packages.gz](http://download.skype.com/linux/repos/debian/dists/stable/non-free/binary-amd64/Packages.gz)  Unable to connect to download.skype.com:http:
Failed to fetch [http://deb.opera.com/opera/dists/lenny/non-free/binary-amd64/Packages.gz](http://deb.opera.com/opera/dists/lenny/non-free/binary-amd64/Packages.gz)  Unable to connect to deb.opera.com:http:
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/main/binary-amd64/Packages.gz](http://security.ubuntu.com/ubuntu/dists/lucid-security/main/binary-amd64/Packages.gz)  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.167 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/restricted/binary-amd64/Packages.gz](http://security.ubuntu.com/ubuntu/dists/lucid-security/restricted/binary-amd64/Packages.gz)  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.167 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/universe/binary-amd64/Packages.gz](http://security.ubuntu.com/ubuntu/dists/lucid-security/universe/binary-amd64/Packages.gz)  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.167 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/multiverse/binary-amd64/Packages.gz](http://security.ubuntu.com/ubuntu/dists/lucid-security/multiverse/binary-amd64/Packages.gz)  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.167 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/main/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/lucid-security/main/source/Sources.gz)  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.167 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/restricted/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/lucid-security/restricted/source/Sources.gz)  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.167 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/universe/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/lucid-security/universe/source/Sources.gz)  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.167 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/multiverse/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/lucid-security/multiverse/source/Sources.gz)  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.167 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-proposed/main/binary-amd64/Packages.gz](http://security.ubuntu.com/ubuntu/dists/lucid-proposed/main/binary-amd64/Packages.gz)  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.167 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-proposed/restricted/binary-amd64/Packages.gz](http://security.ubuntu.com/ubuntu/dists/lucid-proposed/restricted/binary-amd64/Packages.gz)  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.167 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-proposed/universe/binary-amd64/Packages.gz](http://security.ubuntu.com/ubuntu/dists/lucid-proposed/universe/binary-amd64/Packages.gz)  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.167 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-proposed/multiverse/binary-amd64/Packages.gz](http://security.ubuntu.com/ubuntu/dists/lucid-proposed/multiverse/binary-amd64/Packages.gz)  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.167 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-proposed/main/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/lucid-proposed/main/source/Sources.gz)  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.167 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-proposed/restricted/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/lucid-proposed/restricted/source/Sources.gz)  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.167 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-proposed/universe/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/lucid-proposed/universe/source/Sources.gz)  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.167 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-proposed/multiverse/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/lucid-proposed/multiverse/source/Sources.gz)  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.167 80]
Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by Hellfish03 on 2011-08-01
any ideas??

---

### Post by amjjawad on 2011-08-01
> **Hellfish03 said:**
> any ideas??

Are you still have the same issue with Skype?


Edit:
[https://help.ubuntu.com/community/Skype#Installing%20Skype](https://help.ubuntu.com/community/Skype#Installing%20Skype)

Skype is part of the Canonical partner repository: [https://help.ubuntu.com/community/Repositories/Ubuntu#Adding%20Canonical%20Partner%20Repositories](https://help.ubuntu.com/community/Repositories/Ubuntu#Adding%20Canonical%20Partner%20Repositories)

Try to un-tick that option, refresh Synaptic then tick it again and try.

See if that helps!

---

### Post by Hellfish03 on 2011-08-01
ok, i ran the update manager agian and this time i didn't get the whole long list, just this:

**Failed to fetch [http://download.skype.com/linux/repos/debian/dists/stable/non-free/binary-amd64/Packages.gz](http://download.skype.com/linux/repos/debian/dists/stable/non-free/binary-amd64/Packages.gz)  404  Not Found Some index files failed to download, they have been ignored, or old ones used instead.**

so then i went into synaptic - settings - repositories - other software and unchecked skype. now it runs with no errors. 

will i have any problems from not updating skype? is there another source for the repositories?

---

### Post by amjjawad on 2011-08-01
> **Hellfish03 said:**
> ok, i ran the update manager agian and this time i didn't get the whole long list, just this:

**Failed to fetch [http://download.skype.com/linux/repos/debian/dists/stable/non-free/binary-amd64/Packages.gz](http://download.skype.com/linux/repos/debian/dists/stable/non-free/binary-amd64/Packages.gz)  404  Not Found Some index files failed to download, they have been ignored, or old ones used instead.**

so then i went into synaptic - settings - repositories - other software and unchecked skype. now it runs with no errors. 

will i have any problems from not updating skype? is there another source for the repositories?

Check my previous post, I edited it.

Tick that option and refresh Synaptic ... see what will happen :)

---

### Post by Hellfish03 on 2011-08-01
tried it, still the same problem. seems to be a problem with that particular source? :confused:

---

### Post by amjjawad on 2011-08-01
> **Hellfish03 said:**
> tried it, still the same problem. seems to be a problem with that particular source? :confused:

I'm sorry, not sure what has to be done?!

---

### Post by Pimps on 2013-02-17
I've just registered to tell you how i managed to get right of that problem. 

my deb line was not in etc/apt/sources.list but in etc/apt/sources.list.d/addon-ppa.list

I edited the line out and saved.

then:

$ sudo apt-get update

Got a duplicate error from canonical software.

Gone to repositories and un-tick the canonical in duplicate (doesnt matter which one).

$ sudo apt-get update

again and it was fine. no more errors.

---

