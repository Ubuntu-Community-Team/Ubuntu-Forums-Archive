---
title: "update edgy"
date: 2007-02-03
forum: Networking &amp; Wireless
---

### Post by akjohn on 2007-02-03
downloaded edgy to dvd and installed from dvd without booting live. now when I enter "sudo apt-get update" , I get following errors in Terminal window.
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release.gpg
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy Release.gpg
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/restricted Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

What configuration needs changing to be able to update and install packages.
I can get to site when i copy link to Firefox.  and Internet access is good.

---

### Post by vigleik on 2007-02-03
It looks like apt is trying to update from a local source (the DVD?) instead of over the internet. You need to change your /etc/apt/sources.list.

---

