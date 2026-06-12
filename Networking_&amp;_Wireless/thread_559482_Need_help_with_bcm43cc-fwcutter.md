---
title: "Need help with bcm43cc-fwcutter"
date: 2007-09-25
forum: Networking &amp; Wireless
---

### Post by NeHigh on 2007-09-25
I'm banging my head trying to get my WMP54G wireless adapter to work with U&.04

I got the correct version of bcmwl5.sys from Linksys.  I downloaded bcm43xx-fwcutter.  When I try to draw out the firmware I get:

[B]d:~$ sudo bcm43xx-fwcutter -w /lib/firmware bcmwl5.sys
fwcutter can cut the firmware out of bcmwl5.sys
  filename :  bcmwl5.sys
  version  :  3.30.15.0
  MD5      :  ebf36d658d0da5b1ea667fa403919c26

extracting bcm43xx_microcode2.fw ...
extracting bcm43xx_microcode4.fw ...
extracting bcm43xx_microcode5.fw ...
*****: Sorry, it's not posible to extract "bcm43xx_microcode11.fw".
*****: Extracting firmware from an old driver is bad. Choose a more recent one.
*****: Luckily bcm43xx driver doesn't include microcode11 uploads at the moment.
*****: But this can be added in the future...
extracting bcm43xx_pcm4.fw ...
extracting bcm43xx_pcm5.fw ...
extracting bcm43xx_initval01.fw ...
extracting bcm43xx_initval02.fw ...
extracting bcm43xx_initval03.fw ...
extracting bcm43xx_initval04.fw ...
extracting bcm43xx_initval05.fw ...
extracting bcm43xx_initval06.fw ...
extracting bcm43xx_initval07.fw ...
*****: Sorry, initval08 is not available in driver file "bcmwl5.sys".
*****: Extracting firmware from an old driver is bad. Choose a more recent one.
*****: Luckily bcm43xx driver doesn't include initval08 uploads at the moment.
*****: But this can be added in the future...
extracting bcm43xx_initval09.fw ...
extracting bcm43xx_initval10.fw ...[/B]

My adapter is version 2 and that is the version of the driver on Linksys support.  I'm willing to buy a card if someone can tell me which one will work without months of screwing around.

Thank you.

---

### Post by spd106 on 2007-09-25
Download and use this firmware instead [http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o](http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o)

See [http://linuxwireless.org/en/users/Drivers/b43](http://linuxwireless.org/en/users/Drivers/b43) for more information

---

### Post by NeHigh on 2007-09-26
Thanks for the reply, spd106.  I'll try this tonight.

---

