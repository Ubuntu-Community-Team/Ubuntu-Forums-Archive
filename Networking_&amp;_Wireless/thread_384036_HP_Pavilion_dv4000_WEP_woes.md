---
title: "HP Pavilion dv4000 WEP woes"
date: 2007-03-14
forum: Networking &amp; Wireless
---

### Post by VernerVonTux on 2007-03-14
Hello, I am posting this question on behalf of a friend, who has very recently installed kubuntu dapper 6.06 on his HP Pavilion dv4000 laptop computer. Thus far, he has had no compatibility problems with anything other than his wi-fi. He is currently only able to connect to wi-fi networks that have WEP turned off. He is using wlanassistant to connect and has also attempted wi-fi radar to no avail. What could be causing his wi-fi woes that are preventing him from connected to WEP encrypted networks? I think I recall a similar problem when I first started using ubuntu ;however, I do not remember my solution :-? . Any assistance on this problem would be very greatly appreciated.

---

### Post by DapperMe17 on 2007-03-14
Getting to the open network is a good start....it shows the wifi card is seeing the network!


I would try to steer away from the "auto" wifi managers.....and stick to configuring the WEP through "network settings" in the Kmenu.



You'll need to know if the router is boadcasting a 64 or 128 bit key, network name, shared or open, aci or hexidecimal and whether the router is communicating via dhcp, or static ip.



Because I use WPA, I know that I need to enter the encryption key in hex code, meaning I have to use Konsole to "convert" the actual network name into that funky looking, scrambled key. You may have to play with that similarly when it comes to entering in the WEP key in the "network settings" configuration file.

Play with it a bit, I'm sure you'll get there.

---

