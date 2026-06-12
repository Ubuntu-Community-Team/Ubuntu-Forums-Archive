---
title: "Update Manager error: 111 Connection refused"
date: 2009-05-26
forum: New to Ubuntu
---

### Post by rex_virtutis on 2009-05-26
I have been unable to use the update utility and synaptic.  Recently I was trying out various proxies such as tinyproxy, anon-proxy and squid3.  I got the following error message when I attempted to update my system.

> 
W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/intrepid-backports/Release.gpg](http://gb.archive.ubuntu.com/ubuntu/dists/intrepid-backports/Release.gpg)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/intrepid-backports/main/i18n/Translation-en_US.bz2](http://gb.archive.ubuntu.com/ubuntu/dists/intrepid-backports/main/i18n/Translation-en_US.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/intrepid-backports/restricted/i18n/Translation-en_US.bz2](http://gb.archive.ubuntu.com/ubuntu/dists/intrepid-backports/restricted/i18n/Translation-en_US.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/intrepid-backports/universe/i18n/Translation-en_US.bz2](http://gb.archive.ubuntu.com/ubuntu/dists/intrepid-backports/universe/i18n/Translation-en_US.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/intrepid-backports/multiverse/i18n/Translation-en_US.bz2](http://gb.archive.ubuntu.com/ubuntu/dists/intrepid-backports/multiverse/i18n/Translation-en_US.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/intrepid-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/intrepid-security/Release.gpg)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/intrepid-security/main/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/intrepid-security/main/i18n/Translation-en_US.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/intrepid-security/restricted/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/intrepid-security/restricted/i18n/Translation-en_US.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/intrepid-security/universe/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/intrepid-security/universe/i18n/Translation-en_US.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/intrepid-security/multiverse/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/intrepid-security/multiverse/i18n/Translation-en_US.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Some index files failed to download, they have been ignored, or old ones used instead.

and a similar error message when I tried to install firestarter from synaptic. I have tried the advice offered in [this thread]("http://ubuntuforums.org/showthread.php?t=1019320") but the problem persists.

Can anyone offer me some advice?  I am using Ubuntu 8.10.  Thanks in advance.

---

### Post by stephanvaningen on 2009-05-26
Try this:
[LIST]
[*][https://answers.launchpad.net/ubuntu/+faq/93](https://answers.launchpad.net/ubuntu/+faq/93)
[/LIST]

---

