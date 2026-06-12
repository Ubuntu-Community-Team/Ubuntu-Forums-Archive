---
title: "sudo-apt get update error"
date: 2009-09-08
forum: New to Ubuntu
---

### Post by al.adab on 2009-09-08
I'm using opera - last time I opened the browser I was asked if I want update it to a new version. I initially clicked yes and then changed my mind. Now when I run sudo-apt-get-update I get the following error msg: 

[I]Fetched 190B in 0s (250B/s)
Reading package lists... Done
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://deb.opera.com](http://deb.opera.com) stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY F9A2F76A9D1A0061

W: Failed to fetch [http://deb.opera.com/opera/dists/stable/Release](http://deb.opera.com/opera/dists/stable/Release)  

W: Some index files failed to download, they have been ignored, or old ones used instead.
W: You may want to run apt-get update to correct these problems[/I]

What shall I do?

---

### Post by Joshua Lückers on 2009-09-08
You could try the steps explained at the Opera .deb Repository [website]("http://deb.opera.com/").

---

### Post by al.adab on 2009-09-08
...but I don't want the new version or to install any version of opera. I'd just like to get rid of this error msg at terminal...

---

### Post by al.adab on 2009-09-08
...trying to install the key now...

---

### Post by sonu 1807 on 2009-09-08
In System --> Administration --> Software Sources, un-check the opera deb source and then run update

---

