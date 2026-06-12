---
title: "Speedtouch USB modem not working"
date: 2008-09-03
forum: Networking &amp; Wireless
---

### Post by Balin85 on 2008-09-03
I have followed every guide I can find and I still cant get it to work I cant even work out how to get the firmware version test to work.

I am the first to admit I am completely new to this and I am probably missing something obvious can anyone help me?

---

### Post by Balin85 on 2008-09-03
[https://help.ubuntu.com/community/UsbAdslModem/SpeedTouch]("https://help.ubuntu.com/community/UsbAdslModem/SpeedTouch")

This is the one of the guides I have used and I cant get this to work even

> About the firmware

The firmware is a small piece of code that gets loaded into the modem itself as a kind of OS for the modem. There are three revisions for the SpeedTouch and each revision runs its own firmware. To determine what revision you need, use the following command:

grep -B 1 "THOMSON" /proc/bus/usb/devices

---

### Post by coffeecat on 2008-09-03
The Ubuntu guide you link to seems to be nearly two years old - it refers to Ubuntu 6.10. When I plug my old Speedtouch 330 (hack, spit! :wink:) into this laptop running 8.04, I get 'No such file or directory' when I ...

```
grep -B 1 "THOMSON" /proc/bus/usb/devices
```

Indeed when I look in /proc/bus/usb, the folder is empty which explains why. I guess 8.04 handles usb devices differently. That guide may simply not be suitable for 8.04 - I don't know.

My advice is to ditch that piece of #%$&£# and get yourself a proper adsl modem-router. That is the collective advice on [this thread from another forum]("http://www.linuxformat.co.uk/index.php?name=PNphpBB2&file=viewtopic&t=8497"). The OP there seems to be confused as to exactly what hardware he does have, but it comes out right in the end and some of the thread is entertaining to read, although it wouldn't be allowed here. :)

I see that one poster there links to [this]("https://launchpad.net/usb-adsl-modem-manager"), but whether that's of any help I really don't know. I only keep my Speedtouch as a reminder of how cheap and nasty some hardware (particularly free hardware supplied by an ISP) can be.

Honestly, get a modem-router.

---

### Post by Balin85 on 2008-09-03
Thank I guess I will just have to wait then.

---

