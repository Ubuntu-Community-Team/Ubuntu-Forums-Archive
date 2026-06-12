---
title: "Bluetooth in 8.10 (Kubuntu)?"
date: 2008-10-25
forum: Networking &amp; Wireless
---

### Post by bertilow on 2008-10-25
After trying in vain for a few hours to get my bluetooth mouse running in Kubuntu 8.10 RC1 I've come to the conclusion that there simply is no support for bluetooth at all in Kubuntu 8.10. Is this correct?

---

### Post by corck on 2008-10-30
no, its not (yet)
[http://www.ubuntu.com/getubuntu/releasenotes/810#Kubuntu%20Bluetooth%20support](http://www.ubuntu.com/getubuntu/releasenotes/810#Kubuntu%20Bluetooth%20support)

---

### Post by wpiter on 2008-11-06
Currently in Kubuntu 8.10 you can add bluetooth support via the adept package manager. You need to install Bluez-compat. Now after installation, you open a shell and type 'sudo hidd --search'. A connection to your bluetooth mouse/keyboard is now possible.

Succes.

By the way, do read the notes that come with Bluez-compat.

---

### Post by jwillar on 2008-11-11
Works good, however it all stops working after a system reboot.  How do I make it permeate?

---

