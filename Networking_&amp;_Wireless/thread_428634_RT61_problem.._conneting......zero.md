---
title: "RT61 problem.. conneting......zero"
date: 2007-04-30
forum: Networking &amp; Wireless
---

### Post by Draq on 2007-04-30
Just installed ubuntu 7.04

My RT61 wireless card dont work.

I go into the manual setup and the wireless is showed. But how ever i put it i will not connect. 
If I manual set it up the access point show up. I done the WEP sec. When I finish and I click on the netowrk manager icon up right i cant see the wireless option. only the wired one. If i put the wireless on roaming mode (whatever that is i dont know and i couldnt find any clue ether) the wireless text show up but no accesspoint.

Its like if I do the one thing I dont get the next and other way around. 

Im so confused and sad. Linux without internet is a no go.

Hope anyone got any clue.

Simon

---

### Post by whayong on 2007-04-30
My RT61 card worked out of the box with WEP.  I don't recall whether I used "manual" or "roaming" mode.  I know it works with the included drivers without having to configure /etc/network/interfaces.  I couldn't check my setting for you because I took the card (built in) out and replaced with another one since WPA could not connect with the same card..

edit: Yes, I did get WPA to work with this card in Edgy.  I'm in Feisty now and decided on a new card.  So, yes, the card does "work."

---

### Post by dolphin_oracle on 2007-04-30
the RT61 built in driver does not support WPA through network manager.  I believe that even though the RT61 driver is installed by default you still need to copy some firmware files availbable from Ralink's website into a directory called /etc/Wireless/RT61STA (the capitalization is important).  Network manager should then be able to work your card.

assuming your rt61 is NOT usb based, here's the link

[http://www.ralinktech.com.tw/data/RT61_Firmware_V1.2.zip](http://www.ralinktech.com.tw/data/RT61_Firmware_V1.2.zip)

You can also download the complete driver set on that site, which has a nice readme file on how to setup RT61STA.dat, which is a configuration file that will allow you to use WPA.

[http://www.ralinktech.com/ralink/Home/Support/Linux.html](http://www.ralinktech.com/ralink/Home/Support/Linux.html)

good luck.

---

### Post by Clang on 2007-04-30
I can't seem to find /etc/Wireless on my system, any idea how can I get this to work with feisty?
cheers

---

### Post by dolphin_oracle on 2007-04-30
you need to create the directory by hand

$ sudo mkdir -p /etc/Wireless/RT61STA

then copy the *.bin files from the link I gave above to the RT61STA folder.  I then rebooted and was able to configure my wireless through network manager (even the WEP key).  WPA doesn't work by default, but you can use a rt61sta.dat file (an example is in the driver download package, along with instructions for editing), also stored in /etc/Wireless/RT61STA to configure WPA.

I no longer have feisty installed, for non-networking related reasons.  The networking work very well for me!

---

