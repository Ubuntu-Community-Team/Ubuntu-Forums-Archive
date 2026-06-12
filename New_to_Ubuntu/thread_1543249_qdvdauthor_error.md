---
title: "qdvdauthor error"
date: 2010-07-31
forum: New to Ubuntu
---

### Post by m3t3ors on 2010-07-31
hi im running ubu ntu 10.04 on my dell latitude d520 and trying to encode and burn a movie to dvd using dvdauthor but received the following error.

There are newer versions available for :
Masks: The masks library is missing on your system.
Buttons: The button library is missing on your system.
Transitions: The transitions library is missing on your system.
Do you want to download the latest libraries now ?
Could not locate any GUI for root
Please execute the following commands as root.
```
#!/bin/bash cd /tmp wget [http://qdvdauthor.sourceforge.net/data/masks.tar.bz2](http://qdvdauthor.sourceforge.net/data/masks.tar.bz2) -O masks.tar.bz2 cd /usr/share/qdvdauthor/ tar -xjf /tmp/masks.tar.bz2 cd /tmp wget [http://qdvdauthor.sourceforge.net/data/buttons.tar.bz2](http://qdvdauthor.sourceforge.net/data/buttons.tar.bz2) -O buttons.tar.bz2 cd /usr/share/qdvdauthor/ tar -xjf /tmp/buttons.tar.bz2 cd /tmp wget [http://qdvdauthor.sourceforge.net/data/alpha_trans.tar.bz2](http://qdvdauthor.sourceforge.net/data/alpha_trans.tar.bz2) -O alpha_trans.tar.bz2 cd /usr/share/qdvdauthor/ tar -xjf /tmp/alpha_trans.tar.bz2 
```


when i try running the commands in a terminal it asks for password?
is the root password my log in password?

---

### Post by cariboo on 2010-08-01
The short answer is yes. By default the root account is disabled in Ubuntu. You have to manually add a password. You can do the same thing as running as root, by typing:

```
sudo -i
```

at the prompt. This opens a root terminal.

---

