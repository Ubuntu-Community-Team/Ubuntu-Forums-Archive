---
title: "How to fix wireless usb?"
date: 2009-10-07
forum: New to Ubuntu
---

### Post by pointyblue on 2009-10-07
Hi,

I can't figure out how to make my Philips SNU5600 wireless usb stick work with Ubuntu 9.04.

When I insert it, restart and click on the network icon on the panel it indicates that both wired network and wireless network are enabled - but I can't find my (or any) wireless network to connect to. When I remove it the panel icon indicates there's only a wired internet.

(My laptops have no problem finding and connecting to the wireless network.)

I've googled the problem and it appears Philips SNU5600 is supported by recent kernels but it just doesn't work.

I'd really appreciate some help here!

:)

---

### Post by mikeyphi on 2009-10-07
When you right-click on the icon - do you get a 'edit wireless networks' option? that should allow you to enter domains, etc. for your router.

Although, unless your router is 'hidden' you should be seeing the connection.
Try to check under 'connection information' to see if the connection shows any activity.

Finally - open a terminal and enter
ifconfig

see what is listed about the wifi

also enter
iwconfig

and see what is listed

---

