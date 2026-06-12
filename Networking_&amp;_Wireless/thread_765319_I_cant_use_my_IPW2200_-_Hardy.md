---
title: "I cant use my IPW2200 - Hardy"
date: 2008-04-24
forum: Networking &amp; Wireless
---

### Post by oidacra on 2008-04-24
my dmesg
//////////////////////////////////////
[   19.639090] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
[   19.639094] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[   19.813085] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[   23.220469] ipw2200: Radio Frequency Kill Switch is On:
[   23.412338] ipw2200: Detected geography ZZM (11 802.11bg channels, 0 802.11a channels)
[   40.094514] ipw2200: Failed to send TX_POWER: Command timed out.
[   53.886998] ipw2200: Failed to send TX_POWER: Command timed out.
[   54.034276] ipw2200: Failed to send TX_POWER: Command timed out.
[   54.288351] ipw2200: Failed to send TX_POWER: Command timed out.
[   54.589789] ipw2200: Failed to send TX_POWER: Command timed out.
[   54.589808] ipw2200: Unable to initialize device after 5 attempts.
[   54.589812] ipw2200: Failed to up device
///////////////////////////////////////////////////
i dont know how i can fix this...

---

### Post by tsantsa31 on 2008-05-04
Me neither.  The installed driver from ubuntu works but I have to insert info each time I boot up.  I tried ndiswrapper with the latest intel driver and not only did it not work, it deleted the wireless card from the network manager when I removed the nonworking driver from ndisgtk!!

---

### Post by chili555 on 2008-05-04
> Radio Frequency Kill Switch is On:That's the whole answer. There is a switch or key combination on your laptop that switches your wireless card on and off. It's off. 

On my Thinkpad T60, it's a little slide switch on the front; yours may be a combination like Fn+F5. If you are unlucky, you can turn it on in Windows but not Linux. Let us know.

---

### Post by oidacra on 2008-05-06
nobody can helP¿?.....

---

### Post by chili555 on 2008-05-06
I thought I did help.> nobody can helP¿?..... Nope. Nobody but you can push the right button and turn your wireless card on. As long as your card is switched off or, to put it another way, the kill switch is on, you will not have wireless. So find the switch or key combination and push it! When you can run:```
dmesg | grep ipw2200
```and you do **not** see any reference to the kill switch, only then will your wireless work.

---

### Post by Turkey Baster on 2008-05-24
> **chili555 said:**
> I thought I did help.

You did! 

I was reading posts looking for how to turn on the "virtual switch," growing a beard like Gandalf, when I typed in "wireless:radio off" in search, read your post and saw this all of a sudden:

[IMG]http://ubuntuforums.org/picture.php?albumid=191&pictureid=583[/IMG]

An actual switch, it seems. Well. I guess this is my first laptop, and, yeah. A labeled button.

For the searchers, pressing and holding Fn, then F2 on my Dell Inspiron 9300 solved my problem with my 2915abg wifi card using the ipw2200 driver, when it had it's wireless radio off.

Now to steal my neighbours "default" connection :guitar:

---

