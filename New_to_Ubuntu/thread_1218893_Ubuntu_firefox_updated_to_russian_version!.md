---
title: "Ubuntu firefox updated to russian version!"
date: 2009-07-21
forum: New to Ubuntu
---

### Post by pagheca on 2009-07-21
Hi,

I was trying to update Firefox to 3.5 in Jaunty. I attempted several suggestion but all of them ended with a problem with the PGP key like this:

W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A6DCF7707EBC211F
W: GPG error: [http://dl.google.com](http://dl.google.com) stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A040830F7FAC5991
W: Failed to fetch [http://no.archive.ubuntu.com/dists/edgy/main/binary-i386/Packages](http://no.archive.ubuntu.com/dists/edgy/main/binary-i386/Packages)  404 Not Found

(note that I followed all the procedures, including the sudo apt-key ... command).

At the end I tried by using ubuntuzilla:

ubuntuzilla.py -a install -p firefox

Apparently everything went ok. I selected uk as the language (option 72) and went ahead.

When I started mozilla it was actually version 3.5, but in Cyrillic!!! I'm able to read some Russian but I would like to go back to the English version and it's really difficult because I can't easily search for hints and tips. That's why I'm writing to this forum rather than to the more appropriate ubuntuzilla or firefox forum....

Can someone tell me what is going on and how to go back to the original version please? Thanks very much!

pagheca

---

### Post by Sef on 2009-07-21
I would uninstall firefox  and reinstall it from the [Ubuntu PPA]("https://launchpad.net/%7Eubuntu-mozilla-daily/+archive/ppa").

Moved to ABT.

---

### Post by nothingspecial on 2009-07-21
> **pagheca said:**
> Hi,

I was trying to update Firefox to 3.5 in Jaunty. I attempted several suggestion but all of them ended with a problem with the PGP key like this:

W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A6DCF7707EBC211F
W: GPG error: [http://dl.google.com](http://dl.google.com) stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A040830F7FAC5991
W: Failed to fetch [http://no.archive.ubuntu.com/dists/edgy/main/binary-i386/Packages](http://no.archive.ubuntu.com/dists/edgy/main/binary-i386/Packages)  404 Not Found

(note that I followed all the procedures, including the sudo apt-key ... command).

At the end I tried by using ubuntuzilla:

ubuntuzilla.py -a install -p firefox

Apparently everything went ok. I selected uk as the language (option 72) and went ahead.

When I started mozilla it was actually version 3.5, but in Cyrillic!!! I'm able to read some Russian but I would like to go back to the English version and it's really difficult because I can't easily search for hints and tips. That's why I'm writing to this forum rather than to the more appropriate ubuntuzilla or firefox forum....

Can someone tell me what is going on and how to go back to the original version please? Thanks very much!

pagheca

I`ll bet you did the same thing as me. When you chose your location during the install did you choose uk, assuming that meant United Kingdom?

Opps that stands for Ukraine. Run the script again and choose en-gb instead. 

Did I feel stupid?\\:D/

---

### Post by pagheca on 2009-07-21
Yep... I realized that suddenly. UK = Ukraine, not United Kingdom. The correct selection is 13. 

I really feel stupid... sorry about bothering people here :D:D:D:D

pagheca

---

### Post by nothingspecial on 2009-07-21
I have quite a long list of "stupid things I have done whilst using linux". I may post them in the cafe one day.

---

