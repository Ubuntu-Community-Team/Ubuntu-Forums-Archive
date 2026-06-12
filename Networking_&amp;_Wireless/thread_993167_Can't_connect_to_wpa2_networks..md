---
title: "Can't connect to wpa2 networks."
date: 2008-11-25
forum: Networking &amp; Wireless
---

### Post by epqr on 2008-11-25
So im trying to connect to my newly conifgurated WPA router. But ubuntu won't allow me to put in a WPA2 encrryption/password. its just give me option of three different WPA alternatives (WPA 64bit HEX, and so on.). How can i fix this?

---

### Post by spd106 on 2008-11-25
I suggest that you first make sure that the AP is set to broadcast it's SSID info. That often causes difficulty in trying to guess the encryption type. It's also a good idea to set the encryption type to just WPA rather than WPA/WEP mixed mode, unless you need the WEP compatibility for an old device.

Next try the WPA option with your key, if you haven't already.

If that still fails try adding a new network with the same name. To do this right-click the applet and select Edit Connections... Then on the Wireless tab click on Add.. and fill in the details.

---

### Post by kevdog on 2008-11-25
Can you type the following:

sudo iwlist <interface ie wlan0> auth

Thanks

---

