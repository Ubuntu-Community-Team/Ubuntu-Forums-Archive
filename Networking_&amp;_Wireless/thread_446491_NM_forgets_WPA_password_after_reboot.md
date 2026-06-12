---
title: "NM forgets WPA password after reboot"
date: 2007-05-17
forum: Networking &amp; Wireless
---

### Post by hondaman on 2007-05-17
Why do I have to type in my auth key for wpa every time I reboot?  Whats worse, about 30 seconds after I connect, the prompt comes up again to enter the password for authentication.  I can cancel that ok, but I think it should remember the password for an AP.

Can this be done?

---

### Post by spd106 on 2007-05-18
The WPA key should stay stored in gnome-keyring. If you want it to connect without entering your keyring password try following the steps here [https://help.ubuntu.com/community/WifiDocs/NetworkManager](https://help.ubuntu.com/community/WifiDocs/NetworkManager) under Automatic Keyring.

This requires that your login and keyring passwords are the same.

---

### Post by frisket on 2007-05-18
> **hondaman said:**
> Why do I have to type in my auth key for wpa every time I reboot?

I have a related problem: my WPA password for one network I use has changed. How amd where do I change it in nm-applet? 

When it tries (and of course fails) to connect, it puts up a window asking for the passphrase, but the only options are 128-bit/64-bit hex/64-bit ASCII.

If I try to start afresh with 'Connect to another network', the security menu only provides the same three options, whereas before it would let me set up WPA as well -- where's it all gone?

---

### Post by spd106 on 2007-05-18
The simplest way to do this would be to change the passphrase in System > Admin > Keyring Manager.

---

