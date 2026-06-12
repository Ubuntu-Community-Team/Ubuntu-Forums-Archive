---
title: "trackpoint T43 Xubuntu 8.10"
date: 2009-01-28
forum: New to Ubuntu
---

### Post by coffey7 on 2009-01-28
I have a IBM thinkpad T43 running Xubuntu 8.10 and I can't seem to figure out how to find the posts that tell how to configure the track point scrolling feature. Does any one have a link to a fix for this? I tried a few fixes when I was running Ubuntu 8.10 but never could get it to work. The instructions were not clear for Noobs.

I found this but don't understand how to change HAL

Create the file /etc/hal/fdi/policy/mouse-wheel.fdi as root with the following content:

<match key="info.product" string="TPPS/2 IBM TrackPoint">
 <merge key="input.x11_options.EmulateWheel" type="string">true</merge>
 <merge key="input.x11_options.EmulateWheelButton" type="string">2</merge>
 <merge key="input.x11_options.YAxisMapping" type="string">4 5</merge>
 <merge key="input.x11_options.XAxisMapping" type="string">6 7</merge>
 <merge key="input.x11_options.Emulate3Buttons" type="string">true</merge>
 <merge key="input.x11_options.EmulateWheelTimeout" type="string">200</merge>
</match>

---

