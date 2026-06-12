---
title: "Wireless help!!! Dell B130 w/ 1370 miniPCI"
date: 2007-02-13
forum: Networking &amp; Wireless
---

### Post by bswindell77 on 2007-02-13
I am so tired of reading guides. I have read so many guides, I can write one by now. 

I could never understand why a "free" OS has never taken off. I can see why now. Windows will always dominate until the average **tard can install linux, and it work right out of the box. But don't get me wrong, I don't like windows, but, as a lot of others are, I am forced to use it. 

I just can't swallow the fact that I will have to pay $250.00 for Commercial Support, when I am only having a problem with one thing!

THE PROBLEM:   Can not get wireless card to work.

THE SYSTEM:

Dell B130
Intel Pentium M 1.7ghz
512 mb RAM
CD-RW
40G HD
15.4" Widescreen
[COLOR="Red"]Dell 1370 Wireless mini PCI LAN Adpater (internal) using BCMWL5.INF in windows XP
[COLOR="Black"]Updated...[/COLOR] [NO INTERNAL NIC![/COLOR]]

WHAT I HAVE DONE:

1.  Installed Ubuntu 6.10 from CD to Dual with XP (completed perfect)
2.  Chose Ubuntu 6.10 in Grub (loaded Ubuntu perfect)
3.  Ubuntu loads, wireless light not on, no Internet. (****)
4.  Start reading guides. (way too many, boring)
5.  Attempt walk-throughs in multiple guides w/ fresh install every time (no luck)
6.  Woke up with ASDF imprint on my forehead. (74.45 hours awake)
7.  Yelled at wife to leave me alone. (get off my back)
8.  Apologized to wife and tried to explain why I am tense. (she's ok now)
9.  Tried Using CTRL-F2 to turn on wireless (Dell's wireless on/off button)
10. Tried [http://ubuntuforums.org/showpost.php?p=1189681&postcount=105](http://ubuntuforums.org/showpost.php?p=1189681&postcount=105) (No success)
11. Tried [http://ubuntuforums.org/showthread.php?t=197102](http://ubuntuforums.org/showthread.php?t=197102) (no sucess)
12. Tried wlan in bios ON and APPLICATION (on, always on) (Application, turns on by app) neither worked.
13. Tried conecting to wrt54g wirless router that is unsecured and secured.

[COLOR="red"]**Updated:**[/COLOR]

14. Tried Ubuntu [COLOR="Red"]*6.06 LTS*[/COLOR] I followed some more guides (with a new isntalle cah time) and got to the point where ndis says hardware present, The wlan is on the Network Manager, but this I actually get a [COLOR="Red"]LIGHT[/COLOR], albeit for only one second when I first activate it, and again when I click OK in Network Manger. I feel that I have a better chance with Ubuntu 6.06 LTS since I am at least geting some lights... BTW when the live cd is in and the old bcm43xx is loaded the light is on the whole time.. the card just doesnt work and ndis says hardware not present.

15. Have you ever seen a 29 year old man ***crying*** over a computer? yeah, like a little baby.

WHERE I AM AT NOW:

I have gotten to the point where I have the bcm43xx blacklisted, ndiswrapper 1.8 and ndisgtk installed and working. ndisgtk shows "Hardware Present: Yes". Comes up as eth1 in porpeties, have settings to my network entered. Everything seems fine except the light doesn't come on indicating the card is active. No interenet. Works perfect in windows XP.

[COLOR="Red"]**IS THERE ANYWAY TO GET THE Broadcom BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02) WORKING ON A FRESH INSTALL OF EITHER UBUNTU 6.06 LTS or 6.10? USING THE CD IMAGES DOWNLOADED TODAY!??**[/COLOR]

Is there any help out there for me? I will even take (or make) phone calls, emails, or bring my computer to you (if reasonably close) and after the blizzard is over. (NE Indiana)

---

### Post by Floppyjoe on 2007-02-13
This probably wont help you but is there a button on your computer somewhere to activate your wireless device? My laptop has a button/light in the front which i had to push to activate my broadcom wifi device.

Floppyjoe

---

### Post by bswindell77 on 2007-02-13
See newly added #9, 10, 11, 12, 13, 14, 15

---

### Post by Floppyjoe on 2007-02-13
There might also be a on/off setting for that card in you computers bios. U need to press one of the function keys at the begining of the boot-up sequence to enter into the bios configuration. It will probably say which key for a split second on the screen during boot-up.

---

