---
title: "Are there any stinking wireless cards that work?"
date: 2006-11-06
forum: Networking &amp; Wireless
---

### Post by mrtrick on 2006-11-06
Are there any wireless pci cards that work out of the box with Edgy. I'm so frustrated with my Zyxel g-302 currently. I've tried everything. The installer doesn't work, ndiswrapper makes the card show, it detects my wireless ISPs network, but shows zero signal strength and doesn't connect at all. I'm so close. 

```

wlan0     Scan completed :
          Cell 01 - Address: 00:60:B3:E5:65:32
                    ESSID:"ITTech30_3747787"
                    Protocol:IEEE 802.11b
                    Mode:Master
                    Channel:6
                    Encryption key:on
                    Bit Rates:11 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 11 
                    Quality:0  Signal level:0  Noise level:158
                    Extra: Last beacon: 7ms ago



```

sudo gedit /etc/network/interfaces shows

```

name Wireless LAN card
iface wlan0 inet dhcp
wireless-essid ITTech30_3747787
wireless-key xxxxxxxxxxxxxxxxxxxxxxxxxx

```

This is a 128bit key. 

I want to use Ubuntu, I really like it. I started using it because it "just worked". I'm highly considering having to go back if I can't get a wireless card to work. I live in the sticks and Wisp is my only high speed Internet choice.  Any advice is greatly appreciated. I don't care if I get this card to work if there is another one that works out of the box I'll go buy it. 

Wireless on Edgy = ](*,) :confused: :confused: :confused: :confused: :mad: :mad:

---

### Post by jdhancey on 2006-11-06
mrtrick, I feel your pain.  I just went thru the same process of trying to find a card that works with Edgy. The good news is, I found one that works, the D-link WDA-2320.  Edgy live cd correctly identified the card, and once I entered the essid and wep key worked flawlessly.  So I installed permanently, and the card has been working no problems.  The card is based on the Atheros AR5212 chipset, so other cards based on this chipset might work also.

Good luck

Doug

---

### Post by mrtrick on 2006-11-07
Doug, 

Thanks for the suggestion, I'm going to take back my Zyxel g-302 card and buy the one you suggested. Hope I have the same luck you did.

---

### Post by mrtrick on 2006-11-08
Well, I bought the recommended card and it looks better. I now have an ath0 and a wifi0 interface (strange). Anyway, I now see signal strength and can scan, find, and show signal strength for the access point that I'm trying to connect to, but still can't connect. I may have it all jacked up due to the driver stuff I was doing with my other Zyxel card. Going to reinstall Edgy (or would Dapper maybe be better... hmmm) tonight and see how it goes.

---

### Post by handy on 2006-11-08
I'm glad you have found a card that works.

If I may offer some advice?  When you set up (if you haven't already anyway) set up a separate **/home** partition, your life will be so much easier whenever you have to do a new install in the future.

---

### Post by jdhancey on 2006-11-08
mrtrick, before you reinstall, I would set the wep key to 1, and set to channel 1 on your access point.  Also, make sure if you're using mac filtering to enter the new mac of your d-link.

---

