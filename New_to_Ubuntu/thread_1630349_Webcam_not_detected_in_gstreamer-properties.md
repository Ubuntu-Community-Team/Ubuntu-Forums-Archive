---
title: "Webcam not detected in gstreamer-properties"
date: 2010-11-25
forum: New to Ubuntu
---

### Post by SammiSabbat on 2010-11-25
The only way I can access it is if I hook up a usb webcam, then I have the option of using both internal and usb.

 For things like Video chatting and stuff like that I like the internal, and for things like youtube I like the usb. 

How can I get gstreamer to detect my internal webcam without having the usb hooked up?

---

### Post by no2498 on 2010-11-25
you say its internal
you on a lap top ?
if yes do you not need to push a key like fn to turn it on ?
with out the usb 1 plugged in

btw i still have the books that come with my first computer/also it still runs

---

### Post by SammiSabbat on 2010-12-03
My laptop is automatic there isnt a button to turn it on.

---

### Post by no2498 on 2010-12-04
with the usb cam unplugged
open a terminal type  dmesg   click enter
see if any cam gets listed

also type  lsusb  click enter

if the cam is seen look for the cam # and name in/with google
see if it uses a diff driver than the usb cam

---

