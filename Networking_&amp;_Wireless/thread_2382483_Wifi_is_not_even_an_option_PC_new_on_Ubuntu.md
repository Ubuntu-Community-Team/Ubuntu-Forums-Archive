---
title: "Wifi is not even an option PC new on Ubuntu"
date: 2018-01-14
forum: Networking &amp; Wireless
---

### Post by gfeti on 2018-01-14
I can not choose wifi it is either ethernet or nothing. I run a n300 netgear usb wifi stick and it doesn't even pick it up. Keep in mind I am using a 32bit software. I have tried for 6 hours today and after many forms and youtube videos I need help. My pc will recognize Usb drives, but not the wifi usb.  The light on the netgear usb drive though does light up. PLEASE HELP. Installing drivers is not working. Nothing is. What do i do

---

### Post by kc1di on 2018-01-14
From what I've seen the n300 dongle only works with windows drivers and you'll have to use ndiswrapper to get it going. 
[See here]("https://askubuntu.com/questions/839947/netgear-n-300-wna3100-usb-adapter-for-ubuntu-16-04") how to do that:
It may be easier to order another dongle that's known to work with linux out of the box.
good luck.

---

### Post by gfeti on 2018-01-15
Thanks, what 'dongle' would you recommended?

---

### Post by SeijiSensei on 2018-01-15
Linux support for 802.11ac adapters has been slow.  I'm using this device

[https://www.newegg.com/Product/Product.aspx?Item=9SIAF176R40516](https://www.newegg.com/Product/Product.aspx?Item=9SIAF176R40516)

with the Realtek 8812au chipset.  That device is supported in recent Linux releases via the Driver Manager.  When you run the Manager, it will offer the option to use the rtl8812au-dkms package. You'll need to have another Internet connection to download the driver, so connect the machine with an Ethernet cable, then plug in the device and run the Driver Manager.

---

### Post by kc1di on 2018-01-17
I have not personally test any but [this page]("http://willhaley.com/blog/linux-usb-wifi/") gives several that are supposed to work well. 
good luck.

---

