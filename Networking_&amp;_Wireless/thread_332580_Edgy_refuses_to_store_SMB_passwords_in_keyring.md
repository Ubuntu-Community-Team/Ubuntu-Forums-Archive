---
title: "Edgy refuses to store SMB passwords in keyring"
date: 2007-01-06
forum: Networking &amp; Wireless
---

### Post by LeSkip on 2007-01-06
Since installing Edgy I have never managed to store the password for my samba server in the keyring. Every time I access the share I have to enter my password. I click the check box to save the password in the keyring, but it never does!

This also means I can't use Rhythmbox or any other application which requires network access, they all fail, saying that the file could not be accessed.

Any resolve?

Thanks,
Skip

---

### Post by LeSkip on 2007-01-14
Further investigation into this reveals that it is a known bug in Gnome 2.16, per

[https://launchpad.net/ubuntu/+source/gnome-keyring/+bug/67189](https://launchpad.net/ubuntu/+source/gnome-keyring/+bug/67189)

And it's previously discussed in this forum at

[http://ubuntuforums.org/showthread.php?p=1745940](http://ubuntuforums.org/showthread.php?p=1745940)

Skip

---

