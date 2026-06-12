---
title: "install banshee 2 and Gnome3?"
date: 2011-04-06
forum: New to Ubuntu
---

### Post by Robing Goodfellow on 2011-04-06
Running Maverick on a 64 bit HP G62 laptop.  Tried Natty, didn't like it, keeping Maverick.

I have banshee 1.8 and Gnome 2.not.really.sure installed.

I want to install the new banshee 2 and am interested in trying Gnome 3.

I did

```

[COLOR=#0000ff]sudo add-apt-repository ppa:banshee-team/ppa
sudo apt-get update
sudo apt-get install banshee[/COLOR]

```

but got back that the most current version is already installed.

Any guidance on how to install these, or should I wait a bit?

regards, Richard

---

### Post by andrewthomas on 2011-04-07
```
**Publishing details**
              Published       6 minutes ago                   **Changelog**
         **banshee (2.0.0-1ubuntu1~hyper1+maverick) **maverick; urgency=low    * Merge from Natty, remaining changes:     - [c20e6c9] Revert "Drop libindicate0.1-cil-dev"     - [c31d919] Revert rename of libwebkit-dev  -- Chow Loong Jin <[hyperair@ubuntu.com]("https://launchpad.net/%7Ehyperair")>   Thu, 07 Apr 2011 00:26:15 +0800
```[https://launchpad.net/~banshee-team/+archive/ppa/+packages]("https://launchpad.net/%7Ebanshee-team/+archive/ppa/+packages")

A new package was just published. The debs should be built pretty soon.

---

