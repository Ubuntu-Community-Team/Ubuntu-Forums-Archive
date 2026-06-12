---
title: "Yet Another DELL D600 Wireless Problem!"
date: 2010-03-09
forum: New to Ubuntu
---

### Post by fremantle on 2010-03-09
So just switched from xp prof to Ubuntu KarmicKoala 9.10 on my crappy old dell D600 laptop. I knew wireless wouldnt work just out of box, so after installation followed the directions on [http://linuxwireless.org/en/users/Drivers/b43](http://linuxwireless.org/en/users/Drivers/b43) . it worked ! BUT 1 and a half days later everythings gone, net manager not picking up any wireless device or connections, but in Hardware Driver B43 is installed and activated.

My wifi card type is Broadcom [14e4:4320] (rev 03)

Can anyone PLEASE give a effective solution on HOW to use wireless on D600 under these specifications?

*NDIS didnt work - so forget about it

---

### Post by summersource on 2010-03-09
I'm new myself but I will give it a shot..I had the same thing happen.. Installing back port modules fixed my wireless issue. Copy and paste these in your terminal separately.

sudo apt-get install linux-backports-modules-karmic


sudo apt-get install linux-backports-modules-wireless-karmic-generic

---

### Post by summersource on 2010-03-10
also follow these steps and install madwifi if you haven't already
[http://www.stchman.com/ath_drv.html](http://www.stchman.com/ath_drv.html)

---

### Post by bkratz on 2010-03-10
> **summersource said:**
> also follow these steps and install madwifi if you haven't already
[http://www.stchman.com/ath_drv.html](http://www.stchman.com/ath_drv.html)

Madwifi is for Atheros wireless cards, not Broadcom.

@fremantle

Please post the output of
 
```
lsmod
```

(LSMOD in lowercase)

and also

```
rfkill list
```

---

### Post by ac_d600 on 2010-03-10
I also use a D600 (running Hardy) and I also had the same problem that you
described. Net manager not finding any wireless signals, and the drivers
were installed and activated, but I couldn't figure out what was wrong.

But then I tried the Fn-F2 key (turns on/off wireless) problem solved!
Sounds like this could be you problem also.

---

### Post by waterinthefuel on 2010-03-20
> **summersource said:**
> I'm new myself but I will give it a shot..I had the same thing happen.. Installing back port modules fixed my wireless issue. Copy and paste these in your terminal separately.

sudo apt-get install linux-backports-modules-karmic


sudo apt-get install linux-backports-modules-wireless-karmic-generic

I finally figured out what a terminal is, but I still can't get it to work. When I copy and paste what you said to, with both of them it just says that it can't find it. I am using the laptop now, with Ubuntu, but using the ethernet card. (I forgot about it earlier.) 

Any hints on how to get one of these up and running? Why is it so difficult?

---

### Post by bkratz on 2010-03-20
> **waterinthefuel said:**
> I finally figured out what a terminal is, but I still can't get it to work. When I copy and paste what you said to, with both of them it just says that it can't find it. I am using the laptop now, with Ubuntu, but using the ethernet card. (I forgot about it earlier.) 

Any hints on how to get one of these up and running? Why is it so difficult?



Now that you have found the terminal we need to discover what your wireless card is.  In the terminal type

lspci -nn

(that is LSPCI in lowercase). The listing will be quite long, but look for something that says network controller or 802.11 and copy/paste or type what the line reads back here. 
This will tell us what you need to do.

---

### Post by fremantle on 2010-03-21
Ok guys listen, i reinstalled the whole OS and then ran the b43fwcutter command which extracted the firmware. Then rebooted and wireless works! But wait, when i go standby and then wake up my laptop, wireless is gone again. So, i have to reboot every time and let go of stand by mode. WHY????

---

### Post by fremantle on 2010-03-21
> **ac_d600 said:**
> I also use a D600 (running Hardy) and I also had the same problem that you
described. Net manager not finding any wireless signals, and the drivers
were installed and activated, but I couldn't figure out what was wrong.

But then I tried the Fn-F2 key (turns on/off wireless) problem solved!
Sounds like this could be you problem also.
no, i tried that.

---

