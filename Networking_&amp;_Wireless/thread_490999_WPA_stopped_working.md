---
title: "WPA stopped working"
date: 2007-07-03
forum: Networking &amp; Wireless
---

### Post by SkyScrap on 2007-07-03
Sunday night it worked without problems, now network manager keeps asking for the WPA password and cannot connect any longer. Have there been some updates? I remember that the kernal was updated recently, but don't remember the exact date, can somebody tell me where the updater logs what has been updated when?

Andreas

---

### Post by Circus-Killer on 2007-07-03
are you sure its asking for your network password and not your keyring password?

after the very first time network-manager connects, it asks you to create a password for that keyring thingum. generally, it is this password that gets asked when the network starts up, and not the actual network password. hope that makes sense. :P

---

### Post by SkyScrap on 2007-07-03
> **Circus-Killer said:**
> are you sure its asking for your network password and not your keyring password?

Yes I am sure. :) The network manager somehow has problems with accessing the keyring and storing the WPA password there now. I deleted the password from the keyring, but NM has not put it there again. Now I have deleted the whole "default" keyring and will see what's happening after a reboot.

---

### Post by SkyScrap on 2007-07-03
ok, it's working again. 

strange ....

---

### Post by Atomic Dog on 2007-07-03
interesting.  This may help solve my own network manager quirks as it has also been asking me for WPA passwords for ssid's that I have connected to for months w/o problems.

---

### Post by walkerk on 2007-07-03
the easiest fix for network-manager is uninstalling it and installing/using wicd instead :)

---

