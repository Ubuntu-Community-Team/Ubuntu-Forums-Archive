---
title: "HP Envy m6 bluetooth not working Ubuntu 13.10"
date: 2014-02-26
forum: Networking &amp; Wireless
---

### Post by lonelywolf96 on 2014-02-26
I have a HP ENVY m6 laptop, which came pre-installed with Windows 8. I did a clean install of Ubuntu 13.10 today in an attempt to use a software to emulate the PS3 controller (In order to play with mouse and KB on the PS3 of course ;)) since I was kinda tired of Windows 8.1 anyways...

But that software (GIMX) uses bluetooth, which my laptop has built-in.

Ubuntu is starting up with the flight mode (disconnecting wireless activity, like Wifi and bluetooth), except the wifi is working, even though the button is lit red (off).
It is one of those rigs that you have to press FN+F12 to toggle the flight mode, but for some reason it doesn't work...

I've searched for hours on the ubuntu forums after a solution to no avail... So here I am.
The bluetooth is a Railink RT3290. 

I've tried the stuff that was recommended, from ```
sudo unblock all
``` to writing a bunch of code..

Sorry, but I am a Linux noob after years of not using it properly :-({|=

I'd love to get the bluetooth working! I can only find a single trace of the bluetooth even existing using ```
lshw
```... 
On the GIMX software, it says "Bluetooth dongle was not found", and in the system settings, it doesn't even show..

Any help to solving this problem would be much apprechiated :rolleyes:

---

### Post by varunendra on 2014-03-01
Welcome to the forums lonelywolf96!

Please post back the outputs of -
```
lsusb
usb-devices
hcitool dev
```

Have you checked the BIOS to make sure the bluetooth is enabled there (if there is any option there to enable/disable the bluetooth)?

---

