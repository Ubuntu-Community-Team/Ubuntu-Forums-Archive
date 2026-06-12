---
title: "New mobile phone for modem"
date: 2008-06-11
forum: Networking &amp; Wireless
---

### Post by somersetsimon on 2008-06-11
When my old laptop was running Windows XP, I used to use Motorola Phone Tools in order to use my Motorola RAZR3 phone as a modem to connect to the internet when out and about. I've now installed Hardy on the laptop and I'd like to attempt the same thing. I've seen a few threads on how to connect particular phones, but is there a reliable phone connection package or guide out there?

Also, I'm coming to the end of my phone contract, so I'll be upgrading my phone. Are there any particular makes, models or networks (I'm in the UK) that work better than others?

Thanks

Simon

---

### Post by lswb on 2008-06-11
Usually when a cell phone is plugged into a USB port in linux, the proper modules will automatically load and a serial port will be created. Most of the time it is /dev/ttyACM0. Then you just need to set up a ppp connection using that port, more or less easily done with pppconfig or a similar program, or even just manually writing a ppp peer file for the connection.

You will need to know what user name the ISP assigns you (often the telphone number), any password and authentication type if used, etc. Sometimes you can find this info in the windows program you use with the same phone. If you were in the USA and used Verizon I could have you connected in a few minutes! There are probably some differences in the configuration where you are, but it shouldn't be tough at all to get it sorted out.

---

