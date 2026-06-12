---
title: "logitech usb trackball mouse"
date: 2009-03-14
forum: New to Ubuntu
---

### Post by techno-mole on 2009-03-14
hello.

i have a logitech trackball mouse (trackman marble) im currently playing with the alpha 6 of jaunty (kubuntu) and i have found a small problem.

on intrepid i used this ( [https://help.ubuntu.com/community/Logitech_Marblemouse_USB](https://help.ubuntu.com/community/Logitech_Marblemouse_USB)) method to turn one of the buttons into a scroll wheel (well at least it makes the mouse scroll when you hold it down)
but in kubuntu jaunty it doesnt work.

any body got any ideas ?

maybe i need to put the file into a different place ?

cheers

---

### Post by kmoffat on 2009-04-22
[Not trackball, but marblemouse, you might try variants]
In Ubuntu 9.04 I added the following file, /etc/hal/fdi/policy/mouse-wheel.fdi, and my Logitech Marble Mouse, plugged in to USB, has scroll wheel functionality, apparently both verticle and horizontal, at least in Firefox, while holding the small left button and moving the ball:

<?xml version="1.0" encoding="ISO-8859-1"?>
<deviceinfo version="0.2">
  <device>
    <match key="info.product" string="Logitech USB Trackball">
      <merge key="input.x11_options.Buttons" type="string">5</merge>
      <merge key="input.x11_options.ButtonMapping" type="string">1 8 3 4 5 6 7 2 9</merge>
      <merge key="input.x11_options.EmulateWheel" type="string">true</merge>
      <merge key="input.x11_options.EmulateWheelButton" type="string">8</merge>
      <merge key="input.x11_options.EmulateWheelTimeout" type="string">300</merge>
      <merge key="input.x11_options.XAxisMapping" type="string">6 7</merge>
      <merge key="input.x11_options.YAxisMapping" type="string">4 5</merge>
      <merge key="input.x11_options.ZAxisMapping" type="string">4 5</merge>
      <merge key="input.x11_options.Emulate3Buttons" type="string">true</merge>
    </match>
  </device>
</deviceinfo>

---

