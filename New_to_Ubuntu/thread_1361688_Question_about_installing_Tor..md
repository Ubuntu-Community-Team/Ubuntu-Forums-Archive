---
title: "Question about installing Tor."
date: 2009-12-22
forum: New to Ubuntu
---

### Post by suomalainen on 2009-12-22
Ubunteros,

I want to install Tor and have reviewed the community documentation. The process looks to be straight forward. However, I do have a question about a few steps and maybe somebody can guide me appropriately.

I visited:

[https://help.ubuntu.com/community/TOR](https://help.ubuntu.com/community/TOR)

Under "Installing Tor" directions for adding the repositories to your /etc/apt/sources.list file are given. Then the documentation covers "PGP keys".

On the other hand, there is a link called "Tor installation documentation" on the same page which leads you to:

[https://www.torproject.org/docs/debian](https://www.torproject.org/docs/debian)

And then guides the user through the installation process.

My question is do I need to use both websites to do the install or not?

I'm kinda lost on adding the "repositories to your /etc/apt/sources.list file" AND "PGP keys" as described in the Community documentation. Aren't these automatically added if I follow the Tor website instructions???

Your advice is appreciated. Especially your feelings about Tor if you are a user.

Thank You.

---

### Post by ikt on 2009-12-22
> **suomalainen said:**
> My question is do I need to use both websites to do the install or not?

I'm kinda lost on adding the "repositories to your /etc/apt/sources.list file" AND "PGP keys" as described in the Community documentation. Aren't these automatically added if I follow the Tor website instructions???


You shouldn't need to use both,

If you have ubuntu 9.10 add these lines to your sources.list:


> deb [http://deb.torproject.org/torproject.org](http://deb.torproject.org/torproject.org) karmic main
deb-src [http://deb.torproject.org/torproject.org](http://deb.torproject.org/torproject.org) karmic main

and then open terminal and use the torproject pgp keys

> gpg --keyserver keys.gnupg.net --recv 886DDD89
gpg --export A3C4F0F979CAA22CDBA8F512EE8CBC9E886DDD89 | sudo apt-key add -
sudo apt-get update
sudo apt-get upgrade

then run:

>  sudo apt-get update
 sudo apt-get install tor tor-geoipdb

and you're done.

---

### Post by suomalainen on 2009-12-22
Thanks for the reply itk.

Actually, I'm using 8.04 LTS.

F.Y.I> Tor isn't the only program required for this install as the documentation points out.

---

### Post by lotharmat on 2009-12-22
> **suomalainen said:**
> Thanks for the reply itk.

Actually, I'm using 8.04 LTS.

F.Y.I> Tor isn't the only program required for this install as the documentation points out.

In that case I think you just need to change the karmic to hardy

---

