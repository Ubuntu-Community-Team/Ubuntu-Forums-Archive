---
title: "Modem authentication hangs"
date: 2007-10-26
forum: Networking &amp; Wireless
---

### Post by EmilyRose on 2007-10-26
I just got a system 76 gazelle laptop and bought a zoom Model 3095F V.92 USB Mini External modem. I installed the drivers, and it dials just fine, sends un/pw... seems to connect, but gnome ppp just hangs on "authenticating" and it never actually connects. I tried using WVDail straight, and it does the same thing. It does give a couple erros about not having permission to edit pap-secrets and chap-secrets, but goes on...

---

### Post by EmilyRose on 2007-10-31
So... theres a secondary/follow-up problem too. 

The modem works, most ot f the time. But, when you first start the computer, you usually have to unplug it from the computer and plug it back in once or twice for it to be 'found' and accepted. Its not a huge deal, but it is a bit of a bummer and PITA.

Gnome PPP just says that theres no such device, over and over again... Does this sound like a computer issue or a modem issue??

Thanks in advance!!

---

### Post by mpokrywka on 2007-10-31
I suspect "udev" is the problem - when system boots or when you (re)connect usb devices they are sometimes given different "names", and in your configuration (Gnome PPP) there is hardcoded device name, for example /dev/ttyUSB0. You can configure udev to always give same name for your modem. First check usb vendor and product id - open Terminal and type:
```
lsusb
```
You should get something like:
```
Bus 005 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000
Bus 001 Device 004: ID **046d**:**c50a** Logitech, Inc.
Bus 001 Device 001: ID 0000:0000
```
Those bold "numbers" are important, of course in your case they will be different and there should be mentioned "Zoom" instead of "Logitech".
Next, add udev rule to make your modem name permanent:
```
sudo gedit /etc/udev/rules.d/45-usb-modem.rules
```
add line:
```
ATTRS{idVendor}=="**046d**", ATTRS{idProduct}=="**c50a**", NAME="USB-modem"
```
and save.

Change device in Gnome PPP connection properties to /dev/USB-modem, and enjoy... (You should reconnect modem after adding udev rule to apply this rule to your device)
(Note: I do not use Gnome and I have never seen Gnome PPP, I am only guessing its configuration options)

---

