---
title: "WPA in ubuntu 7.04"
date: 2007-05-03
forum: Networking &amp; Wireless
---

### Post by jimbouk on 2007-05-03
Hello

I am trying to get WPA to work in ubuntu but so far am failing!

I had installed 6.10 a few weeks ago, but was utterly unable to get WPA working - the network manager only ever seemed to want to join WEP networks (which is obviously no good)

I installed wpasupplicant, but to no avail, so just decided to wait for Feisty in the hope that would deal with it.

So anyways i updated to Fesity via the Update Manager and all was well... except that WPA still is not showing as an option in the network manager.

I am a bit of a noob, so not sure if perhaps the changes i made under 6.10 are messing up my ability to get onto WPA under Feisty? I had changed the /etc/network/interfaces file as well as the wpasupplicant gubbins.

if it makes any difference, i use a linksys WUSB54G v4 adaptor.

thanks for any help! i will buy a beer for anyone who gets me on wpa!

cheers

---

### Post by spd106 on 2007-05-03
I suggest that you comment out any/all changes you made to the /etc/network/interfaces and wpa_supplicant.conf files as they might cause problems, don't delete them though.

Make sure that roaming mode is enabled in Network Manager.
[https://help.ubuntu.com/community/WifiDocs/NetworkManager](https://help.ubuntu.com/community/WifiDocs/NetworkManager)

---

