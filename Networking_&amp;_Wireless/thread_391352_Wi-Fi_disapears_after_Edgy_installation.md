---
title: "Wi-Fi disapears after Edgy installation"
date: 2007-03-23
forum: Networking &amp; Wireless
---

### Post by PryGuy on 2007-03-23
Good day, Everyone!!!

I have the following problem: my Acer 292ELC notebook fails to install from the Egdy LiveCD. So the only choice for me is a text-based install. The installations runs smooth and it's even more useful for me. It detects my D-Link DWL-G650 wireless Wi-Fi PCIMCIA adapter during the installation and gives me a choice to configure it and everything goes smooth also. Then I continue my setup without any problem, but when I reboot into the newly installed Edgy *there's no my Wi-Fi adapter!!!* Please help!

---

### Post by spd106 on 2007-03-23
Yep, filed this [bug]("https://bugs.launchpad.net/ubuntu/+source/debian-installer/+bug/63006") before Edgy was even released.

```
sudo apt-get install linux-restricted-modules-generic
```

The files are on the CD and can also be installed through Synaptic.

Afterwards you can either restart or run
```
sudo modprobe ath_pci
```

---

### Post by PryGuy on 2007-04-06
Tanks you, I solved it myself already...:)

---

