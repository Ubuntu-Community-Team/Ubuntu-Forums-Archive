---
title: "usb racing wheels"
date: 2009-02-23
forum: New to Ubuntu
---

### Post by philipballew on 2009-02-23
im intrested in buying a usb racing wheel to use in 8.10 and need some sugestions. im looking at a Microsoft Sidewinder or a Logitech WingMan Formula or a Logitech MOMO Force Feedback Racing Wheel. either would be fine. i just need to know if any have drivers and if so how well do they work?

---

### Post by unutbu on 2009-02-24
Googling "Microsoft Sidewinder Ubuntu" came up with this:
[http://www.ubuntugeek.com/how-to-set-up-a-gameportgamepad-or-joystick-in-ubuntu.html](http://www.ubuntugeek.com/how-to-set-up-a-gameportgamepad-or-joystick-in-ubuntu.html)
Similar google searches for each of the other devices should allow you to decide which one is best supported.

---

### Post by holmes0 on 2009-07-23
Hi,

There are two sidewinder wheels:
- the old one (game port)
- the "recent" one (USB).

To my knowledge support of these devices (or the joystick versions) has not been a problem for several years. The real headache came from the Force Feedback support.
For the game port version, I don't know if it works. For the USB version, it should work since recent improvements.

Since 9.04 (and kernel 2.6.28, it is no longer necessary to compile a custom kernel. Force Feedback support is from now on a standard feature. I have personnaly tested it with a Sidewinder Force Feedback 2 (joystick) using ff-utils and gforce (a ff testing application with a GUI). It works perfectly. It appears Sidewinder support is no longer experimental since I don't have any more freeze as it used to happen with previous kernels.

Now we have to wait for the next SDL 2 (with a FF API) which is now the single element lacking for a FF support within Freespace SCP!

Hope it will come soon ...

---

