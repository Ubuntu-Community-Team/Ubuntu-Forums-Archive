---
title: "Epic Ubuntu fail"
date: 2011-04-03
forum: New to Ubuntu
---

### Post by Torp3x on 2011-04-03
If my router switches off then on while I'm connected wirelessly, Ubuntu  10.10/Network Manager will not reconnect successfully. It will look as  if it's connected, but it's not. It won't communicate with the router's  default address (192.168.1.1) and it won't connect to the internet. 

Switch the wireless card off and on you might think, would solve the  problem. It doesn't. Reload the wireless module? Nope. I have to  reboot....

And that's where it gets really bad- not even rebooting will fix it! Not  once, not twice... it will not reconnect to the router successfully. 

So I logged into Windows on the same machine to ascertain whether it was  a problem with the router, and Windows connected successfully. Windows  also reconnects successfully under the same conditions (router power  down, router power up) without any intervention from me. Also, after  logging into Windows, Ubuntu will finally reconnect properly.

So Ubuntu can't reconnect after a router power down without help from  Windows. Surely not? I've reproduced this situation 6 times.

Not really a major problem, it's not like my router gets switched off  every 5 minutes but still, if it wasn't for Windows, I'd presumably have  had to totally reconfigure the wireless connection in Ubuntu to get it  to work again. Lame.

---

### Post by LowSky on 2011-04-05
More than likely its the Driver's fault and not the OS. What model is the Wifi card?

What wireless card are you using? Have you tried disabling networking from the applet and then turning it back on instead of the hardware switch? How about disconnecting from the wireless signal and reconnecting?

---

### Post by Linye on 2011-04-05
That has happened to me a few times and some of then it works by just by turning on/off the wireless card. Others just by logging out/in. I don't mind though.

Mi wifi card is one of these. Broadcom BCM4311-, BCM4312-, BCM4321-, and BCM4322

---

### Post by supergirlkara on 2011-04-05
I know this may sound crazy, but it worked for me....Try installing the ntp package. 

sudo apt-get install ntp

For some reason this completely fixed my similar wireless issue. Give it a shot...I hope it helps you.

---

