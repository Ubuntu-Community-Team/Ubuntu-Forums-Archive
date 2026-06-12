---
title: "synaptic keeps trying to download a bad index"
date: 2009-12-01
forum: New to Ubuntu
---

### Post by aharown07 on 2009-12-01
Or maybe more properly, it's trying to download index from a bad source?
Here's the error
```
W: Failed to fetch http://archive.getdeb.net/ubuntu/dists/Gloria-getdeb/games/binary-i386/Packages  404 Not Found

```
Happens when I apt-get update

A little background: I've been trying to install a game warzone2100. Since the version avail in the regular repos. is old, I went to playdeb.net to try to download the latest in a deb compatible format.
They have these apt protocol links there. Well, these did nothing. Came to discover that I needed to install apturl. Did that.
Now I get the error above. Yes... I'm using Mint. Already posted there. 
But either way, here's the question
[B]How do I tell Synaptic to stop looking for this particular index?
[/B]Thanks.

---

### Post by yeats on 2009-12-01
In Ubuntu, there is a Software Sources menu item in the System -> Administration section, and I'm pretty sure it's the same in Linux Mint.  The will be an "Other Software" tab that allows you to select/deselect/delete your .deb sources.

---

### Post by aharown07 on 2009-12-01
Thanks. Software Sources isn't working for me either though. Have it installed but and can select from a menu, but it doesn't come up. I assume there is a file somewhere I can edit? But it's not the sources.list file, apparently. Already looked that over and can't see anything in it that would go looking for this index.

---

### Post by yeats on 2009-12-02
Software Sources is just a front end for changing the /etc/apt/sources.list and /etc/apt/sources.list.d files.  /etc/apt/sources.list.d is probably where your custom source is (it's a directory containing more sources.lists).

---

### Post by aharown07 on 2009-12-02
yep. thx
```
sudo gedit /etc/apt/sources.list.d/playdeb.list
```

---

