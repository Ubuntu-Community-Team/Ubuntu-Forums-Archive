---
title: "ADSL isp encryption?"
date: 2008-06-03
forum: Networking &amp; Wireless
---

### Post by ilych on 2008-06-03
I currently connect to the Internet by issuing the following two commands:
```
sudo iwconfig eth1 essid GW-AP11X
```
then
```
pon dsl-provider
```
(I previously configured sudo pppoeconf)

Is it the case that the username and password of my isp are being sent unencrypted over the air?

How do I set an encryption? I am using Ubuntu with Fluxbox, and if possible, I'd like to not load nm-applet and gnome-keyring-daemon.

Thanks,
ilych

---

### Post by ilych on 2008-06-06
bump?

---

### Post by ilych on 2008-06-08
bump

---

### Post by SpaceTeddy on 2008-06-09
The only way you can use encryption here is by using wireless encryption - preferably WPA or WPA2. That needs to be setup in your router/modem thing. How i cannot tell you, as there is about a million different device out there. 
Also, you will need to make sure that you change your iwconfig command to reflect your encryption (don't ask me how, i have never set this up via command line) but i'd say it has something to do with the wpa supplicant. Mentioning that is to help you search for solutions :)

besides that, i cannot see any way to encrypt that traffic... sorry.

hope it helps :)

---

