---
title: "Thinkpad X60 + ubuntu 8.10"
date: 2008-10-30
forum: Networking &amp; Wireless
---

### Post by Frozzare on 2008-10-30
Hello, 

i trying to get the wirless network to work on my Thinkpad X60, but it don't work. 

i think it is a Intel 3945 network card. when i have a network cabel the network work. But i have to get the wirless to work.

---

### Post by Frozzare on 2008-10-30
Any one? The are a killswitch on this computer,

---

### Post by Frozzare on 2008-10-30
pleas help someone :/

---

### Post by fosix on 2008-10-31
hey, yesterday I installed 8.10 on my thinkpad x60s, it works perfectly. I have met the same network problem in 8.04, maybe you can try to make a completely new installation, not just using upgrade method.

---

### Post by GoodPanos on 2008-10-31
From my experience the wireless on the Lenovo's especially the X60 series is turned on by software.  Even though there is a hard switch you still need the software to turn on the wireless.  Their philosophy for this, is so you can iterate between WiFi, bluetooth, and WLAN if any.  BTW, Dell does this in the BIOS.

So, the only solution I can think of, is if you have Windows installed on the laptop, boot into it and turn on the Wifi there.  The antenna with the air waves should light up.  From that point on you can just use the hard switch to turn off and on the Wifi.  When you boot into Ubuntu, it should then work.  I am not sure if there is a utility to do this from Ubuntu.

Further more, if you have Bluetooth as well, turn that one on too.  If you have a WLAN card, it gets a bit confusing.  I believe only the Wifi or WLAN can be on at one time.  You can't have both on at the same time.  I am not 100% sure on this; I have seen it work both ways.

Good Luck!

---

### Post by jeffme on 2008-10-31
Frozzare - What model X60 do you have? I have the 1706 & have been able to install 8.10 and have the Wireless Manager "just work". You can find the specific model number on the bottom of your laptop, on a white label marked "Type".

8.10 does not properly support the hardware wireless kill switch on the front of the x60. For example, if I boot up with wireless on, and then use the kill switch to turn it off, it properly turns off. But, when I try to turn the wireless back on, it does not turn back on.

Good Panos has good advice, but the comment about the WiFi and WLAN is confusing - I thought these were the same things.

Good luck in your efforts, I'll try to get back and keep an eye on the thread if I can help in any way.

---

### Post by dash2 on 2008-10-31
Did you see the release notes about iwl3945 cards? If you boot with the wireless switch turned off, it won't work when you turn it on later. You have to boot with it turned on. Hope this helps.

---

### Post by GoodPanos on 2008-10-31
WLAN is the 3G card, be it HSPDA (GSM) or EVDO (CDMA).

---

