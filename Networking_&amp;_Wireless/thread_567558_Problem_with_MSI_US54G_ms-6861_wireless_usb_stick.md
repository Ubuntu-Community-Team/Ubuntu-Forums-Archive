---
title: "Problem with MSI US54G ms-6861 wireless usb stick"
date: 2007-10-04
forum: Networking &amp; Wireless
---

### Post by by100 on 2007-10-04
Hello Everyone!

I hope that this question isn't somewhere in the forum...

I Just installed Ubuntu, 7.04, Feisty Fawn on my PC (amd64x edition).
The main problem I have, is with configuring my wireless USB modem (MSI US54G / MS-6861).

I don't know if it needs some kind of driver or something like that.... (It's my first time on linux).
I have an Edimax router, and the usb modem worked fine on the XP I had.

when I connect my pc to the router with a cable, it works perfectly. the problem is with connecting to the wireless network.

I hope you can help me.

Thanks a lot, 
Barak

---

### Post by Lambert on 2007-10-05
This device I believe uses the ralink chipset. If you are trying to use the default network tool it won't work and get you connected.

There are two steps you can take.

1. to use the default tools look at [this]("http://ubuntuforums.org/showthread.php?t=564419") thread. It will set you up to use the windows drivers with an app called ndiswrapper.
2. The other option you have is to uninstall network manager and look at a tool called RutilT (I believe that's correct). It is a graphical application to configure and use devices based on the ralink chipset.

If you decide option 2, you can open up a terminal and run these commands to see if the device is working.

```

iwconfig

```
This will list any wireless devices that are recognized with a loaded driver. If you see something like wlan0 or ra1 or rausb0 etc... then run this command

```

iwlist wlan0

```
rplace wlan0 with whatever interface showed in the first output. If it's working it will show all routers with in range of you.

You can try to configure the device from the command line if you'd like, (only if not using wpa encryption) samples would be 

[code]
sudo iwconfig wlan0 ssid ________

sudo iwconfig wlan0 ssid ________ key _______ mode managed
[/code)
replacing wlan0 with correct one and entering information in blanks.

In the terminal you can type [COLOR="Red"]man iwconfig[/COLOR] which will show you a quick reference on that command and how to use it to connect.



You can find more help searching in the forums using keywords like rausb / ralink / rt2x000 / RutilT

The instructions will all be similar for any usb device using a ralink chipset.

---

