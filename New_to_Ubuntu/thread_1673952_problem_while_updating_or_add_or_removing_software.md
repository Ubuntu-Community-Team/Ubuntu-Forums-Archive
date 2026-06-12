---
title: "problem while updating or add or removing software"
date: 2011-01-23
forum: New to Ubuntu
---

### Post by c.sourav on 2011-01-23
[SIZE=4]While updating in terminal using "[/SIZE][SIZE=4]sudo apt-get update"[/SIZE] [SIZE=4]after getting the list a notice is coming

"W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY [KEY 16 alphanumerics ]"[/SIZE]


[SIZE=4]Also while installing or uninstalling a software it is successfully getting added or removed but a error notice showing [/SIZE]
[SIZE=4]
"[/SIZE][SIZE=5][SIZE=4]E:firmware-b-43[/SIZE][/SIZE][SIZE=4]-installer: subprocess installed[/SIZE] [SIZE=4]post installation script returned error exit status 4"[/SIZE]

[SIZE=4]please help[/SIZE].

---

### Post by oldos2er on 2011-01-23
To get the gpg key, open a terminal and run ```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys KEYID
``` where KEYID is the number shown in the error message.

Not sure about the second error, but you could try ```
sudo dpkg --configure -a
```

---

