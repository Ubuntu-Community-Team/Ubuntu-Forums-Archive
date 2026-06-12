---
title: "webcam video driver"
date: 2010-01-17
forum: New to Ubuntu
---

### Post by manny43 on 2010-01-17
Hello friends
 
How do you download and install video driver for Logitech Webcam C200?

---

### Post by J V on 2010-01-17
You shoulden't need to, ubuntu recognizes pretty much all webcams straight away, no extra clumsy drivers needed :P

---

### Post by manny43 on 2010-01-17
I just installed Logitech Webcam C200 and it wont work when running Cheese.

---

### Post by hobo14 on 2010-01-17
> **manny43 said:**
> I just installed Logitech Webcam C200 and it wont work when running Cheese.

Weird.  I plugged my C200 in and it just worked.

---

### Post by pietro_spina on 2010-01-17
Presumably you are running a stock kernel?
```
uname -a
```

That web cam should just work it's on the supported list like my C500. However, my cam does have some odd behavior sometimes and is not found by cheese sometimes.

if you use the command
```
lsusb
```
you can see if it is recognized at all.

for some reason my camera doesn't like to be plugged in and out... It stays recognized. the other odd thing is sometimes it like to be plugged in the back of by computer and other time it like the front...

I recommend trying different combos of plugged in at boot in front/back and plugged in after boot in both places...

run ```
lsusb
```
unplug it
run ```
lsusb
```
see that is is gone or not
reboot
run ```
lsusb
```
see that it is not there
plugin
run ```
lsusb
```
see that it is there
run cheese
...
etc
I'm sure you can take it from there...

---

### Post by lyall on 2010-01-20
see the following link
[http://ubuntuguide.org/wiki/Ubuntu:Karmic]("http://ubuntuguide.org/wiki/Ubuntu:Karmic")
then scroll down to **4.16 WebCams**

also look at [https://help.ubuntu.com/community/Webcam]("https://help.ubuntu.com/community/Webcam")

good luck and have fun learning

---

### Post by yeeshkull on 2010-01-21
luvcview -f yuv


All I get is a black screen.

This is the output of lsusb:

Bus 001 Device 004: ID 046d:0802 Logitech, Inc. 
Bus 001 Device 003: ID 1058:0910 Western Digital Technologies, Inc. 
Bus 001 Device 002: ID 050d:705a Belkin Components F5D7050A Wireless Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

---

