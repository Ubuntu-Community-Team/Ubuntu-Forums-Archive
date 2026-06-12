---
title: "bluetooth usb adapter on edgy"
date: 2007-03-29
forum: Networking &amp; Wireless
---

### Post by absol_of_doom on 2007-03-29
I recently bought a iogear bluetooth usb adapter.  I have searched google like a madman, but I can't figure out how to install it on edgy although I think it might have something to do with something called bluez.  (btw, I have already tried using wine to install it, doesnt work)

---

### Post by jrw6 on 2007-04-01
I'm pretty sure that the "bluez" you've seen referred to is the "bluez-utils" package, which is an Ubuntu package you can install, not a Windows program you need to run via WINE.  In any case I'd like to bump this thread because I've recently upgraded to Feisty.  The problem is that when I load the "Bluetooth filesharing" program and plug in my USB bluetooth adapter, nothing happens. :( 

No popup telling me the computer has become visible, nothing.  This worked fine in Edgy.  Right now I am having to plug the bluetooth adapter into my laptop (an old Apple iBook G3 :-D) which is running Edgy, transfer the files to it and them ftp them over to my desktop.  Not really ideal.  Can someone help us?!

---

### Post by polomint on 2007-04-01
To get bluetooth support, you'll need the following packages:

libbluetooth2
bluez-pin
bluez-utils
bluez-passkey-gnome
gnome-bluetooth

and kdebluetooth if your're using KDE.

you'll need to add bt-applet to the gnome session if it's not added already. this should work following a restart. 

in my experience, bluetooth support s**ks immensely in edgy. feisty, however, is much better in handling bluetooth.

@jrw6, you might want to try clearing all files in /var/lib/bluetooth, then restart the bluetooth service by:

```
sudo /etc/init.d/bluetooth restart
```

i've had a similar problem of device being not discoverable and the above solves the problem.

---

