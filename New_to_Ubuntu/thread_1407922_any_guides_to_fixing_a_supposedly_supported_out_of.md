---
title: "any guides to fixing a supposedly supported out of box webcam? (sony Z series)"
date: 2010-02-15
forum: New to Ubuntu
---

### Post by niffcreature on 2010-02-15
i have a sony z series with a webcam.
lsusb
Bus 003 Device 002: ID 147e:1000 Upek 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 002: ID 044e:3017 Alps Electric Co., Ltd 
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 1410:2120 Novatel Wireless 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

i dont really understand what this means, because upek shows up as upek but i know that one of the "linux foundation 2.0 root hub" is my webcam. how do you further identify these usb devices?
the information im getting that it is tested and supported is here:
[http://www.basyskom.org/~eva/log_installation_vaio_z21vnx.html](http://www.basyskom.org/~eva/log_installation_vaio_z21vnx.html)
lsusb
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
# Camera
Bus 004 Device 003: ID 05ca:18b0 Ricoh Co., Ltd
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
# Bluetooth?
Bus 007 Device 002: ID 044e:3017 Alps Electric Co., Ltd
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
# TouchStrip device
Bus 001 Device 003: ID 147e:1000
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
# 3G modem
Bus 002 Device 006: ID 0af0:6911 Option
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

some things have changed i guess, based on model or OS. he is running opensuse.
im running ubuntu studio jaunty 64 bit, but i have tried intrepid and kubuntu jaunty 32 bit as well with no success.

i also tried to create /dev/video0 which did not work. its because v4l-conf showed this
v4l-conf: using X11 display :0.0
dga: version 2.0
WARNING: No DGA direct video mode for this display.
mode: 1600x900, depth=24, bpp=32, bpl=6400, base=unknown
can't open /dev/video0: No such file or directory

i think it should be supported by the integrated UVC driver, can someone tell me how any of this works as far as configuration? i just dont understand it at all. thanks

---

### Post by no2498 on 2010-02-15
try this
open a terminal type ( gstreamer-properties ) click enter
click video try v4l1 or v4l4
click the bottom test button for each 1

now you need a program to use it with

get ( cheese and wxcam 1 of the 2 will see the cam
if your cam uses v4l1 do not open cheese or you need to do  this over   cheese does have a very nice help file in it
is more programs that can see the webcam

---

### Post by niffcreature on 2010-02-15
uh no /dev/video0

that means,
no /dev/video0!

if i hadnt already tried what you suggested, i would have no way of knowing it didnt work in the first place. lol. guess i should have mentioned that i had tried the simplest things already

unless you can tell me where to get v4l4? maybe thats my problem

---

