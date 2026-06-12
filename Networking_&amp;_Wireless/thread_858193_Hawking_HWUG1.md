---
title: "Hawking HWUG1"
date: 2008-07-13
forum: Networking &amp; Wireless
---

### Post by Gene_s on 2008-07-13
I have just installed Ubunto Linux 8.04 and love it! Goodbuy MS.

I have a wired Linksys home network I am using right now but wish to convert to wireless. I have two USB Hawking's HWUG1's and an old wireless Linksys DSL router....will the USB wireless devices work OK without a lot of hula-hoops??

thanks, Gene

---

### Post by chili555 on 2008-07-13
I think this is supposed to work with a module called *rt73usb.* The nice thing about Linux, is you can open a terminal and do:```
sudo tail -f /var/log/messages
```Leave the terminal open as you insert your Hawking and see if the kernel puts out a message like, "Hey, I have detected a new device and loaded a module rt73usb. I'm going to call my new baby wlan0." If so, do Ctrl-C to exit *tail* and then type:```
iwconfig
```Do you have a new interface ready to configure and connect?

---

### Post by Gene_s on 2008-07-13
Thank you....will give it a try!:)

---

### Post by Gene_s on 2008-07-24
I tried that but get no wireless extensions

any other suggestions??

---

### Post by ophie99 on 2009-06-18
just got one and works right out of the box on ibex and jaunty
this is one of the best adapters I've had for linux:p

---

