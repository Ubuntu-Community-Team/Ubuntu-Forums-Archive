---
title: "Install iBall 300m Wireless usb adapter on ubuntu 17.04?"
date: 2018-08-25
forum: Networking &amp; Wireless
---

### Post by endomondo1980 on 2018-08-25
Hello i have iBall 300m Wireless USB Adapters that i would like to use on Ubuntu.
I have the Disc with the Linux drivers. I do not know how to get Ubuntu to work with this device.
Or simply to install these drivers on Ubuntu.
[IMG]http://i429.photobucket.com/albums/qq12/pinso/Ubuntu1.jpg[/IMG]

I am not too fond of using cmdline but that is what Linux is about, installing and updating softwares from cmdline.
Not too familiar in that area, but i would be glad if someone could help me.
How do i install the drivers in Ubuntu.

The How-to-install.txt contains these lines:
```
Driver for Realtek chipset RTL8192EU: how-to install

1. Download the driver package Realtek-RTL8192EU-driver.tar.gz into the folder Downloads.

2. First unpack it in the terminal, because it's a compressed folder with files. In the terminal (use copy/paste):
cd Downloads && tar xvzf ~/Downloads/Realtek*.tar.gz

3. Now go to the uncompressed folder: in the terminal (use copy/paste):
cd install_folder

4. Finally: the actual installation. In the terminal (use copy/paste):
sudo ./install.sh

5. Plug the wireless dongle with the Realtek chipset into you computer: it should be functional now.
```

This is only confusing me more. Why does it need a Realtek-RTL8192EU-driver.

---

### Post by oldos2er on 2018-08-25
17.04 is [EOL]("https://wiki.ubuntu.com/Releases"), you really should install a supported version.

---

### Post by endomondo1980 on 2018-08-26
Just downloaded Ubuntu 16.04 and made a live usb.
Surprisingly it recognized all the drivers for iBall 300m and TP-Link 300m Wireless. **Ubuntu 18.04 LTS** 32bit is not available. Only for 64bit.
Ubuntu still feels like a handicapped OS.

---

### Post by pauljw on 2018-08-27
> **endomondo1980 said:**
> Just downloaded Ubuntu 16.04 and made a live usb.
Surprisingly it recognized all the drivers for iBall 300m and TP-Link 300m Wireless. **Ubuntu 18.04 LTS** 32bit is not available. Only for 64bit.
Ubuntu still feels like a handicapped OS.

Heheheh... ya, it has to be so that users that are afraid of the cli can still write insults in our forums.

---

### Post by coffeecat on 2018-08-27
Not a chat thread.

*Thread moved to **Networking & Wireless**.*

---

