---
title: "winebudgetdedicated.com"
date: 2009-08-11
forum: New to Ubuntu
---

### Post by al.adab on 2009-08-11
hello,

I've just installed Wine 1.0.1 (from Synaptics) on Ubuntu 9.04 + the virtual Internet Explorer through IEs4Linux. At the software sources (third party) I notice two lines: "WineHQ - Ubuntu..." > (ticked) and "WineHQ - Ubuntu...(source code)" > (not ticked).

When I run a "sudo apt-get update" on Terminal I now get the following error: 

"Reading package lists... Done
W: GPG error: [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 58403026387EE263
W: You may want to run apt-get update to correct these problems"

Any idea? Thanks.

---

### Post by Tibuda on 2009-08-11
Follow the instructions at [http://www.winehq.org/download/deb](http://www.winehq.org/download/deb)

You can add the wine key by pasting this in a terminal:
```
wget -c http://wine.budgetdedicated.com/apt/387EE263.gpg -O- | sudo apt-key add -
```

We need an easier way to add repository keys in the GUI. It is possible but requires tons of clicking.

---

### Post by al.adab on 2009-08-11
Thanks. It worked.

---

