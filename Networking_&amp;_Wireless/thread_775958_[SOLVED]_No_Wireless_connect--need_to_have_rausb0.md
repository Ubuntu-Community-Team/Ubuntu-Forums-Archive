---
title: "[SOLVED] No Wireless connect--need to have rausb0?"
date: 2008-04-30
forum: Networking &amp; Wireless
---

### Post by jerrallan on 2008-04-30
Problem solved...............I had Ubuntu 6.06 LTS on my computer before it crashed.  I was able to connect to the internet using a workaround on rausb0. I had to enter iwconfig etc,essid,passcode in the terminal and it would connect. I used a Linksys WUSB54Gv4 wireless device

I have reinstalled it using the Canonical CD 6.06.1 LTS. I have tried to get wireless through eth0, but it does not like the essid and passcode. I now have a Belkin 7050 usb wireless device. when I installed the driver, ndiswrapper did recognize the driver and the hardware. I cannot get a connection. I have followed the two sticky's on Network but no luck.

Is there a way I can get rausb on this? rausb is not given as a choice.When I installed 6.06.1 this time I did an ndiswrapper -l and it did not list the rt2570.  In fact it listed no wireless drivers.

Help would be appreciated.
Thanks

---

