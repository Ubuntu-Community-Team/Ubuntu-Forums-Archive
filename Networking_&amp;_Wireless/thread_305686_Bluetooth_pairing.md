---
title: "Bluetooth pairing"
date: 2006-11-23
forum: Networking &amp; Wireless
---

### Post by iitywygms on 2006-11-23
Hey all.  I am using edgy 6.10, have all the latest updates.  I have bluetooth-gnome installed and working.  I can transfer files between my computer and one phone no problem.  My other phone wants to pair up with a pin.  I tried using the default 1234, and I tried changing the default pin in hcid.conf to 0000.  Still no luck.
It seems that at the very second I hit okay on my phone (after entering a pin) I get an error, obex-send "unable to connect to remote device"  this happens _right when I press the okay button_ on my phone.  Any Ideas?
Thanks

---

### Post by Jamesp on 2006-11-24
Hi, wish i could help you, i've had exactly the same problem and tried the same things - but no success. If you find an answer let me know!

---

### Post by iitywygms on 2006-11-25
Hopefull bump

---

### Post by A.Wingrove on 2006-11-27
Not sure if this will work for you, but I've just managed to get pairing working after an hour of struggling with similar symptoms. On my Edgy install, the bluez-passkey-gnome package was not installed. Once I installed this and rebooted, creating the connection from my SonyEricsson w810i worked first time :eek:

It might, therefore, be worth simply checking which bluez packages you have installed through System > Administration > Synaptic Package Manager.

Regards,
Alex

---

### Post by iitywygms on 2006-12-02
> **A.Wingrove said:**
> Not sure if this will work for you, but I've just managed to get pairing working after an hour of struggling with similar symptoms. On my Edgy install, the bluez-passkey-gnome package was not installed. Once I installed this and rebooted, creating the connection from my SonyEricsson w810i worked first time :eek:

It might, therefore, be worth simply checking which bluez packages you have installed through System > Administration > Synaptic Package Manager.

Regards,
Alex

Works now!  Thanks for the help, you rock!

---

