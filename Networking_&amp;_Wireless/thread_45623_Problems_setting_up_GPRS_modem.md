---
title: "Problems setting up GPRS modem"
date: 2005-06-30
forum: Networking &amp; Wireless
---

### Post by arkiv on 2005-06-30
Hi all,

I have a problem setting up my GPRS wireless modem to work in Ubuntu.

Ubuntu has detected my device as a serial-to-USB controller installed to ttyUSB0. And this is according to the manufacturer's guide.

I am able to communcate with the device using minicom. However, I would like to set up a dial-up profile using this device. 

In the networking config window, my device ttyUSB0 is not on the lists of devices which list: /dev/modem, /dev/ttyS1, /dev/ttyS2, etc. i have to manually key-in /dev/ttyUSB0 as a dial-up device.

I can activate it, but if I close the window and open it again, my ppp connection is not active. 

Is there a way i can make /dev/modem point to /dev/ttyUSB0?

Can anyone suggest a solution to this problem?  

Best regards,
Nicholas

---

