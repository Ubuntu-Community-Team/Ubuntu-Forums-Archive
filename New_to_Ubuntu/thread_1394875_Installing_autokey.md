---
title: "Installing autokey"
date: 2010-01-31
forum: New to Ubuntu
---

### Post by SirRedTooth on 2010-01-31
I reccently downloaded autokey.
In the install instructions I found this:

```
$Id: INSTALL 74 2009-07-04 15:38:27Z cdekter $

This application requires a full Debian package build - it cannot be installed using only
the setup.py script:

dpkg-buildpackage -us -uc
cd ../
sudo dpkg -i <buildpackagename>
```I am quite confused on where to start.
I have run the first command in the terminal "dpkg-buildpackage -us -uc" then went to the folder using cd.
But now I am stuck.
"sudo dpkg -i <buildpackagename>"

How do I know what to replace <buildpackagename> with?

---

### Post by Greenwidth on 2010-01-31
It's probably a lot easier to just add the ppa to your software sources and install through synaptic:
[https://launchpad.net/~cdekter/+archive/ppa](https://launchpad.net/~cdekter/+archive/ppa)

In Synaptic > settings tab > repositories

Other Software tab > Add
paste this: ppa:cdekter/ppa

Reload

Search for it, mark for installation

It also auto updates then as well.

Useful thread in the cafe:
[http://ubuntuforums.org/showthread.php?t=1052846&page=3](http://ubuntuforums.org/showthread.php?t=1052846&page=3)

---

### Post by SirRedTooth on 2010-01-31
Thanks for your help I managed to solve the problem.
But it would be better if I could understand the manual way of doing things =)

---

