---
title: "Message Box: &quot;Requires installation of untrusted packages&quot;"
date: 2010-05-22
forum: New to Ubuntu
---

### Post by ramosdelpalo9 on 2010-05-22
I recently installed Ubuntu 10.04. I'm new at it.
When I go to the Ubuntu Software Center and try to install a program, the Message Box "Requires installation of untrusted packages". The message says 'The action would require the installation of packages from not authenticated sources.'

What does this means? And what I should do to be able to install programs?

Thank you.

RDP9

---

### Post by unmole on 2010-05-22
It's just an extra safety precaution. You can safely install any package from the official repositories.

---

### Post by ramosdelpalo9 on 2010-05-22
Then why I can't download any software?
And what are the official repositories?

---

### Post by bodhi.zazen on 2010-05-22
> **ramosdelpalo9 said:**
> Then why I can't download any software?
And what are the official repositories?

Repositories are collections of applications and source code.

The official repositories are the ones that came with Ubuntu when you installed Ubuntu.

See:

[https://help.ubuntu.com/community/InstallingSoftware](https://help.ubuntu.com/community/InstallingSoftware)

For a start.

The warning you are getting is because I assume you added a repository or ppa without adding the gpg key :

[http://wiki.debian.org/SecureApt](http://wiki.debian.org/SecureApt)

[https://help.launchpad.net/Packaging/PPA/InstallingSoftware](https://help.launchpad.net/Packaging/PPA/InstallingSoftware)

Run ```
sudo apt-get update
```

and post any error messages.

Otherwise hard to know your exact problem.

---

### Post by ramosdelpalo9 on 2010-05-22
Thanks for the links. Looks like I just had to request the key it already had.. I think, not sure. But it works. :D

---

### Post by ubeautu on 2010-06-20
"Runing in terminal ```
sudo apt-get update
```"

Fixed it. Thanks

---

### Post by rulitawyn on 2010-10-18
hey im having almost the exact same problem only i am on maverick meercat 10.10 and this is the error message when i try $ sudo apt-get update

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/maverick/Release.gpg)  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick/main/i18n/Translation-en.bz2](http://archive.ubuntu.com/ubuntu/dists/maverick/main/i18n/Translation-en.bz2)  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://archive.getdeb.net/ubuntu/dists/maverick-getdeb/Release.gpg](http://archive.getdeb.net/ubuntu/dists/maverick-getdeb/Release.gpg)  Could not connect to archive.getdeb.net:80 (208.98.166.60). - connect (110: Connection timed out)

W: Failed to fetch [http://archive.getdeb.net/ubuntu/dists/maverick-getdeb/games/i18n/Translation-en.bz2](http://archive.getdeb.net/ubuntu/dists/maverick-getdeb/games/i18n/Translation-en.bz2)  Unable to connect to archive.getdeb.net:http:

W: Failed to fetch [http://archive.getdeb.net/ubuntu/dists/maverick-getdeb/games/i18n/Translation-en_US.bz2](http://archive.getdeb.net/ubuntu/dists/maverick-getdeb/games/i18n/Translation-en_US.bz2)  Unable to connect to archive.getdeb.net:http:

W: Failed to fetch [http://dl.google.com/linux/chrome/deb/dists/stable/Release.gpg](http://dl.google.com/linux/chrome/deb/dists/stable/Release.gpg)  Something wicked happened resolving 'dl.google.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://archive.getdeb.net/ubuntu/dists/maverick-getdeb/games/source/Sources.gz](http://archive.getdeb.net/ubuntu/dists/maverick-getdeb/games/source/Sources.gz)  Unable to connect to archive.getdeb.net:http:

W: Failed to fetch [http://archive.getdeb.net/ubuntu/dists/maverick-getdeb/games/binary-amd64/Packages.gz](http://archive.getdeb.net/ubuntu/dists/maverick-getdeb/games/binary-amd64/Packages.gz)  Unable to connect to archive.getdeb.net:http:

E: Some index files failed to download, they have been ignored, or old ones used instead.
rulitawyn@Oakenheart:~$

---

### Post by nyamunga on 2010-10-27
Thanks you saved my day

---

### Post by aattwwss on 2011-09-05
Thank you very much.

---

### Post by wildmanne39 on 2012-08-05
If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

