---
title: "USB device not starting/mounting after restart? Please help!"
date: 2009-03-03
forum: New to Ubuntu
---

### Post by Gp. on 2009-03-03
Hi,
I have the logitech dinovo edge keyboard...

It uses bluetooth (so it's wireless)

To get it to work, I plug the receiver into a usb port and get both the devices to communicate (Receiver and Keyboard). It works fine.

However after restarting, it doesn't. In order to get them communicating I have to unplug the receiver and plug it back in again. 

Ubuntu is not automatically starting the bluetooth receiver, or not mounting it or something. I'm new to all this so I'm not sure, so I hope someone will know what to do!

Thanks.

---

### Post by rogueleader12345 on 2009-06-15
With all my stuff, when you reboot, you have to take it out and plug it back in to get it to remount. I suppose you could write a script to mount it. Or have your terminal do it. For the startup command it would be something like ```
mount /dev/sde1
```, with your drive substituted for sde1.

---

