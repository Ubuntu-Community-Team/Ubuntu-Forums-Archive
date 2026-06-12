---
title: "can anyone tell me what is this error??"
date: 2011-03-30
forum: New to Ubuntu
---

### Post by Alif Radzi on 2011-03-30
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 7D2C7A23BF810CD5


everytime im updating through terminal this error will shown..how can i remove it ??

---

### Post by Thijk on 2011-03-30
it means your missing a GPG key. 

Open a terminal window and to this:

First you get the key you're missing

```
gpg --keyserver subkeys.pgp.net --recv  7D2C7A23BF810CD5
```
then you add it to your list of keys


```
gpg &#8211;export &#8211;armor 60D11217247D1CFF | sudo apt-key add -
```That should do it.

---

### Post by Paqman on 2011-03-30
> **Alif Radzi said:**
> W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) **hardy** Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 7D2C7A23BF810CD5


everytime im updating through terminal this error will shown..how can i remove it ??

It looks like you've still got an old PPA for Hardy Heron (Ubuntu 8.04) in your software sources. If you are still running Hardy, you need to upgrade right away, as support for Hardy ends in a  few weeks. You can upgrade to Lucid (the next LTS release) through Update Manager.

If you aren't running Hardy, just delete that PPA from your software sources.

---

