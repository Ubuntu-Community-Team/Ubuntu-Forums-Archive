---
title: "Trouble installing B43 driver"
date: 2008-11-26
forum: Networking &amp; Wireless
---

### Post by Nikku49 on 2008-11-26
Hello,
 Im having issues trying to install and use the B43 driver over the wl driver. Let me go ahead and tell you guys that my wireless is working fine. Im running 8.10 on a clean install and Im using the BCM4312 (rev.01) card.

 The whole reason for me wanting to use the b43 driver is so I can have improved speeds/ signal strength/ and rf monitoring.
 
 When I goto the hardware drivers it shows the Broadcom STA driver but everytime I hit activate it asks me for root and then does nothing. It never activates.

 I've tried blacklisting wl but it just broke my wireless. Let me say though that the hardware drivers did show the Broadcom STA driver as active at one point but if I went to connection info it showed wl as the driver and so did airmon-ng. I then deactivated it and havent been able to activate it since. Not like it was in use or anything before hand.

Anyways, I know you guys get these Broadcom questions all the time and I have done some searching and havent turned up much. So any help would be greatly appreciated.

Thanks,
 Nik

---

### Post by Ayuthia on 2008-11-26
> **Nikku49 said:**
> Hello,
 Im having issues trying to install and use the B43 driver over the wl driver. Let me go ahead and tell you guys that my wireless is working fine. Im running 8.10 on a clean install and Im using the BCM4312 (rev.01) card.

 The whole reason for me wanting to use the b43 driver is so I can have improved speeds/ signal strength/ and rf monitoring.
 
 When I goto the hardware drivers it shows the Broadcom STA driver but everytime I hit activate it asks me for root and then does nothing. It never activates.

 I've tried blacklisting wl but it just broke my wireless. Let me say though that the hardware drivers did show the Broadcom STA driver as active at one point but if I went to connection info it showed wl as the driver and so did airmon-ng. I then deactivated it and havent been able to activate it since. Not like it was in use or anything before hand.

Anyways, I know you guys get these Broadcom questions all the time and I have done some searching and havent turned up much. So any help would be greatly appreciated.

Thanks,
 Nik

Please check lspci -nn.  If you have a chipset of [14e4:4315], your card is not yet supported by the b43 driver.  If it is not, please post the results of:
```
lsmod|grep -e b43 -e ssb -e wl
```

---

### Post by Nikku49 on 2008-11-26
ahh, I have the [14e4:4315]. Thanks for the help. Although I did ninja a bcm94318mpg broadcom card out of one of the laptops we gutted at work. Do you know anything about this card? Wether it supports the b43 driver?

---

### Post by Ayuthia on 2008-11-26
> **Nikku49 said:**
> ahh, I have the [14e4:4315]. Thanks for the help. Although I did ninja a bcm94318mpg broadcom card out of one of the laptops we gutted at work. Do you know anything about this card? Wether it supports the b43 driver?

From the name (bcm94318mpg), it sounds like it is a 4318 card.  The b43 driver does support them, but some of the 4318 card have had a hard time working in Ubuntu using Hardy(some had problems connecting), but it has improved in Intrepid.

Hope that helps.

---

### Post by Titan8990 on 2008-11-26
I have the same card with similar issues that I just finished working out. Unfortunately, I ended up having to reformat and install using ndiswrapper:

[http://ubuntuforums.org/showthread.php?t=985223](http://ubuntuforums.org/showthread.php?t=985223)

[http://ubuntuforums.org/showthread.php?t=986374](http://ubuntuforums.org/showthread.php?t=986374)

[http://ubuntuforums.org/showthread.php?t=992259](http://ubuntuforums.org/showthread.php?t=992259)

---

### Post by Ayuthia on 2008-11-26
If you are going to use the card for aircrack type tools, ndiswrapper is not supported.  However ndiswrapper is another option to get your wireless card to work.

---

