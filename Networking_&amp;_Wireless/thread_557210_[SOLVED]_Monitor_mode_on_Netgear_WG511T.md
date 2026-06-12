---
title: "[SOLVED] Monitor mode on Netgear WG511T"
date: 2007-09-22
forum: Networking &amp; Wireless
---

### Post by scruffybeard on 2007-09-22
Hiya everyone,

Here's the problem I find myself with. I'm still trying to get aircrack-ng working for my networking class. My current problem is that I can't get my wireless card into monitor mode.

Following the walk-through on the aircrack-ng site, I attempted to run airodump-ng, and here is my terminal output. I dunno if I'm just missing something or what, but every google search has basically given me instructions as if the program were working perfectly rather than info that might help me get it running in the first place.

> scruffybeard@VaioPirate:~$ sudo airodump-ng ath0
Password:
ioctl(SIOCSIWMODE) failed: Invalid argument
Error setting monitor mode on ath0
scruffybeard@VaioPirate:~$ 

Now, I have compiled my own MADWifi-ng driver, along with the required patch, and I can see the wireless network in question, and I can see that it has a WEP encryption. Now I just need to be able to bust into the network to get the bonus points.

Hopefully someone can help point me in the right direction. Thanks in advance!

----------------------Edit--------------------------
Ok, so after some tinkering, I finally figured out how to do it. I first had to enter this code
```
sudo airmon-ng wifi0
```

This brought up a window saying that ath0 was monitor mode enabled

Then the previous code got me scanning the network. Now I just need to figure out what I'm doing with the rest of the suite and I'll get my A for sure.

---

### Post by scruffybeard on 2007-09-25
Ok, I ran airodump for a couple of days, and I collected about 150000 packets, and decided to try running aircrack to see if I could come up with the key.

Aircrack has been running for over 19 hours now, and still hasn't said yay or neigh. Is this normal? I should also mention that I have been unsuccessful at injecting packets, so I am running aircrack just against the packets collected from the allowed machine and the AP.

---

### Post by aldo_m on 2007-12-17
what version of aircrack are u using 0.9 or 1.0?

i followed these steps after installing dev_1.0 .[http://www.aircrack-ng.org/doku.php?id=madwifi-ng](http://www.aircrack-ng.org/doku.php?id=madwifi-ng) 
 there is a error on this page because when i installed my patch it installed it to my home directory so your going to notice when patching your driver for packet injection .
patch -Np1 -i ../madwifi-ng-r2277.patch   i think they had a typo they put 2 periods infront of madwifi-ng. should be ../ home directory ./ and it worked . but that is if you have aircrack installed correctly.
[http://www.aircrack-ng.org/doku.php?id=install_aircrack](http://www.aircrack-ng.org/doku.php?id=install_aircrack)
make  sure you have OpenSSL (libssl-dev on Debian-based system) installed.



if you have any other questions i will be at work in a few hours i have the same card.

---

### Post by tturrisi on 2007-12-17
> I should also mention that I have been unsuccessful at injecting packets
then you are NOT using patched drivers!
Run the injection test:
[http://www.aircrack-ng.org/doku.php?id=injection_test](http://www.aircrack-ng.org/doku.php?id=injection_test)

To put the card into monitor mode you must first detroy any existing virtual devices, place into monitor mode and then bring uo the interface::
airmon-ng stop ath0
airmon-ng start wifi0
ifconfig ath0 up

or

wlanconfig ath0 destroy
wlanconfig ath0 create wlandev wifi0 wlanmode monitor
ifconfig ath0 up

---

### Post by aldo_m on 2007-12-17
turisi you cant inject? i had that problem in te beging then figured everything out by following the distructions:)on the aircrack website.
ifyou have any problems with injection i can walk you threw it . you can message me on yahoo fl3xt0r.

and i know if you guys go to aircrack-ng channel on irc they wont give you any walk threws so if you want i will creat a room and i will help you. NSA_ on irc.go to channel #patch-help

going to have a group install from start to end "also doing injection test" 8 pm eastern mountain time.

---

### Post by scruffybeard on 2007-12-17
I did manage to get it working guys. I was using aircrack wrong. Thanks though, I have since gotten it totally working and have successfully gained access to the network.

---

### Post by scruffybeard on 2007-12-17
> **tturrisi said:**
> then you are NOT using patched drivers!


Incorrect.

Simply because I have not been successful does not mean I have the wrong software. Another issue that can happen, though it is less common, is proximity.

If the signal from the AP is too weak, then often packet injection will fail, even though one is capable of capturing packets.

Once I moved closer to the AP physically, lo and behold, there goes the injection. Please do not assume.

---

### Post by aldo_m on 2007-12-17
thanks for the responce . thread bumped if you have data then you shouldn"t have a problem injecting a packet.

---

### Post by scruffybeard on 2007-12-18
> **aldo_m said:**
> thanks for the responce . thread bumped if you have data then you shouldn"t have a problem injecting a packet.

WHat I have found is that I can collect packets as long as signal strength is 15 or better, but I cannot inject until signal is 35 or better.

This is not isolated either, [aircrack's own site]("http://aircrack-ng.org/doku.php") actually states this as an issue. Something about signal strength and AP strength, neither here nor there.

Practical upshot is this, if you're wanting to inject, make sure you're close enough to do it.

---

### Post by tturrisi on 2007-12-18
> **aldo_m said:**
> turisi you cant inject? i had that problem in te beging then figured everything out by following the distructions:)on the aircrack website.
ifyou have any problems with injection i can walk you threw it . you can message me on yahoo fl3xt0r.

and i know if you guys go to aircrack-ng channel on irc they wont give you any walk threws so if you want i will creat a room and i will help you. NSA_ on irc.go to channel #patch-help

going to have a group install from start to end "also doing injection test" 8 pm eastern mountain time.

I can inject.
I was telling the other guy why he could not inject.

---

