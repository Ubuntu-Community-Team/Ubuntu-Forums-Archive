---
title: "Cant Upgrade to Karamic kola"
date: 2009-10-13
forum: New to Ubuntu
---

### Post by HamzahQaisar on 2009-10-13
I cant get my ubuntu to upgrade :( :(

this is the command im using

sudo update-manager -d

and this error comes up...

before that this comes up

Third party sources disabled

Some third party entries in your sources.list were disabled. You can re-enable them after the upgrade with the 'software-properties' tool or your package manager.

and then..
Error during update

A problem occurred during the update. This is usually some sort of network problem, please check your network connection and retry.

W:Failed to fetch [http://security.ubuntu.com/ubuntu/dists/karmic-security/Release](http://security.ubuntu.com/ubuntu/dists/karmic-security/Release)  Unable to find expected entry  multivers/source/Sources in Meta-index file (malformed Release file?)
, E:Some index files failed to download, they have been ignored, or old ones used instead.

and then it stops!!!!

---

### Post by perlsyntax on 2009-10-13
it work for me.Make sure yoou have a new install and then try it.


works for me.

---

### Post by HamzahQaisar on 2009-10-13
> **perlsyntax said:**
> it work for me.Make sure yoou have a new install and then try it.


works for me.

I dont wanna go downloading it i wanna "update" it

---

### Post by sandyd on 2009-10-13
> **HamzahQaisar said:**
> I cant get my ubuntu to upgrade :( :(

this is the command im using

sudo update-manager -d

and this error comes up...

before that this comes up

Third party sources disabled

Some third party entries in your sources.list were disabled. You can re-enable them after the upgrade with the 'software-properties' tool or your package manager.

and then..
Error during update

A problem occurred during the update. This is usually some sort of network problem, please check your network connection and retry.

W:Failed to fetch [http://security.ubuntu.com/ubuntu/dists/karmic-security/Release](http://security.ubuntu.com/ubuntu/dists/karmic-security/Release)  Unable to find expected entry  multivers/source/Sources in Meta-index file (malformed Release file?)
, E:Some index files failed to download, they have been ignored, or old ones used instead.

and then it stops!!!!
sudo apt-get clean

---

