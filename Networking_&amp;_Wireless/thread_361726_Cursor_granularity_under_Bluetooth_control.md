---
title: "Cursor granularity under Bluetooth control"
date: 2007-02-14
forum: Networking &amp; Wireless
---

### Post by frisket on 2007-02-14
I've managed to get my SE Z520i cellphone to control the cursor on my Edgy laptop (Inspiron 4150), so running presentations from halfway down the classroom works fine...

...except that each click on the phone rockerpad is a 60-pixel jump on the laptop screen, which is way too much at 1440x1050 pixels.

1. Does anyone know where the config for the resolution of the cursor remote-control is kept, and how to crank it way down to about 10 pixels? 

Weirdly, the only way I got it to work at all was for the *laptop* to make the request to be remote-controlled:

sudo /etc/init.d/bluetooth restart
MYPHONE=Frisket
sudo hidd --connect `hcitool scan | grep $MYPHONE | awk '{print $1}'`

This is 180 degrees from normal, where you should use the *phone* to request the laptop to allow itself to be remote-controlled. If I try to do an INQ for services from the phone to the laptop, the response is that the laptop offers no services, which is an obvious lie.

2. Does anyone know why remote control has to be done ***-backwards?

---

### Post by qbs on 2007-04-03
Thx, I tried this for a long time with my SE k700i and never thought of doing it the other way round. Sadly I have exactly the same problems as you experience (high pixel jump, no offered services). Letting the Computer to make the request renders the remote-control nearly useless to me, as walking to the PC is what I want to avoid when I'm lazy ;)
Now as you got this working, I will see if I'm finding out more when I find the right time to do it.
Anyway this is better than nothing.

---

