---
title: "[SOLVED] Question: D-Link dwl-g132 USB"
date: 2008-06-20
forum: Networking &amp; Wireless
---

### Post by pure life on 2008-06-20
I have been searching around the forums and noticed that others have had problems getting this particular wireless adapter to work in Ubuntu. I have checked the ubuntu wireless wiki article and see that it is not specifically supported, but have to believe that there is a way to get it to connect in Ubuntu. I have seen lots of suggestions, but want to be sure that it will work before I do the full install.

Thanks!

---

### Post by pokipoki08 on 2008-06-20
It won't. I have tried hard to get it to work with WPA2, it just can't, even in Gutsy (7.10).

Get the Linksys WUSB54GC. Do a search first.

---

### Post by pure life on 2008-06-21
I would like to think that there is a possibility to be able to use this type of USB adapter with Linux. I have tried it out on an older family computer and it seemed to function OK. The only problem was that it was not regisering as a wireless network. I could connect fine to the internet.

What i did was connect the test machine with kubuntu wired to the router and installed ndiswrapper and then added the .inf driver that I had downloaded from the D-Link support site and saved to a usb thumb drive to use in the installation process. Then when it was installed, i unplugged the cable and after entering the wireless settings (including network id and security settings) and I was online.
Just hoping this will work on my personal machine...

Thoughts?  Suggestions?

---

### Post by kennedyjch on 2008-06-21
I've gotten mine working. Here's how:

1) I installed ndiswrapper and graphical interface through "add/remove" and search for "Windows wireless drivers"
2) I then used the .inf file that came with the card (XP version)
3) I was able to get the card operating in ROAMING mode only. Manual config through the graphical netowrk configuration has not worked.  I was able to use command line with iwconfig to also get the card to function properly.

In roaming mode I've not been able to get the wireless interface opreational until I login. If you manually configure, seems to work OK. 

Further, I use WEP-64 key encryption. If I specify ascii key in non-roaming mode, adapter does not work. In roaming mode, the ascii key is accepted and functions. However, to get the adapter to function properly in manual mode I've had to specify the equivalent hex key. I'm guessing that ascii keys either don't work or they need to be in uppercase only. 

Also, when manually configures, there is no desktop status of connection or signal strength - a desirable feature but by far not a show-stopper.

---

### Post by kennedyjch on 2008-06-21
Just a further clarification... I use WEP-64 key encryption. If I specify ascii key in non-roaming mode, adapter does not work. In roaming mode, the ascii key is accepted and functions. However, to get the adapter to function properly in manual mode I've had to specify the equivalent hex key.

---

