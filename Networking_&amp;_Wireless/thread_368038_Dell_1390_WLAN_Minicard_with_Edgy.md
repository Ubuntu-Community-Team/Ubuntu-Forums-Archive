---
title: "Dell 1390 WLAN Minicard with Edgy"
date: 2007-02-22
forum: Networking &amp; Wireless
---

### Post by Skyler on 2007-02-22
Hi,
I'm trying to get Ubuntu Edgy to cooperate with my Dell 1390 minicard on my laptop. I have tried the method described here:
[http://geeklimit.com/2007/02/06/easy-wireless-networking-in-ubuntu-edgy/](http://geeklimit.com/2007/02/06/easy-wireless-networking-in-ubuntu-edgy/)
It still didn't work. Ubuntu's default networking utility can't detect any wireless networks, and neither can the wpasupplicant utility. Does anyone have suggestions?

---

### Post by dekalbave on 2007-02-22
A Dell 1390 uses a Broadcom 4311 chip.  The only way I could get mine to work was to follow these instructions, though it worked with the 2.6.17.10 kernel.  Using the 11 kernel broke it for me, so I went to Feisty, where they work also.  It's pretty complicated, though you can copy and paste most of the commands from the web page into the terminal.  Here's the link:

[https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29?highlight=%28WifiDocs%2FDevice%29](https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29?highlight=%28WifiDocs%2FDevice%29)

Good luck.

---

### Post by Skyler on 2007-02-23
Thank you. I'll try it and let you know what happens.

---

### Post by Skyler on 2007-02-23
Now it's *really* screwed up. If a program tries to access the network, it gets shut down. That includes Firefox, even when I'm not trying to access the Internet. 
It started happening after I restarted the computer prior to step 7.

EDIT: It works now. I don't know what I did.

---

