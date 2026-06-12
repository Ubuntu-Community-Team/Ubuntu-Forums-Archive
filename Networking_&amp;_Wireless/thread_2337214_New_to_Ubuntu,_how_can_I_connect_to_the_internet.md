---
title: "New to Ubuntu, how can I connect to the internet?"
date: 2016-09-15
forum: Networking &amp; Wireless
---

### Post by nanamica on 2016-09-15
Hi guys, I'm new to Ubuntu. I've just installed it on an old laptop with a broken network adapter so I want to use a USB wifi adapter instead, but can't download the driver for it because it is only for Windows. Is there anyway I can get this to install onto Ubuntu? The adapter is a Linksys AE1200. Thanks!

---

### Post by ian-weisser on 2016-09-15
Did you check the hardware database? [http://www.ubuntu.com/certification/](http://www.ubuntu.com/certification/)

What does dmesg show when you plug in the dongle?

There is an [old thread on AskUbuntu]("http://askubuntu.com/questions/100090/how-do-i-install-the-driver-for-my-linksys-ae1200-wireless-n-usb-adapter") (2012) that basically says this dongle is garbage without ndiswrapper. Maybe things have changed.If not, then newer, better, linux-compatible dongles are cheap.

---

### Post by mörgæs on 2016-09-16
If you want hardware that is guaranteed to work then [https://www.thinkpenguin.com/](https://www.thinkpenguin.com/) is a fine place. 
I have good experience with Trendnet wifi gear, especially used stuff some years old.

---

### Post by wildmanne39 on 2016-09-16
Are you positive the internal card is faulty? that usb adapter is almost impossible to get to work and you have to use windows drivers with ndiswrapper and the connectivity would never be great.

Please click on the wireless script in my signature and follow the directions for running the script and posting the results here. 
Thanks

---

