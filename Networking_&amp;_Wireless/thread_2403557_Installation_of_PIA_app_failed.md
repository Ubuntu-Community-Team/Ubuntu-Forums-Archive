---
title: "Installation of PIA app failed"
date: 2018-10-13
forum: Networking &amp; Wireless
---

### Post by karebo on 2018-10-13
Wanted to install private internet access app on my new computer running Ubuntu 18.04 with Gnome.
This computer is intended to be a moviebox running P2P with my windows 10 PC where PIA is already installed.

Downloading and uncompression of PIA app v81 goes fine, but when running the install command
./pia-v81-installer-linus.sh
something goes wrong:
"E: cannot find package libappindicator1
E: cannot find package gconf2
Package installation failed. Please make sure that Your package manager is configuered correctly and is still supported by Your distribution vendor"

Other installations, for instance Chrome went fine

---

### Post by chili555 on 2018-10-13
Did you try:```
sudo apt update
sudo apt install libappindicator1 gconf2
```...and then try the installer again?

---

### Post by Bashing-om on 2018-10-13
karebo; Hey ...

in addition ->
server install where the universe repo is not enabled by default ?
> 
apt show libappindicator1

Section: universe/libs
<snip>


[INDENT][INDENT]my bit to try and help
[/INDENT][/INDENT]

---

