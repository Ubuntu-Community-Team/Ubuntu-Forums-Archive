---
title: "WPA Encryption"
date: 2008-04-27
forum: Networking &amp; Wireless
---

### Post by Gauvenator on 2008-04-27
In Ubuntu 8.04 my Linksys WRP54G 4.1 (rt61) works if there is no encryption.  I want to use WPA, but when I turn that encryption on in my router and I give Ubuntu the code and specify the type of encryption, it doesn't work.  I'm using System>Administration>Network.

---

### Post by kevdog on 2008-04-27
If you are using an rt61 module -- basically a ra chipset -- I dont think this chipset interfaces with the wpa_supplicant module.  I believe NM is trying to force your parameters through wpa_supplicant and this is causing a problem with your driver.

You can overcome this however by a few methods, adding changes to the /etc/network/interfaces file as per this thread:
[http://ubuntuforums.org/showthread.php?t=400236](http://ubuntuforums.org/showthread.php?t=400236)

or try installing rutilt as your card manager.

---

### Post by Gauvenator on 2008-04-27
I'm trying to connect manually now, but I get an error about "set" not being a command when I try something like this:

```
sudo iwpriv set AuthMode=WPAPSK
```

---

