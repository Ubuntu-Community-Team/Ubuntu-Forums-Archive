---
title: "SMC 2802W help"
date: 2005-05-01
forum: Networking &amp; Wireless
---

### Post by GazaM on 2005-05-01
I know there has been alot of threads on this forum dealing with SMC wireless cards, but none have reported the same problems as I am having. When I start Ubuntu the 'configuring network interfaces' takes ages and I mostly have to ctrl+c to cancel it it takes that long! That's just a minor issue, now the real problem; I have an SMC 2802W wireless card and I can't get it to work, even though it's detected in the display manager and networking tool. When I go into the networking tool the card is disabled and I have to go into the properties to set up the ESSID and the WEP key, I then press enable and it takes a long time until finishing then I hit 'OK' to get out of the networking tool and that takes ages to close, but I still have no internet connection! I have tried everything from using the 's:' prefix before the passphrase, or just typing the hex digits in the format of XXXX-XXXX etc and just XXXXXXXX but it still won't work! I have tried disabling encryption on my router altogether and leaving the WEP key blank but it still wouldn't connect! I need help as I now have no internet connection until I get it working ](*,)  (i brought the PC into the room with the router for the install so I had the LAN port set as default, maybe this has something to do with the startup thing taking so long if someone could please tell me how to permanently change this?). Any help is greatly appreciated!

---

### Post by psYchotic on 2006-02-20
I did the following to get my 2802W to work. I used ndiswrapper to load the native windows drivers. I completely disabled wlan0 in System->Administration->Networking, and made a little script I run everytime I reboot (which is usually no more than once a week)
```
iwconfig wlan0 essid <your essid> enc s:<your wep key>
dhclient wlan0
```
Of course you'll have to run the script with sudo, but that shouldn't be too much of a problem.

---

