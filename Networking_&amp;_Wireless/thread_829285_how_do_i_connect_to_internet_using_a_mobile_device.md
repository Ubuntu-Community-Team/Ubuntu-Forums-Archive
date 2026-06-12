---
title: "how do i connect to internet using a mobile device"
date: 2008-06-14
forum: Networking &amp; Wireless
---

### Post by noRoot on 2008-06-14
Hello everybody. Someone please tell me how to connect to internet using a mobile device. I am a new user of Ubuntu and do not know the procedures how to use my mobile as a modem to set up a connection. Thanks

---

### Post by lswb on 2008-06-14
Are you talking about using connecting a cell phone via USB or bluetooth as a modem? If so, they usually are recogized as a serial port and a ppp connection can be established if you know the right settings. Plug you phone in and open a terminal, type the command "dmesg" and see if there is any output near the end about a new USB device being found, in particular loof for something like ttyACM0 or ttyUSB0.

The other information you need will vary with you service provider. If you google something like "cell modem verizon linux ppp" you will probably find the info you need, (replace "verizon"with the name of your provider!)

---

### Post by Jaxl on 2008-06-24
[http://ubuntuforums.org/showthread.php?t=838891](http://ubuntuforums.org/showthread.php?t=838891)
running on ubuntu gnome 8.04 from a verizon wireless usb 720 card :D use gnome ppp all u need

---

