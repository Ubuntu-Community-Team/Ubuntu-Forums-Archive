---
title: "No wireless connection until login"
date: 2007-09-22
forum: Networking &amp; Wireless
---

### Post by Drasla on 2007-09-22
I recently ran an 'apt-get upgrade', which appears to have changed around my network settings a bit.

I am on a wireless network with WPA2 encryption that I'm connecting to with ndiswrapper.  Previously, my computer would automatically connect upon boot.  Now, I can only connect after logging in and entering the nm-applet keyring password.

Does anyone know how I can get Ubuntu to revert back to connecting to my network automatically?  This computer is primarily used as a server, so this functionality is relatively important.

Thanks.

---

### Post by Drasla on 2007-09-22
Nevermind, got it.

For some reason, the update changed my wireless interface's name from 'ath0' to 'wlan0'.  I just had to update /etc/network/interfaces to reflect the change.

---

