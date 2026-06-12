---
title: "Enter password for default keyring to unlock"
date: 2007-02-05
forum: Networking &amp; Wireless
---

### Post by SnowPunk98 on 2007-02-05
I installed NetworkManager and got my wireless working. However every time I log in it prompts me with "Enter password for default keyring to unlock" and won't take my password or the WPA key. 

Does anyone know how I make this popup go away and log me into my wireless network automatically?

---

### Post by kylevan on 2007-02-05
[http://ubuntuforums.org/showthread.php?t=192281&highlight=GNOME+session](http://ubuntuforums.org/showthread.php?t=192281&highlight=GNOME+session)

---

### Post by SnowPunk98 on 2007-02-06
I tried that but when I reboot the same thing happens :(

---

### Post by SnowPunk98 on 2007-02-08
I used keyring-manager-gnome to look at my keyring, I have the default one and one called session1. I'm not sure why I have 2 but I think this might be the problem. Would it be safe to delete both and have it create a new one.

Also there is a CVS version of PAM that I want to try that should reset the password, how risky is that?

---

