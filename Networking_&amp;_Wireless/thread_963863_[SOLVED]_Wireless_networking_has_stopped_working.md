---
title: "[SOLVED] Wireless networking has stopped working"
date: 2008-10-30
forum: Networking &amp; Wireless
---

### Post by Mark224 on 2008-10-30
Hi,

I have a Linksys WUSB54GB v2.1 USB wireless adaptor.  I installed the ndiswrapper and the windows drivers and it worked fine :-)

However now it no longer works :-(.  I haven't changed any of the network parameters.

When I login, in place of the network icon, I get two blue dots and rotating arrows.  There is a tooltip which says "Waiting for network key..." which goes on forever.

I have tried modprobe and iwconfig and it shows the wireless
interface wlan0.

It stopped working after I download 100's of recommended updates.  I know a lot of people have had problems with this
and I could not log in with the new kernel so have gone back
to 2.6.24-19.  I'm not sure if this is the cause.

Please help.

---

### Post by Mark224 on 2008-11-10
This seems to be an issue with Network Manager.  Now I have finally figured out how to configure the network manually it works ok as long as I don't plug in any other USB devices.

---

