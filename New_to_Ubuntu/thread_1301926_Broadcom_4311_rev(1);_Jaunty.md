---
title: "Broadcom 4311 rev(1); Jaunty"
date: 2009-10-26
forum: New to Ubuntu
---

### Post by UnhappyBroadcomUser on 2009-10-26
Freshly installed Ubuntu Jaunty, wireless internet is not working. I have tried various strategies from google to no avail, so I reinstalled Ubuntu to clear those mistakes. "Broadcom STA" is listed as a proprietary driver, except activating that last time did not help so I have left it alone for the moment. Sorry if I haven't given much information, I don't know what else to include. Thanks.

---

### Post by arochester on 2009-10-26
Have you looked at "Howto install and Enable Broadcom Wireless in Ubuntu 9.04 (Jaunty)" on [http://onlyubuntu.blogspot.com/2009/07/howto-install-and-enable-broadcom.html](http://onlyubuntu.blogspot.com/2009/07/howto-install-and-enable-broadcom.html)

---

### Post by UnhappyBroadcomUser on 2009-10-26
I followed the instructions in the link, and I still cannot get an internet connection. Blue bars appear as if it were connected and it says it is connected, but I cannot view the internet. I don't see why it could be my connection not Ubuntu because it worked with the laptop before I installed Ubuntu, and it works with e.g. my Nintendo DS.

---

### Post by undecim on 2009-10-26
When you right click on the network manager icon when it has the blue bars and choose "Connection Information", what information do you see?

---

### Post by UnhappyBroadcomUser on 2009-10-26
In the short time since you replied, the blue bars have gone away, I can't get them to come back. Just a cycling green/blue circles that keeps asking for the WEP key (which I know and entered).

EDIT: Got them back, connection information says:

Interface: 802.11 WiFi (eth1)
Hardware Address: 00:1A:73:2E:24:57
Driver: wl
Speed: 48 Mb/s
Security: WEP

It also lists my IP Address, Broadcast Address, Subnet Mask and Primary DNS which I can provide if necessary. The last digit of the Ethernet connection IP address differs to the last digit of the Wireless connection IP address.

---

### Post by undecim on 2009-10-26
Okay, so that means you have connected to your local network, sent and recieved packets (data). It seems that something is causing you to disconnect.

---

### Post by UnhappyBroadcomUser on 2009-10-26
Is it worth taking my laptop to another wireless access point to determine whether the problem lies with my router or the laptop's hardware?

---

### Post by undecim on 2009-10-26
Can't hurt. Though I think I've used a BCM4311 before and installed it with fwcutter. Is there a driver in your Hardware Drivers program called "Broadcom B43"? If so you might want to try switching to that driver (disable STA, enable B43) first.

EDIT: you can also install the b43-fwcutter package after removing the STA driver.

---

### Post by UnhappyBroadcomUser on 2009-10-27
I tried changing the IP address from what appeared as default when it picked up the wireless signal to match the digit on another laptop and entered some more numbers in. Don't know why it didn't work before, but I have had no issues since. Thank you for your help, totally resolved. :D

---

