---
title: "Edimax EW-7811UN not working on 12.04lts"
date: 2013-11-06
forum: Networking &amp; Wireless
---

### Post by Nakira89 on 2013-11-06
I have decided to use this usb wifi because my built in wifi wasnt the best, however this usb wifi was always dropping connection and every 2 - 5 minutes id have to un plug it and put it back in to get it to reconnect. 

So i did some research and came across this post with the drivers listed at the bottom ([http://ubuntuforums.org/showthread.php?t=2092934&p=12621449#post12621449](http://ubuntuforums.org/showthread.php?t=2092934&p=12621449#post12621449))

However now the usb wifi now doesnt work at all and ive blacklisted the native drivers, the only way i can post this now is to quickly load an older kernel version to use my built in wifi. Which obviously isnt ideal or very practical. I do hope some of you geniuses can help me out here. 

Regards, Josh.

---

### Post by SeijiSensei on 2013-11-06
I'm a bit surprised you're having problems with this device.  I just bought one for a Raspberry Pi I'm playing with and, using the "[Raspbian]("http://www.raspbian.org/")" distribution based on Debian Wheezy, the adapter is rock solid.  Since Ubuntu is also a Debian derivative, I would have thought they shared the same drivers.  (The architectures are different, of course, since the Pi runs on an ARM chip, not x86.)

Have you tried using different USB ports on the computer?  If you have a USB 3.0 port, give that a try.

---

### Post by Nakira89 on 2013-11-07
> **SeijiSensei said:**
> I'm a bit surprised you're having problems with this device.  I just bought one for a Raspberry Pi I'm playing with and, using the "[Raspbian]("http://www.raspbian.org/")" distribution based on Debian Wheezy, the adapter is rock solid.  Since Ubuntu is also a Debian derivative, I would have thought they shared the same drivers.  (The architectures are different, of course, since the Pi runs on an ARM chip, not x86.)

Have you tried using different USB ports on the computer?  If you have a USB 3.0 port, give that a try.

Yeah iv have tried all of the different USB ports including my usb 3 ports. :/ im pretty stumped so anyone with any advice thatd be amazin!

---

### Post by Herber on 2013-11-07
Hello:  I had a similar problem with this USB device in and it was solved by the steps in this thead:  

[lubuntu] Two wireless card, how do I disable one of them?

I don't know how to insert a link to the thread, but if you start reading and following the directions from post #23 - #25 on page three of the thread I think your problem will be solved.

---

