---
title: "Btscanner bluetooth lockup on Toshiba Satellite ...and possible workaround"
date: 2008-06-08
forum: Networking &amp; Wireless
---

### Post by Langleyo on 2008-06-08
Hi, if you're like me and having problems with Btscanner locking up, maybe this may help. Let me explain.

I have been experimenting with Btscanner for a while under Hardy Heron on my Toshiba Satellite A100 -332 with a few different Bluetooth dongles,(including 2.0) only to find after five minutes of scanning the computer would hang up totally, with a blinking Caps lock (apparently a kernel panic indicator).

 I tried running it in a separate terminal window (ctrl-alt F1-6) but same thing happened - only at least this time it came back with various reports, usually involving interrupts and kernel panics, but always total lock up.

Frustrated, I was all but ready to give up on the program altogether, when I noticed if I ran 2 instances of the software (each in 2 separate terminal windows), the thing stayed stable! (I used the "btscanner --no-reset" option which keeps the light on constantly on the dongle, but doesn't seem to cause any problems).

 I began wondering if the problem is some sort of timing or waiting issue. Maybe the computer is out of step - too "fast/slow" or "out of synch" with the bluetooth somehow, and giving it two lots of data to process slowed something down sufficiently to make it work? It sounds weird!

Hope this helps someone, I'd love to hear from you if it does, or if you can shed some light on the problem, even better!! Am I the only one?

UPDATE:
I managed to capture this error message in a terminal window. Hope it helps debug, as I fear there is a problem with Ubuntu and Bluetooth after reading other users are having similar issues with kernel panics and lock ups (caps lock flashing while doing some bluetooth operation) while using different applications and dongles. Is it only Ubuntu? and if so, what's different about the way it works compared to other distro's?

[http://ubuntuforums.org/album.php?albumid=257&pictureid=818](http://ubuntuforums.org/album.php?albumid=257&pictureid=818)

Regards

---

