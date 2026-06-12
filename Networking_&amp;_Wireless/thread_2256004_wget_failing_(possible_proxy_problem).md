---
title: "wget failing (possible proxy problem)"
date: 2014-12-09
forum: Networking &amp; Wireless
---

### Post by david.aldrich.ntml on 2014-12-09
Hi

I am running Ubuntu 10.04 (Lucid). I want to download the Subversion 1.7 package from the WanDisco repository:

$ echo "deb [http://opensource.wandisco.com/ubuntu](http://opensource.wandisco.com/ubuntu) lucid svn17" | sudo tee /etc/apt/sources.list.d/svn.list
$ sudo wget [http://opensource.wandisco.com/wandisco-debian.gpg](http://opensource.wandisco.com/wandisco-debian.gpg) -O- | sudo apt-key add -
--2014-12-09 10:25:08--  [http://opensource.wandisco.com/wandisco-debian.gpg](http://opensource.wandisco.com/wandisco-debian.gpg)
Resolving opensource.wandisco.com... 54.247.191.119
Connecting to opensource.wandisco.com|54.247.191.119|:80... failed: Connection timed out.
Retrying.

The url works fine from my PC browser.  I guess wget is failing in because I am behind a proxy but I have done:

export https_proxy=http://<proxy url>:<port>
export http_proxy=http://<proxy url>:<port>

Any idea what's wrong please?

David

---

### Post by david.aldrich.ntml on 2014-12-09
Fixed. Should not have run wget as sudo, because proxy environment variables weren't active in sudo profile.

---

