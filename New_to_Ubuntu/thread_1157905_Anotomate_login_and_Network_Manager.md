---
title: "Anotomate login and Network Manager"
date: 2009-05-13
forum: New to Ubuntu
---

### Post by dunbrokin on 2009-05-13
I want to set up my old PC to automatically log in and connect to the internet and send weather data. The automatic log in is not a problem...but it keeps asking me for a password and authentication before it will connect to the net. I have tried fiddling around with the NM setting in Authorization...but that does not seem to work either...any suggestions please?

---

### Post by SteveDee on 2009-05-13
> **dunbrokin said:**
> I want to set up my old PC to automatically log in and connect to the internet and send weather data. The automatic log in is not a problem...but it keeps asking me for a password and authentication before it will connect to the net. I have tried fiddling around with the NM setting in Authorization...but that does not seem to work either...any suggestions please?


When set to auto-login, Gnome will still ask for a password for your Wifi. The only answer is to set a blank password. If you clear the keyring file (as below) then restart, enter the Wifi keyphrase when requested. But for keyring password just accept a blank.

The user keyring is held in $Home/.gnome2/keyrings/default.keyring
Deleting this file forces a request for fresh network keyphrase next time system starts.

I hope this helps.

---

### Post by dunbrokin on 2009-05-13
Thank you, I will give that a try...

---

