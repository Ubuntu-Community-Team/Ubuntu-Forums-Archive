---
title: "Bluetooth &amp; Kubuntu Edgy"
date: 2006-11-18
forum: Networking &amp; Wireless
---

### Post by josh2112 on 2006-11-18
My bluetooth seems to be broken in Edgy; my mobile devices are not being discovered, nor is my bluetooth dongle being discovered by the mobile devices.  It worked fine in Breezy.  Whenever I plug in the dongle I get a popup that says:

> To use the kbtobexsrv service, some other devices might require a modified class number for your bluetooth adapter in /etc/bluetooth/hcid.conf. 
Currently the class is set to 0x0. We suggest you change this to something like 0x100000 instead and restart BlueZ's hcid. The service will be activated anyway.

Ok, so I found "Local device class" in hcid.conf... it was 0x3e0100, but I changed it to 0x100000 as was suggested, and issued an /etc/init.d/bluetooth restart, removed and reinserted teh dongle.

Now here's the thing "bluetooth:/" does not find any devices, but "hcitool inq" does!  Why is KDE's bluetooth module not working for me and what can I do to fix it?

Thanks,
  Josh

---

### Post by Amitava on 2006-11-19
Is SELinux turn on? if yes then try configuring it by excluding the blutooth connection from it...keep trying.

---

### Post by meldroc on 2006-12-31
How do you do that?  For that matter, how do you make KDE bluetooth work at all?

---

### Post by devnet on 2006-12-31
I'm having the same issue on this one everyone.  Bluetooth is as buggy as a North Carolina swamp on this.

What's up with this?  This keyboard and mouse have been a no-brainer on just about every distro out there...what's up with edgy?

---

### Post by lilmienboy on 2007-01-02
for some reason when i open up the bluetooth program and try to look for my cellphone it doesn't show anything but if i sent a file to my computer ,the bluetooth 4rm my computer picks it up. im not sure whats up with my too

---

