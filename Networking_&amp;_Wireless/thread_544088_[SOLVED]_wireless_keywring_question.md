---
title: "[SOLVED] wireless keywring question"
date: 2007-09-05
forum: Networking &amp; Wireless
---

### Post by fontenot_1031 on 2007-09-05
My wireless has a  WPA-PSK login.  When I start Ubuntu, it askes me for a password to open the keyring that contains the pass-phrase.  Is it possible to manipulate the program that askes me for the keyring password so that it will automatically log me onto my network?

---

### Post by spd106 on 2007-09-07
Yep, install the lib-pamkeyring package and add the following line to the end of your /etc/pam.d/gdm file

```
@include common-pamkeyring

```

It's probably a good idea to read the Network Manager page in the Ubuntu help wiki
[https://help.ubuntu.com/community/WifiDocs/NetworkManager](https://help.ubuntu.com/community/WifiDocs/NetworkManager)

---

### Post by digitalbenji on 2007-09-07
sort of on the same topic - does anyone know how to delete the keyring?

---

### Post by peebly on 2007-09-07
I solved this problem by using a better network manager.

Wicd logs on for you no need to use other apps to remember wpa/wep keys etc..

One application does it all.

[http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

---

### Post by spd106 on 2007-09-07
> **digitalbenji said:**
> sort of on the same topic - does anyone know how to delete the keyring?

You can delete keyrings in the Keyring Manager, under System -> Administration menu. Alternatively delete them directly from the ~/.gnome2/keyrings/ directory.

---

### Post by digitalbenji on 2007-09-10
cool, thanks spd106.  I like to know where things live.

---

