---
title: "Wireless on Hardy 8.04"
date: 2008-05-17
forum: Networking &amp; Wireless
---

### Post by gdelta9 on 2008-05-17
I got this aspire 5520 laptop these days and hardy 8.04_64.Problem is i cannot make my wireless to work.
I try to be as more specific as i can.
My wlan card is Atheros AR5007EG
First,
Knetworkmanagger does not see any wireless networks.Then i follow this How To: [http://ubuntuforums.org/showthread.php?t=512828](http://ubuntuforums.org/showthread.php?t=512828) .After doing every step it mentions i get my wcard to work without any errors.
Knetwork manager is able to see now all available wireless networks.
Main problem is i cant connect to any network with data encryption enabled.I can connect to my neighbours unsecured network but not mine.
When knetworkmanager tries to connect it stucks at 28%.I have no problems at all if i remove encryption from my wireless network.But if i enable wpa,wpa+wpa2,wep encryption i cant connect.
I have tried all clients other than knetworkmanager provided by ubuntu repositories.I have also tried wicd and still same problem.The WPA_Supplicant is installed as well.

Any help would be appriciated,
Thnx a lot in advance

---

### Post by silberj on 2008-05-17
This post provides specific instructions which got mine working 100%. Very good documentation.

[http://ubuntuforums.org/showthread.php?p=4975916#post4975916](http://ubuntuforums.org/showthread.php?p=4975916#post4975916)

---

### Post by gdelta9 on 2008-05-17
THnx a lot for your reply.
Solved the problem some mins ago.All i did was to follow the guide i post for one more time,but this time i disabled the HAL and support for atheros restricted drivers.
everything works fine

---

